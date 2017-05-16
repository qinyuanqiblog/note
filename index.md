# angualr 入坑不完全指南

* __(1)__ ui.router 和 angular 一起被 require 引用的时候，会报错

> 原因解析
> required 原理引入机制没有具体研究，原因就是 router 必须在 angular 框架之后引入
> 解决办法
> 单独先引入 angular 解决问题