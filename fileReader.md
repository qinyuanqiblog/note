# fileReader不完全指南

[阮一峰的详解](http://javascript.ruanyifeng.com/htmlapi/file.html)

* 一个demo 彻底明白fileReader的使用 [demo预览](http://qinyuanqiblog.github.io/fileReader.html)
* demo 在move的时候的位置还需要进一步进行相关的计算，现在的位置计算出错了


```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>fileReader + canvas 预览剪切demo</title>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <style>
        canvas {
            border: 1px solid red;
        }

        .mergeBox {
            display: inline-block;
            position: relative;
            width: 200px;
            height: 200px;
            z-index: 0;
            top: 0;
            overflow: hidden;
        }

        #mergeCanvas {
            position: absolute;
            top: 0;
            left: 0;
            z-index: 0;
            width: 200px;
            height: 200px;
        }

        .mergeDiv {
            display: none;
            position: absolute;
            z-index: 0;
            top: 0;
            left: 0;
            width: 200px;
            height: 200px;
            background-image: url('http://qinyuanqiblog.github.io/images/angular/shape_lingxing.png');
            background-repeat: no-repeat;
            background-size: 200px, 200px;
        }

        label {
            display: block;
            width: 100px;
            height: 50px;
            font-size: 20px;
            color: #fff;
            line-height: 50px;
            background: #999;
            cursor: pointer;
            text-align: center;
            border-radius: 10px;
        }

        input[type='file'] {
            display: none;
        }

        .preview-area {
            display: none;
        }
    </style>
</head>

<body>
    <label for="file">选择文件</label>
    <input id="file" type="file" accept="image/*">
    <div class="preview-area">
        <canvas id="previewCanvas"></canvas>
        <canvas id="compareCanvas"></canvas>
        <button class="merge">合成</button>
        <button class="inverse">反色</button>
        <div class="mergeBox">
            <canvas id="mergeCanvas"></canvas>
            <div class="mergeDiv"> </div>
        </div>
        <canvas id="clipCanvas"></canvas>
        <button class="clip">确认裁剪</button>
        <img src="" class="makePreview" alt="">
    </div>
</body>
<script>
    /** 思路
     *
     * 1.  使用fileReader API 读取到图片
     * 2.  生成previewCanvas预览图片
     * 3.  在previewCanvas上处理图片的滤镜和裁剪
     * 3.1 在previewCanvas上进行图片滤镜处理(canvas的像素级处理)
     * 3.2 把需要截取的图像写入到compareCanvs上，之后再和previewCanvas对比, 生成clipCanvas(裁剪图片之后的canvas)
     * 3.3 在clipCanvas上进行拖动并生成预览
     * 3.3.1  图片平移这一块使用到了css3的 matrix 相关的知识 其实也可以使用定位来实现的，后来的这个版本我就改用了定位来做的
     *        transform:matrix(a,b,c,d,e,f)
     *          a 水平缩放 (1)
     *          b 水平倾斜 (0)
     *          c 垂直倾斜 (0)
     *          d 垂直缩放 (1)
     *          e 水平位移 (0)
     *          f 垂直位移 (0)
     * 3.4 把clipCanvas上的图片转换成blob对象的地址 并生成预览图片
     *
     */
    var input = document.querySelector('input');
    var previewCanvas = document.querySelector('#previewCanvas');
    var compareCanvas = document.querySelector('#compareCanvas');
    var mergeCanvas = document.querySelector('#mergeCanvas');
    var clipCanvas = document.querySelector('#clipCanvas');
    var previewCtx = previewCanvas.getContext('2d');
    var compareCtx = compareCanvas.getContext('2d');
    var mergeCtx = mergeCanvas.getContext('2d');
    var clipCtx = clipCanvas.getContext('2d');

    var mergeDiv = document.querySelector('.mergeDiv');
    var inverse = document.querySelector('.inverse');

    var merge = document.querySelector('.merge');
    var clip = document.querySelector('.clip');

    var previewWidth = compareCanvas.width = previewCanvas.width = 200;
    var previewHeight = compareCanvas.height = previewCanvas.height = 200;

    var isDrag = false;

    var disX = 0;
    var disY = 0;

    var clipDx = 0;
    var clipDy = 0;

    var previewImg = null;
    var compareImg = null;

    clipCanvas.width = previewWidth;
    clipCanvas.height = previewHeight;

    //读取文件
    input.addEventListener('change', readerFile);

    //生成对比图
    function createCompareImg() {
        compareImg = new Image();
        compareImg.crossOrigin = "Anonymous"; //解决跨域
        compareImg.src = 'http://qinyuanqiblog.github.io/images/angular/shape_lingxing.png';

        compareImg.onload = function() {
            compareCtx.drawImage(this, 0, 0, previewWidth, previewHeight);
        }
    }

    //读取文件,生成canvas预览
    function readerFile() {
        var file = this.files[0];
        // FileReader API用于读取文件，即把文件内容读入内存
        var reader = new FileReader();

        //读取文件成功
        reader.onload = function() {
            createPreviewToCanvas(reader.result);
        }
        //返回一个基于Base64编码编码的数据URI对象
        reader.readAsDataURL(file);
    }

    /**
     * 生成canvas预览图，方便后续处理
     * @param dataURL {object}        一个基于Base64编码编码的数据URI对象
     */
    function createPreviewToCanvas(dataURL) {
        previewImg = new Image();
        previewImg.src = dataURL;
        previewImg.onload = function() {
            previewCtx.drawImage(previewImg, 0, 0, previewWidth, previewHeight);
        }
        createCompareImg();
        document.querySelector('.preview-area').style.display = 'block';
    }

    //合并图片
    merge.addEventListener('click', function() {

        mergeDiv.style.display = 'block';
        mergeCanvas.width = previewWidth;
        mergeCanvas.height = previewHeight;
        mergeCtx.drawImage(previewImg, 0, 0, previewWidth, previewHeight);

    });

    //滤镜处理
    inverse.addEventListener('click', function() {
        var previewData = previewCtx.getImageData(0, 0, previewWidth, previewHeight);
        for (var i = 0; i < previewData.data.length; i += 4) {
            previewData.data[i] = 255 - previewData.data[i];
            previewData.data[i + 1] = 255 - previewData.data[i + 1];
            previewData.data[i + 2] = 255 - previewData.data[i + 2];
            previewData.data[i + 3] = 255;
        }
        previewCtx.putImageData(previewData, 0, 0);
    })

    mergeDiv.addEventListener('mousedown', mouseDownFn);
    mergeDiv.addEventListener('mousemove', mouseMoveFn);
    mergeDiv.addEventListener('mouseup', mouseUpFn);
    mergeDiv.addEventListener('mouseleave', mouseUpFn);

    //裁剪图片
    clip.addEventListener('click', createClipPreview);

    //查看剪切之后的图片
    function createClipPreview() {
        clipImg(clipDx, clipDy)
        var imgSrc = _base64ToBlob(clipCanvas.toDataURL());
        document.querySelector('.makePreview').src = imgSrc;
    }

    /**
     * base64编码数据转成blob对象
     * @param dataURL {object}        一个基于Base64编码编码的数据URI对象
     * @return result {blob object}   返回一个可以直接浏览的本地图片地址 
     */
    function _base64ToBlob(dataURL) {
        //获取源数据类型
        var mimeString = dataURL.split(',')[0].split(':')[1].split(';')[0];
        //取到base64转码后的源数据
        var str = dataURL.split(',')[1];
        //base64解码
        str = window.atob(str);
        //使用一个 Uint8Array 来存放数据
        var utf8Array = new Uint8Array(str.length);
        for (var i = 0; i < str.length; i++) {
            utf8Array[i] = str.charCodeAt(i);
        }
        //转换成一个blob对象
        var blob = new Blob([utf8Array], {
            type: mimeString
        });
        //生成可以直接访问的本地地址
        var src = URL.createObjectURL(blob);
        return src;
    }

    //裁剪图片
    function clipImg(dx, dy) {
        var proviewImgData = previewCtx.getImageData(-dx, -dy, previewWidth, previewHeight);
        var compareImgData = compareCtx.getImageData(0, 0, previewWidth, previewHeight);
        for (var i = 3; i < compareImgData.data.length; i += 4) {
            if (compareImgData.data[i] !== 0) {
                proviewImgData.data[i] = 0;
            }
        }
        clipCtx.putImageData(proviewImgData, 0, 0);
    }


    var mergeCanvasLeft = 0;
    var mergeCanvasTop = 0;

    function mouseDownFn(e) {
        var event = e || ev;
        disX = event.offsetX;
        disY = event.offsetY;

        mergeCanvasLeft = mergeCanvas.style.left == false ? 0 :  mergeCanvas.style.left;
        mergeCanvasTop =  mergeCanvas.style.top == false ? 0 : mergeCanvas.style.top;
        isDrag = true;
    }

    function mouseMoveFn(e) {
        if (isDrag) {
            var event = e || ev;
            var left = event.offsetX - disX + parseInt(mergeCanvasLeft);
            var top = event.offsetY - disY + parseInt(mergeCanvasTop);
            //也可以使用矩阵或者是translate 来做， 我现在的做法是改成了定位的形式
            // mergeCanvas.style.transform = 'matrix(1,0,0,1,' + left + ',' + top + ')';

            mergeCanvas.style.left = left + 'px';
            mergeCanvas.style.top = top + 'px';
            // 裁剪图片 生成预览图
            clipImg(left, top);

            //裁剪位置控制
            clipDx = left;
            clipDy = top;
        }
    }

    function mouseUpFn() {
        isDrag = false;
    }
</script>

</html>
```

