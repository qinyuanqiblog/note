# vue-cli3 项目 token.type.endsWith is not a function 生产事故分析

## 事故描述

> 一图解千愁
![事故图片](https://api2.mubu.com/v3/document_image/5e0327cb-f065-40cf-9117-cf814af1d9d0-2331693.jpg)

## 事故造成的影响

> 生产环境某些页面打不开，控制台报错，错误信息 token.type.endsWith is not a function
![事故图](https://api2.mubu.com/v3/document_image/4b68572d-8490-49a8-af91-7ad677b1b8c5-2331693.jpg)

## 事故原因分析

* 为什么生产环境引入这个包：@vue/cli-plugin-eslint？
* token.type.endsWith is not a function报错的原因是？

### 为什么生产环境引入这个包：@vue/cli-plugin-eslint

* 因为我们项目的 lintOnSave 的配置默认就是true, 官网也说了， 如果是true的话， 会导致生产也会被启用
![lintonSave](https://api2.mubu.com/v3/document_image/e9433c74-2734-4c15-8080-996ee8148492-2331693.jpg)

当前我的项目的配置又刚好是把lintOnSave给开出来了！！！！

### token.type.endsWith is not a function报错的原因是

* 谷歌把我指引到了 eslint-plugin-vue 的官方issues，官方的大佬说，这个问题是babel-eslint的问题！！！
![eslint-plugin-vue 示例图](https://api2.mubu.com/v3/document_image/aa72f63d-7280-40db-a039-064026d0a13c-2331693.jpg)
![eslint-plugin-vue 示例图](https://api2.mubu.com/v3/document_image/aa72f63d-7280-40db-a039-064026d0a13c-2331693.jpg)

#### token.type.endsWith is not a function解决方案

##### babel-eslint 变成8.2.2版本

> 降级babel-eslint,官方babel-eslint 8.2.2 版本之后就修复了， 但是我项目的babel-eslint的版本是10.0.1啊，为啥还会有问题，想不通，网上也碰到很多人说10.0.1的有一堆问题,反正降级到8.2.2就好了

* babel-eslint 升级到8.2.2  

```npm
  npm install -D babel-eslint@8.2.2
```

![](https://api2.mubu.com/v3/document_image/d4c1b831-9340-486f-ab8a-ee42015014b9-2331693.jpg)

##### 升级 eslint-plugin-vue 到 8.3.0

```npm
  npm install -D eslint-plugin-vue@8.3.0
```

![eslint-plugin-vue示例图](https://api2.mubu.com/v3/document_image/938adc51-fc28-4280-9a0c-4e126cddd7d2-2331693.jpg)

### 如何重现这个bug？

#### 项目背景

* 基于若依前后端分离模板里面拷贝出来的项目

> 概率性，我发现使用npm install 比较容易出现这个问题，我的重现步骤是

* **1**  vue.config.js lintOnSave 变成true
* **2**  当前项目的一些依赖，主要就是babel-eslint 10.0.1 在window不同电脑里面，有的电脑，同样的版本就是报错！！
![当前项目的配置](https://api2.mubu.com/v3/document_image/56c9f39b-45ba-4fbf-b56f-b540611f8a45-2331693.jpg)
* **3**  启动服务，报错信息如下
![报错信息](https://api2.mubu.com/v3/document_image/6dacea94-d304-4e8f-84a3-2586ef5183f9-2331693.jpg)
* **4**  打包项目，控制台会报token.type.endsWith is not a function，但是打包成功，出现这种情况，如果你不注意，就把包打上去，恭喜你，领取生产bug福利
![报错信息](https://api2.mubu.com/v3/document_image/8dfd47d7-39a1-4ca2-ab26-37bcbd081b46-2331693.jpg)
* **5**  有错误的包，直接丢生产：页面打不开，控制台报错，一脸懵逼的福利😄😄😄
![报错信息](https://api2.mubu.com/v3/document_image/4b68572d-8490-49a8-af91-7ad677b1b8c5-2331693.jpg)

## 事故解决方案

* vue.config.js 生产环境把lintOnSave 关掉，就算babel-eslint 报错， 也不会导致页面开不出来

![](https://api2.mubu.com/v3/document_image/0620340d-2824-4430-9424-0e49fc34592a-2331693.jpg)

* 降低babel-eslint版本，杜绝出现这种问题，

## 引申问题

* 为啥同样的包，不同window电脑，就会报错？

## 结束语

* 本文如有错误，欢迎指正，非常感谢
* 觉得有用的老铁，点个双击，小红心走一波
* 欢迎灌水，来呀，互相伤害哈 o(∩_∩)o 哈哈

## 参考资料

[TypeError: token.type.endsWith is not a function vue eslint 问题解决](https://blog.csdn.net/qq_41011894/article/details/120793391)
[vue项目所有vue引用报token.type.endsWith is not a function错误](https://zhuanlan.zhihu.com/p/426628743)
[eslint-plugin-vue/issues](https://github.com/vuejs/eslint-plugin-vue/issues?q=token.type.endsWith+is+not+a+function)
