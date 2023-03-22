
## 起源

> 最近被前同事问是否可以帮他去爬取一个网站的数据，然后他把网站发给我了，之后我就去研究了下，
>> 本来计划用spider-flow 这个东西来爬的，毕竟能不写代码的，为啥我要去写代码，然后研究了下spider-flow 发现满足不了需求，浪费了两天时间，
>😄😄😄， 还是老老实实手写把,对spider-flow 感兴趣的可以看看我写的：<https://www.mubucm.com/doc/7rBgfYhSzrt>

## 最终效果

![图片](https://api2.mubu.com/v3/document_image/f6962e12-283b-47e8-831d-b29ea553c618-2331693.jpg)

## 作者在写这篇文章的技能和环境

- 前端略懂一二
- nodejs 一窍不通
- 数据库一窍不通
- window系统
- puppeteer 版本: 19.7.4
- node版本: 14.18.0

## 本文只适合小白阅读，大佬请出门左转~

## 页面地址

- <http://zjj.sz.gov.cn:8004/?__EVENTARGUMENT=3&ddlPageCount=20>

- 本文将以爬取一手房预售房源数据为例

![图片](https://api2.mubu.com/v3/document_image/bbdf06e6-82f1-4871-b0be-7e877ccfb9a4-2331693.jpg)

#### 页面分析

- 一手房预售信息页面信息首页数据从哪里来？

![图片](https://api2.mubu.com/v3/document_image/01ffb709-61b4-4c8b-98f2-6bc63bb14aff-2331693.jpg)

- 页面执行逻辑

![图片](https://api2.mubu.com/v3/document_image/542ef7e7-6159-4656-85bd-12a424356da1-2331693.jpg)

- 页面渲染逻辑

![图片](https://api2.mubu.com/v3/document_image/cfaf2b29-3923-4837-a172-834243594c16-2331693.jpg)

- 项目详情页跳转逻辑：<http://zjj.sz.gov.cn/ris/bol/szfdc/projectdetail.aspx?id=126809>

![图片](https://api2.mubu.com/v3/document_image/f6439137-d019-40c9-97bc-f0c138b76342-2331693.jpg)

- 证件详情页跳转逻辑：<http://zjj.sz.gov.cn/ris/bol/szfdc/certdetail.aspx?id=126809>

![图片](https://api2.mubu.com/v3/document_image/c52c1cb6-7367-4165-b07e-1283886b8654-2331693.jpg)

## 思路

- 思路1：模拟用户操作，像一个正常的用户去点击然后爬取数据，之后再把数据存储到数据库, 然后点击分页重复这个操作，直到爬取完所有数据
- 思路2：直接调用获取数据接口，然后解析数据，之后再把数据存储到数据库我们先用思路1的方式来做，
- 本来我想用思路2的做法来做，后来有个问题没解决，所以先按照思路1来实现

## 核心代码讲解

### puppetter 如何改变页面的值？

#### 官网api

![图片](https://api2.mubu.com/v3/document_image/ddbb398e-c613-4e6a-9413-dec4ce39dac0-2331693.jpg)

- 具体代码，按照20条/页去爬取
![图片](https://api2.mubu.com/v3/document_image/2340c4e1-0e93-4cf9-9b3d-4d45cb903abe-2331693.jpg)

### puppetter 如何触发事件？

- api

![图片](https://api2.mubu.com/v3/document_image/b2b084a7-28c6-4214-a2a9-84428d6b00f3-2331693.jpg)

- 实例：
![图片](https://api2.mubu.com/v3/document_image/401d3c3a-a683-4937-8d5f-eb41b5755893-2331693.jpg)

```js
page.click(#AspNetPager1 > span:nth-last-of-type(1), {delay: 100})
```

### 使用puppetter访问页面，如何去解析数据？

- 一开始我还一直被困在这个puppetter api，一直想在这个浏览器执行的时候去获取这些信息，其实这种也是可以的，但是不方便，后来百度发现可以使用cheerio这个库，像使用jquery把对页面做操作
![图片](https://api2.mubu.com/v3/document_image/e1184de6-31d5-4ef3-a529-5b2e4076a067-2331693.jpg)
- cheerio 遍历页面数据
![图片](https://api2.mubu.com/v3/document_image/f6aa4fc0-b998-42b4-b923-56134a452ec6-2331693.jpg)
- cheerio 具体代码
![图片](https://api2.mubu.com/v3/document_image/9fa4a12d-2b1a-4bba-beb9-68b3a4071112-2331693.jpg)

### 如何把保存数据到数据库？新建一个house_info 数据库，然后搞了一个presell 预售表，预售的表结构

![图片](https://api2.mubu.com/v3/document_image/e2f094d3-f9e4-4b3b-a829-6ef2f643da6d-2331693.jpg)

#### sql相关知识查询数据

- select * from presell
- 更新某一条数据：update presell set name='阿斯顿撒',enterprise=99 WHERE serial=2
- 更新所有的数据：UPDATE presell SET address='深圳'插入数据：INSERT INTO presell (mainKey,serial,id) VALUES (1111,2,3);
- 批量插入数据：INSERT INTO presell ( mainKey, serial, id, NAME, enterprise, address, date ) VALUES ( '10001', '2', '3', '4', '5', '6', '2022-02-06' ),( '10002', '2222', '3', '4', '5', '6', '2022-02-06' )

#### 如何批量插入数据

![图片](https://api2.mubu.com/v3/document_image/631d4a99-96c2-4484-9db7-b24c850b00e5-2331693.jpg)

```js
var mysql      = require('mysql2');
var connection = mysql.createConnection({
  host     : 'localhost',
  user     : 'root',
  password : 'root'
});

connection.query('use house_info')

const array = [
  [ 
    1679389969116,
    '13',
    '深房许字（2023）南山003号',
    'http://zjj.sz.gov.cn/ris/bol/szfdc/certdetail.aspx?id=126737',
    '方直珑樾山花园',
    'http://zjj.sz.gov.cn/ris/bol/szfdc/ojectdetail.aspx?id=126737',
    '深圳市龙廷房地产开发有限公司',
    '南山',
    '2023-03-02'
  ],
  [
    1679389969118,
    '13',
    '深房许字（2023）南山003号',
    'http://zjj.sz.gov.cn/ris/bol/szfdc/certdetail.aspx?id=126737',
    '方直珑樾山花园',
    'http://zjj.sz.gov.cn/ris/bol/szfdc/ojectdetail.aspx?id=126737',
    '深圳市龙廷房地产开发有限公司',
    '南山',
    '2023-03-02'
  ],
]
connection.query(`INSERT INTO presell ( mainKey, serial, idCard, idCardUrl, productName, productUrl, enterprise, location, authorizeDate )
VALUES ?`,[array], function (error, results, fields) {
  if (error) {
   log.error('批量插入失敗，错误信息==>', error)
   throw error;
  }
  // connected!
  log.info('批量插入成功', results)
});
```

## 开始编码

- puppetter 环境搞了我两天，装了新版本，chrom一直没有下载下来，😭😭😭，解决方法看后面

### 先访问一次

![图片](https://api2.mubu.com/v3/document_image/e468bafe-d7db-4309-be1e-b3ef68a9ca4b-2331693.jpg)

### 因为第一组分页的页面结构和第二组的页面结构不一样，所以要搞成不同的逻辑不同的页面结构，难搞哦

![图片](https://api2.mubu.com/v3/document_image/dc9d0b4d-1daf-4f63-9447-5f9f1848e9fe-2331693.jpg)

#### 第一页的时候的页面结构和逻辑

![图片](https://api2.mubu.com/v3/document_image/e2ad4547-a00d-45b7-83d2-8a0b7182be59-2331693.jpg)

#### 第二组分页的页面机构和逻辑

![图片](https://api2.mubu.com/v3/document_image/accd5ddf-7bfb-4aaf-9107-2b0fb8c4c620-2331693.jpg)

#### 开始第一轮的轮询

![图片](https://api2.mubu.com/v3/document_image/e5d7b523-79da-494f-9653-f9be074cfdb0-2331693.jpg)

#### 开始第二轮的轮询

![图片](https://api2.mubu.com/v3/document_image/fad8c2c8-6a26-4c7a-ac8d-d604851edccd-2331693.jpg)

### 存储数据库的逻辑

![图片](https://api2.mubu.com/v3/document_image/1e9ce03d-450a-4560-866b-b802b7a6a30b-2331693.jpg)

## 下载不了chromium的解决办法

### Failed to set up Chromium r1095492! Set "PUPPETEER_SKIP_DOWNLOAD" env variable to skip download

#### 问题截图 关键词：Failed to set up Chromium r1095492! Set "PUPPETEER_SKIP_DOWNLOAD" env variable to skip download

![图片](https://api2.mubu.com/v3/document_image/112081f4-f16e-4065-a4f4-e811afe76a29-2331693.jpg)

#### 问题原因： 下面这张图是我在家里面直接更新就好了，一点问题都没有，在公司电脑已更新就狗带，太难了

![图片](https://api2.mubu.com/v3/document_image/32e96af9-04e3-41fe-8c60-26d151f64a00-2331693.jpg)

#### 解决办法：（想直接看答案的，直接跳到终极原因 或者方法5处查看解决办法）

##### ~~方法1： 从puppeteer 源码找到下载的资源~~

- 修炼不到家，找不到，😄😄😄，后来就放弃了
![图片](https://api2.mubu.com/v3/document_image/ec809c60-6e25-4fb9-b671-5d754e1427b9-2331693.jpg)

#### ~~方法2：从chromium 官网下载对应的版本~~

- 1. 查看puppeter和chromium的对应关系，找到对应关系 然后在chromium的下载链接后面自己换一下，然后下载<https://github.com/chromium/chromium/releases/tag/111.0.5556.0>
![图片](https://api2.mubu.com/v3/document_image/92656856-48fb-4fa7-be85-f67055a534b5-2331693.jpg)
-等了两个小时，发现这个文件是不对的，700m，家里面那个电脑也就是170m。这个思路也是错的
![图片](https://api2.mubu.com/v3/document_image/67b36f83-b1a9-4843-adcb-30a2473800c5-2331693.jpg)

#### 方法3：chrome与puppeteer版本发生冲突在gitee上找了另一个思路

![图片](https://api2.mubu.com/v3/document_image/78c86a47-bf44-42ff-b2e1-5e34cc17567b-2331693.jpg)

- 我当时找到了这个issue，但是没有按照这个思路找下去，如果我直接去搜索这个关键词，可能我就不用浪费半天时间了。哈哈谷歌搜索这个关键词
![图片](https://api2.mubu.com/v3/document_image/206847da-8d77-417a-b6b2-04eff91bdc0b-2331693.jpg)
- 看这里，github地址： <https://github.com/wadezhan/billfeller.github.io/issues/232，是个深圳的大佬，感谢~>
![图片](https://api2.mubu.com/v3/document_image/99a5a762-5378-46b4-b3fa-3b9866ddbccb-2331693.jpg)

#### 方法4：puppeteer install Chromium r1095492  error换了个思路，然后进了这个网站

![图片](https://api2.mubu.com/v3/document_image/768cf23e-39b8-4e21-a5ae-848b28e70b8b-2331693.jpg)

- 看了这个issue：<https://github.com/puppeteer/puppeteer/issues/1597#issuecomment-351945645>
![图片](https://api2.mubu.com/v3/document_image/044f6e32-0c59-47fa-bbd9-3f28ecea3bd3-2331693.jpg)
- 2017年这个问题就存在了，只不过那时候大多数人用了淘宝镜像可以解决，但是我在2023-03-13的时候用淘宝镜像就发现没有那个资源，应该是没有同步过来
![图片](https://api2.mubu.com/v3/document_image/a3a02afb-a50d-429c-a57d-0458ce00534d-2331693.jpg)
- cnpm 也有这个问题
![图片](https://api2.mubu.com/v3/document_image/64de745a-d078-43d9-ab7d-978f8aeebb85-2331693.jpg)
- Download failed: server returned code 404. URL: <https://npmmirror.com/mirrors//chromium-browser-snapshots/Win_x64/1095492/chrome-win.zip>
![图片](https://api2.mubu.com/v3/document_image/cbcb3ae3-8a8d-42fc-9df8-c7894058737c-2331693.jpg)
- chromium-browser-snapshots库
![图片](https://api2.mubu.com/v3/document_image/dd5b3ef0-30e9-4bb8-b482-c17eab919615-2331693.jpg)

#### 终极原因

> 我就一直好奇这个Failed to set up Chromium r1095492! 里面的r1095492是啥东西，后来得到答案才知道，原来是一个所谓的版本号。。。，我一直以为是chromium 的版本，思路错了，他是一个chromium-browser-snapshots 里面的版本号
<https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/>
![图片](https://api2.mubu.com/v3/document_image/2d0fdb73-67f5-45c0-a482-3a5c62d5c2c4-2331693.jpg)

- 这个没有梯子上不去：<https://registry.npmmirror.com/binary.html?path=chromium-browser-snapshots/Win_x64/>
![图片](https://api2.mubu.com/v3/document_image/698d491c-b73f-4def-9904-c2f91452a2dc-2331693.jpg)
<https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/1095492/>
![图片](https://api2.mubu.com/v3/document_image/a1003433-aa58-45be-9f43-ff9775570eaa-2331693.jpg)
-下载后的资源大概长这样，两天了，你知道我两天怎么过来的吗！！！
![图片](https://api2.mubu.com/v3/document_image/8371978f-ea54-41c6-b8c9-8b3bea54654b-2331693.jpg)
- 直接把解压后的文件丢上去是不行的，必须按照puppeter 的这种格式才行，解压出来是chrome-win文件夹，
![图片](https://api2.mubu.com/v3/document_image/e19c8cca-8fdd-49d0-8f45-7012fca32c90-2331693.jpg)
- 然后把拷贝的文件，丢到当前用户下的 .cache/puppeteer 下新建一个win64-1095492文件夹下就好了
![图片](https://api2.mubu.com/v3/document_image/cad27f46-326f-4101-bdf2-96c9f272d2d3-2331693.jpg)
- 搞定，下班！！！
![图片](https://api2.mubu.com/v3/document_image/4eb96ed5-8453-4c8a-b74c-a7d72ccf8221-2331693.jpg)
- 最后，总结一下，其实自己好多次都已经触碰到了答案，只是没有注意到，😄😄，历时两天，终于搞定，感谢阅读，谢谢~

### 方法5：使用本机的chrom

- 第一步：export PUPPETEER_SKIP_CHROMIUM_DOWNLOAD=true
- 第二步：npm i puppeteer
- 第三步：<https://stackoverflow.com/questions/59786319/configure-puppeteer-executablepath-chrome-in-your-local-windows>
![图片](https://api2.mubu.com/v3/document_image/cebc179c-085a-4423-82d7-184f6d83992b-2331693.jpg)

```js
await puppeteer.launch({    headless: false,    args: ['--disable-infobars', '--no-sandbox', '--disable-setuid-sandbox'],   // window 如果复制是下面的地址是不行的，    executablePath: 'C:\Program Files\Google\Chrome\Application\chrome.exe',   // window 要把 地址里面的 \ 都变成 \ \ ,不然狗带，忘记是啥原因了，反正就是没有计算机体系知识不懂，哈哈，大概这种意思   executablePath: 'C:\Program Files\Google\Chrome\Application\chrome.exe',  });
```

## 想看源码的可以瞅瞅

[源码](https://github.com/qinyuanqiblog/house)

## 免责声明

- 本项目只是学习使用，无意对此网站进行爬虫等操作

## 参考资料

- puppeteer如何触发表单提交
![图片](https://api2.mubu.com/v3/document_image/25512407-4cdf-424b-af7c-a136ea2380e4-2331693.jpg)
- puppeteer如何执行页面的js方法
![图片](https://api2.mubu.com/v3/document_image/33d72133-e044-4dca-acb0-6f84c7673b8d-2331693.jpg)
- [Puppeteer 基本概念介绍](https://ifun.dev/post/puppeteer-introduction/)
- [puppeteer环境部署问题小记](https://github.com/wadezhan/billfeller.github.io)
- vscode 如何调试node
![图片](https://api2.mubu.com/v3/document_image/bcc8f89b-b463-41fb-8388-aaf01ba62d4d-2331693.jpg)

```js
// launch.json 配置 
{
  "name": "nodejs-debugger",
  "program": "${workspaceFolder}/index.js",
  "request": "launch",
  "skipFiles": [
      "<node_internals>/**"
  ],
  "type": "node"
},
```

- 数据库相关date空字符串处理问题原因，爬了一千多条数据，然后挂了，说插入数据库错误。。。
![图片](https://api2.mubu.com/v3/document_image/b84fb4fc-2323-416f-a97b-46c7f40bf190-2331693.jpg)
问了下大哥们，好像不行，只能传入date 和null，或者是说把date 变成字符串，哈哈，感觉不好把，有点业余
