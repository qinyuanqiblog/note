
# canvas 不完全指南


* [多种滤镜处理效果](http://www.icodelogic.com/?p=575)
* [多种滤镜处理功能演示](http://sanyecao.me/image-filters-by-canvas.html#参考文档)

```js
    // canvas demo
    var canvas = document.creatElement('canvas');
    var body = document.querySelector('body');
    var ctx = canvas.getContext('2d');//获得一个2d画布;
    ctx.beginPath(); //设置画笔的开始位置，隔离多个画笔
    ctx.moveTo(100, 100);//设置画笔开始的位置
    ctx.lineTo(200, 700);//从画笔开始到那个位置
    ctx.lineTo(100, 200);
        ····
    ctx.closePath(); //这个画笔结束的范围，不必和beinPath 成对出现，将笔点返回到当前子路径起始点的方法。它尝试从当前点到起始点绘制一条直线。 如果图形已经是封闭的或者只有一个点，那么此方法不会做任何操作

    ctx.lineWidth = 5;//设置画笔的大小
    ctx.fillStyle = 'red';//设置填充色
    ctx.fill();//调用填充方法
    ctx.stroke(); //stroke() 方法会实际地绘制出通过 moveTo() 和 lineTo() 方法定义的路径

```

* __ctx.fillText__  把文字转成图片 [api](http://www.w3school.com.cn/tags/canvas_filltext.asp)


* __ctx.drawImage__ 绘制图像
> [api](https://developer.mozilla.org/zh-CN/docs/Web/API/CanvasRenderingContext2D/drawImage)
> [demo](http://www.loveqiao.com/dom/html5css3/hecheng/)
> 绘制语法
> ctx.drawImage(image, dx, dy);
> ctx.drawImage(image, dx, dy, dWidth, dHeight);
> ctx.drawImage(image, sx, sy, sWidth, sHeight, dx, dy, dWidth, dHeight);
> ctx.drawImage(canvasElement,dx, dy); 也可以使用这个方法把一个canvas元素插入到画布中
> 必须在图片载入成功之后 再去使用这个方法，否则 无法绘制到图片

> Uncaught DOMException: Failed to execute 'toDataURL' on 'HTMLCanvasElement': Tainted canvases may not be exported.
>如果出现以上错误，请在服务器环境下运行，可能是受到同源策略的影响

```js
// 使用drawImage 方法画一张图

```

* __HTMLCanvasElement.toDataURL()__
> [api](https://developer.mozilla.org/zh-CN/docs/Web/API/HTMLCanvasElement/toDataURL)
> 语法
> canvas.toDataURL(type, encoderOptions);
> 默认是png格式的图片
> [png jpg  jpeg 图片的区别](http://www.xwbetter.com/image-format/)

* __将toDataURL转换成为blob对象实例__

```js
        //获取到 经过base64转码之后的data数据
        var dataURI = canvasElement.toDataURL();
        //数据的类型
        var mimeString = dataURI.split(',')[0].split(':')[1].split(';')[0];
        //取到数据源
        var str = url.split(',')[1];
        //解码一个已经被base-64编码过的数据
        str = window.atob(str);
        //Uint8Array类型数组表示的8位无符号整数数组
        var utf8Array = new Uint8Array(str.length);
        for (var i = 0; i < str.length; i++) {
            utf8Array[i] = str.charCodeAt(i);
        }
        //将数据转化成blob 对象
        var blob = new Blob([utf8Array], {
            type: mimeString
        });
        //得到一个可以直接访问的blob地址
        var src = URL.createObjectURL(blob);
```

* __ctx.getImageData__  获取到画布上所有的像素点，并且返回 ImageData 对象 [api](http://www.w3school.com.cn/tags/canvas_getimagedata.asp)
> 语法 var imgData=context.getImageData(x,y,width,height)
> 对于 ImageData 对象中的每个像素，都存在着四方面的信息，即 RGBA 值：
> R - 红色 (0-255)
> G - 绿色 (0-255)
> B - 蓝色 (0-255)
> A - alpha 通道 (0-255; 0 是透明的，255 是完全可见的)
> color/alpha 以数组形式存在，并存储于 ImageData 对象的 data 属性中

```js
//以下代码可获得被返回的 ImageData 对象中第一个像素的 color/alpha 信息
red=imgData.data[0];
green=imgData.data[1];
blue=imgData.data[2];
alpha=imgData.data[3];
```

```js
//demo http://www.w3school.com.cn/tags/canvas_getimagedata.asp
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
var img=document.getElementById("tulip");
ctx.drawImage(img,0,0);
var imgData=ctx.getImageData(0,0,c.width,c.height);
// 反转颜色
for (var i=0;i<imgData.data.length;i+=4)
  {
  imgData.data[i]=255-imgData.data[i];
  imgData.data[i+1]=255-imgData.data[i+1];
  imgData.data[i+2]=255-imgData.data[i+2];
  imgData.data[i+3]=255;
  }
ctx.putImageData(imgData,0,0);
```

* __ctx.putImageData__  获取到画布上所有的像素点，并且返回 ImageData 对象 [api](http://www.w3school.com.cn/tags/canvas_putimagedata.asp)

* __ctx.font__  设置画布的字体

```js
//常规设置
ctx.font='italic 20px serif'

//在FontFaceAPI 的帮助下，您可以在画布中使用之前明确加载字体
var f = new FontFace('test', 'url(x)');

f.load().then(function() {
  // Ready to use the font in a canvas context
});
```

* __ctx.fillText__  在画布上绘制文本
> ctx.fillText(text,x,y,maxWidth)
> text 规定在画布上输出的文本
> x	开始绘制文本的 x 坐标位置（相对于画布）
> y	开始绘制文本的 y 坐标位置（相对于画布）
> maxWidth 可选。允许的最大文本宽度，以像素计


* 可以在图片成功加载完成之后获取到图片实际的宽高

> img.naturalHeight
> img.naturalWidth