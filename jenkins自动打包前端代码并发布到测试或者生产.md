# 使用jenkins自动打包前端代码并发布到测试或者生产

## 针对用户：像我这种又看不懂英文，又是小白的码畜
> 前方多图预警，懒得写文字，基本上都是直接上图，还有可能写得很烂，见谅~

## 概要

* **(1)** 环境安装
* **(2)** 安装插件(Git Parameter/nodejs/publish over ssh)
* **(3)** 项目配置

### 环境安装

* [jenkins下载](https://jenkins.io/download/)
* 访问 http://localhost:8080，开始安装
![](/images/jenkins/1.png)
![](/images/jenkins/2.png)

* 如果你碰到安装不成功或者说离线安装什么鬼的，请跳过插件安装，然后参照下面这两张图的解决办法

![](/images/jenkins/3.png)
![](/images/jenkins/3-1.png)
![](/images/jenkins/4.png)

### 安装插件
![](/images/jenkins/3.png)
![](/images/jenkins/5.png)
* 安装(Git Parameter/nodejs/publish over ssh) 这三个插件

#### 配置nodejs插件
![](/images/jenkins/6.png)
![](/images/jenkins/6-1.png)
![](/images/jenkins/6-1.png)
![](/images/jenkins/6-2.png)

* 如果你碰到你的选择node版本这一栏是输入框，而不是官网api 里面的下拉框， 那恭喜你 遇到了和我一样的问题，原因是因为少了一个文件，你会相信吗，就是因为少了一个文件， 被坑了几天，那种感觉 ， 真的是爽的飞起~，例如：
![](/images/jenkins/7.png)
* [解决办法](https://blog.csdn.net/u012075238/article/details/85197034)

#### 配置publish over ssh插件 
* [参考](https://blog.csdn.net/houyefeng/article/details/51027885)

#### 配置Git Parameter插件 
* [参考](https://blog.csdn.net/hwhua1986/article/details/53841741)

## 项目配置
![](/images/jenkins/8.png)
![](/images/jenkins/8-1.png)
![](/images/jenkins/8-2.png)
![](/images/jenkins/8-3.png)
![](/images/jenkins/8-4.png)
![](/images/jenkins/8-5.png)
![](/images/jenkins/8-6.png)
![](/images/jenkins/8-7.png)
![](/images/jenkins/8-8.png)

## 配置成功，开始构建
![](/images/jenkins/9.png)
![](/images/jenkins/9-1.png)
![](/images/jenkins/9-2.png)
![](/images/jenkins/9-3.png)

## 配置过程中可能会遇到的坑

### nodejs 选择版本不是下拉

> 如果你碰到你的选择node版本这一栏是输入框，而不是官网api 里面的下拉框， 那恭喜你 遇到了和我一样的问题，原因是因为少了一个文件，你会相信吗，就是因为少了一个文件， 被坑了几天，那种感觉 ， 真的是爽的飞起~，例如：
![](/images/jenkins/7.png)
* [解决办法](https://blog.csdn.net/u012075238/article/details/85197034)

### Jenkins java.io.IOException: CreateProcess error

* 原因
![](/images/jenkins/8-3-3.png)
> 这里设置成执行shell的话， 会导致构站的时候说什么找不到sh 文件，这个时候就直接到系统设置把这个改成你本地的bash 就可以了
* [解决办法](https://stackoverflow.com/questions/15135771/hudson-on-windows-error-java-io-ioexception-cannot-run-program-sh)
![](/images/jenkins/8-3-4.png)

### SSH: Transferred 0 file(s)

> 这个是因为ssh的source file 路径配置有问题，没有好好看文档的下场，😃
* [解决办法](https://www.cnblogs.com/zongyl/p/9157488.html)

## Jenkins theme 极简式自动生成定制主题css

* [Jenkins theme 极简式自动生成定制主题css](https://blog.csdn.net/dongwuming/article/details/80010101)