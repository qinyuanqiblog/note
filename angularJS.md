# angularjs 不完全指南

* [angularjs官网](https://docs.angularjs.org)

* [Awesome AngularJS](https://github.com/gianarb/awesome-angularjs)

* [angularjs菜鸟学院](http://www.runoob.com/angularjs)

* [angular 中文网](http://www.angularjs.cn/)

* [angular新手经常会碰到的坑](http://www.ngnice.com/posts/2c8208220edb94)

## angularjs核心功能介绍

* 所有的东西都是绑在module上面的

```js

    angular
        .module('app', [])  // module
        .factory()          // 工厂
        .service()          // 服务
        .controller()       // 控制器
        .directive()        // 指令
        .filter()           // 过滤器
```

![一个angular 模块可以包括的](https://github.com/qinyuanqiblog/qinyuanqiblog.github.io/blob/master/images/angular/angular_module.png)

## angular配置阶段

![angular的几个运行阶段](http://qinyuanqiblog.github.io/images/angular/angular_zhuangtai.png)

## angular 过滤器

[详细解释](http://www.tuicool.com/articles/vmmeQvj)

> 可以通过过滤器来进行各种倒叙插入等操作

* __angular自定义过滤器demo__

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>angular自定义过滤器demo</title>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
</head>

<body ng-app="myapp" ng-controller="my">
    <ul>
        <li ng-repeat="userLayer in userLayers | reverse" ng-bind="userLayer"></li>
    </ul>
</body>
<script src="https://cdn.bootcss.com/angular.js/1.5.3/angular.min.js"></script>
<script>
    angular.module('myapp', [])
        .controller('my', function($scope, $timeout) {
            $scope.userLayers = [1, 2, 3, 4, 5, 6, 8];
        })
        .filter('reverse', function() {
            return function(items) {
                return items.slice().reverse();
            }
        })
</script>

</html>
```

## angular  常用指令

[angular所有指令大全](http://www.runoob.com/angularjs/angularjs-reference.html)

* __ng-app__ 指令初始化一个AngularJS应用程序

* __ng-init__ 指令初始化应用程序数据

* __ng-bind__ 绑定 HTML 元素到应用程序数据

* __ng-model__ 双向绑定数据

> ng-model 指令可以为应用数据提供状态值(invalid, dirty, touched, error)

```html
<form ng-app="" name="myForm" ng-init="myText = 'test@runoob.com'">
    Email:
    <input type="email" name="myAddress" ng-model="myText" required></p>
    <h1>状态</h1>
    {{myForm.myAddress.$valid}}
    {{myForm.myAddress.$dirty}}
    {{myForm.myAddress.$touched}}
</form>
```


* __ng-repeat__ 和 __ng-module__ 失效的时候可以使用$parent 解决，作用域的问题

* __ng-repeat__ for 循环遍历数据

> 一些专有变量
> $first 第一个
> $last 最后一个
> $middle 中间值
> $index 索引号 从0开始

* __ng-repeat__  的一些坑

>如果和控制器一起写的话，就会出现 $index 失效的问题
> track by 一定要放在orderBy之后，否则会影响orderBy的效果；
> 当单一数组如["a","a"]有重复元素时，需要使用track by $index来保证两个元素都会渲染，否则只会渲染一个

* __ng-repeat__ for 优化

```html
<div ng-app="" ng-init="names=[
{name:'Jani',country:'Norway'},
{name:'Hege',country:'Sweden'},
{name:'Kai',country:'Denmark'}]">
<p>循环对象：</p>
<ul>
  <li ng-repeat="x in names">
    {{ x.name + ', ' + x.country }}
  </li>
</ul>
</div>
```

* __ng-show__ 和 __ng-hide__  显示或隐藏 HTML 元素

* __ng-switch__ [api](https://docs.angularjs.org/api/ng/directive/ngSwitch)

* __ng-class-odd__ [api](https://docs.angularjs.org/api/ng/directive/ngClassOdd)

* __ng-class-even__ 一般用于隔行换色这种功能

* __ng-class__

```js
<ANY ng-switch="expression">
  <ANY ng-switch-when="matchValue1">...</ANY>
  <ANY ng-switch-when="matchValue2">...</ANY>
  <ANY ng-switch-default>...</ANY>
</ANY>
```

```html
<!--作为属性-->
<div ng-class="key === isShow ? 'active' : ''"></div>
```

```html
<!--作为css类-->
<div class="ng-class:key === isShow ? 'active' : ''"></div>
```

```html
<!--另一种写法-->
<div ng-class="{ture: 'active', false: ''}[isShow]"></div>
```

```html
<!--key/value 的形式-->
<!-- 如果redStatus 和 greenStatus的值都为真， 则分别添加对应的class，适用于添加多个class -->
<div ng-class="{'red':redStatus, 'green': greenStatus}"></div>

```

* __ng-controller__   控制器
* __ng-controller__   控制器的书写方式

```js
//常规写法
app.controller('wolrdCtrl', function($scope, $http){
    // ...
});

// 如果你希望对JS进行压缩处理，那么参数名就可能发生变化，Angular Injector将不能够正确地注入依赖的Service。于是有另外一种写法
app.controller('wolrdCtrl', ['$scope', '$http', function($scope, $http){
    // ...
}]);
```

```html
<div ng-app="app" ng-controller='myCtrl'> {{myName}} </div>
```

```js
angular.moduele('app', []).controller('myCtrl', function ($scope, $rootScope){
  $.scope.myName = '我的名字是xxxx';
  // $rootScope  可以在多个控制器中使用
})
```

* __ng-include__
> 如果是要引入外部文件的话，那么 需要把这个路径变成一个字符串类型的，如下

```html
<div ng-app="">
    <div ng-include="'example.html'"></div>
</div>
```

## angular 自定义指令

> 2017.7.14 试验发现，有时候模版里面的ng-if 不生效，解决方法是把他放到调用的地方即可，原理未知

```html
<div ng-app="angular" ng-controller="Controller">
  <div my-customer></div>
</div>
```

```js
angular.module('angular', [])
    .controller('Controller', function($scope) {
        $scope.customer = {
            name: 'Naomi',
            address: '1600 Amphitheatre'
        };
    })
    .directive('myCustomer', function() {
        return {
            restrict : 'A',
            replace : true,
            templateUrl: 'my-customer.html'
        };
});
```

* __directive常用设置__

> [官网API](https://docs.angularjs.org/guide/directive)
> [中文API](http://haodetong.github.io/2016/05/20/angular-directive/)

**(1)** restrict

> 'A' - 仅匹配属性指令

```html
    <!--属性指令-->
    <div my-directive></div>
```

> 'E' - 仅匹配标签指令

```html
    <!--标签指令-->
    <my-directive></my-directive>
```

> 'C' - 只匹配类名指令


```html
    <!--类名指令-->
    <div class="my-directive"></div>
```

> 'M' - 只匹配注释指令

```html
    <!--注释指令-->
    <!-- directive:my-directive -->
    <div></div>
```

> 默认是 'AE', 表示匹配属性或标签名, 可以根据需要进行拼接


**(2)** replace

> true:  生成的html内容会替换掉定义此指令的html
> false: 生成的html内容会插入到定义此指令的元素中
> 默认值是 false

**(3)** transclude
> 允许在自定义指令内继续嵌套
> 在下面的例子中没有tansclude属性的话，hello指令下面的别的标签就都被覆盖了

```html
<body>
  <hello>
    <p>asdjlkfjaksdfjlsdajf</p>
    <div>
      123131321
    </div>
    <strong>54664456</strong>
  </hello>
</body>
<script>
  angular.module('angular', []).directive('hello', function() {
    return {
      replace: true,
      transclude: true,
      template: '<h1>hellow  angular <p ng-transclude></p> </h1>',
    }
  });
  angular.bootstrap(document, ['angular']);
</script>
```

**(4)** controller  内部的控制器，可以把方法暴露到外部，给外部使用

**(5)** scope   独立的作用域
> 让指令有自己的作用域

```js
    angular.module('app', []).directive('hello', function (){
        return {
            scope: {}
        }
    })
```

**(5.1)** scope 的绑定策略

> scope 可以取的值：
> false为默认，表示没有独立的作用域
> true 表示有自己的独立作用域
> @ 把当前的属性作为自字符串传递，还可以绑定来自外层的scope的值,在属性之中插入{{}}即可
> = 与父元素的属性进行双向绑定
> & 传递一个来自父scope的函数，稍后调用
> @　和　true的区别　－－

> [详解](http://www.imooc.com/video/3085)

```html

<!-- demo1 -->


```

**(6)** link  对dom进行操作 [官网api](https://docs.angularjs.org/guide/directive)  一般接收的参数
> scope 控制器中的 $scope
> element 将原始的DOM元素或HTML字符串包装为jQuery元素 
> [支持jquery的方法有](https://docs.angularjs.org/api/ng/function/angular.element)
> 注意：请注意，此函数不会通过标签名称/ CSS选择器找到元素。对于由标签名称查找，尝试代替 或者，也可以使用标准的DOM API，例如。angular.element(document).find(...)$document.find()document.querySelectorAll()
> attr attrs 是具有标准化属性名称及其对应属性值

**(6)** compile  和 link 同时存在的时候，link 代码不执行

**(8)** require 指令于控制器的交互
>（1）require的值用？、^、或者？^修饰。
>（2）如果不用任何修饰，则在当前指令中进行查找控制器。
>（3）如果用^修饰，则在当前指令的父指令进行查找控制器，若未找到，则会抛出异常。
>（4）如果用？修饰，则说明在当前指令中未找到控制器，此时将以null作为第四个参数。
>（5）如果需要交互多个指令，则以数组形式给出，如：[^?a，^?b]。
> 鉴于此，为了不抛出异常，我们一般以^？来进行修饰。

## angular  常用服务(函数) [可以自定义服务]

> 在 AngularJS 中，服务是一个函数或对象，可在你的 AngularJS 应用中使用, 简单的说，就是angular自带的方法
* __为啥一定要使用这些服务__
> 在很多服务中，比如 $location 服务，它可以使用 DOM 中存在的对象，类似 window.location 对象，但 window.location 对象在 AngularJS 应用中有一定的局限性。
> AngularJS 会一直监控应用，处理事件变化， AngularJS 使用 $location 服务比使用 window.location 对象更好

* [$location](http://www.runoob.com/angularjs/angularjs-http.html)

```js
$location.absUrl() //获取当前页面的地址
```

* [$http](https://docs.angularjs.org/api/ng/service/$http)

```js
    angular中ajax请求的方法说明：
    /*
    * _http:angularJs中的$http对象
    * _url:ajax请求的URL
    * _method:请求方式：POST或GET
    * _params:GET方式请求时传递的参数
    * _data:POST方式请求时传递的参数
    * _responseType:在请求中设置XMLHttpRequestResponseType属性,""（字符串，默认）,
    * "arraybuffer"(ArrayBuffer);"blob"（blob对象）；"document"（HTTP文档）"json"(从JSON对象解析而来的JSON字符串)；
    * "text"（字符串）；"moz-blob"（Firefox的接收进度事件）；"moz-chunked-text"(文本流);"moz-chunked-arraybuffer"（ArrayBuffer流）。
    * 这个参数表示的含义就是服务器给页面返回的数据格式
    * _successCallback:请求成功的回调函数
    * _failureCallback:请求失败的回调函数
    *
    */
```

```js
//AngularJS1.5 以上版本的写法
$http({
    method: 'GET',
    url: 'angular_demo.html'
}).then(function successCallback(response){
    //请求成功执行的代码
}, function errorCallback(response){
    //请求失败执行的代码
});
```

* [$timeout](https://docs.angularjs.org/api/ngMock/service/$timeout)

> $timeout.cancel(定时器的名字);

```js
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope, $timeout) {
    $scope.myHeader = "Hello World!";
    $timeout(function () {
        $scope.myHeader = "How are you today?";
    }, 2000);
});
```

* [AngularJS scope 原理解析](https://w3ctech.com/topic/1611)
* [AngularJS事件流详解](http://www.tuicool.com/articles/qIBNve)

* __$watch__   [api](http://xlows.blog.51cto.com/5380484/1425445)
> $watch 监听 view层 上面的某一个对象，当他的值发生改变的时候触发相对应的代码
> 优化： 释放多余的watch: stopWatch()方法

* __$apply__   [api](http://www.angularjs.cn/A0a6)
> $apply把 module层 的变化传到 view层 上面去

* __$on__   [api](http://www.angularjs.cn/A0a6)
> 语法 =>  $on(name, listener);
> 用于接收 event 与 data

* __$emmit__   [api](http://www.angularjs.cn/A0a6)
> 语法 =>  $emit(name, args);
> $emit只能向parent controller传递event与data

* __$broadcast__   [api](http://xlows.blog.51cto.com/5380484/1425445)
> 语法 => $broadcast(name, args);
> $broadcast只能向child controller传递event与data

* __阻止事件冒泡__ event.stopPropagation

* __angular事件流详解demo__

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <title>angular 事件流解析</title>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
</head>

<body ng-app="app">
    <!--父级-->
    <div ng-controller="ParentCtrl">
        <!--自己-->
        <div ng-controller="SelfCtrl">
            <a ng-click="click()">点我点我点我</a>
            <!--子级-->
            <div ng-controller="ChildCtrl"></div>
        </div>
        <!--平级-->
        <div ng-controller="BroCtrl"></div>
    </div>


<br>
    <div style="color:green;">
        点击完成之后，请在控制台查看相关信息；
    </div>
</body>

<script src="https://cdn.bootcss.com/angular.js/1.5.3/angular.min.js"></script>
<script>
    var app = angular.module('app', []);

    app.controller('SelfCtrl', function($scope) {
        $scope.click = function() {
            // 向child controller传递event与data
            $scope.$broadcast('to-child', 'child');
            // 向parent controller传递event与data
            $scope.$emit('to-parent', 'parent');
        }
    });

    app.controller('ParentCtrl', function($scope) {
        // 用于接收event与data
        $scope.$on('to-parent', function(event, data) {
            // 父级能得到值
            console.log('我是on事件里面的东西哦ParentCtrl', data);
        });

        $scope.$on('to-child', function(event, data) {
            // 子级得不到值
            console.log('ParentCtrl', data);
        });
    });

    app.controller('ChildCtrl', function($scope) {
        $scope.$on('to-child', function(event, data) {
            // 子级能得到值
            console.log('ChildCtrl', data);
        });
        $scope.$on('to-parent', function(event, data) {
            // 父级得不到值
            console.log('ChildCtrl', data);
        });
    });

    app.controller('BroCtrl', function($scope) {
        $scope.$on('to-parent', function(event, data) {
            // 平级得不到值
            console.log('BroCtrl', data);
        });
        $scope.$on('to-child', function(event, data) {
            // 平级得不到值
            console.log('BroCtrl', data);
        });
    });
</script>

</html>
```

* [$interval](https://docs.angularjs.org/api/ng/service/$interval)   同 $timeout 的做法差不多
> 取消定时器 $timeout.cancel(timeName);

* [select](https://docs.angularjs.org/api/ng/directive/ngSelected)  angular select[也可以是用ng-repeat来进行for循环]

```html
<div ng-app="myApp" ng-controller="myCtrl">
    <select ng-init="selectedName" ng-model="selectedName" ng-options="value for (key, value) in names">
    </select>
</div>
<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope) {
    $scope.names = ["Google", "Runoob", "Taobao"];
    $scope.selectdName = names[0];
});
</script>
```

* [tabel](http://www.runoob.com/angularjs/angularjs-tables.html)   tabel 的相关使用

## angular 常用全局方法

* [angular 所有的方法](https://docs.angularjs.org/api/ng/function)

* __angular.lowercase()__  转换字符串为小写
* __angular.uppercase()__  转换字符串为大写
* __angular.isString()__   判断是否是一个字符串，如果是则返回true
* __angular.isNumber()__   判断是否是一个数组，如果是则返回false
* __angular.toJson()__     把数组或者对象变成字符串
* __angular.fromJson()__   把字符串变成对象
* __angular.isNumber()__   判断是否是一个数组，如果是则返回false
* __angular.element($(element) || 'js原生获取元素方法')__   判断是否是一个数组，如果是则返回false

```js
angular.module('', []).controller('', function ($scope){
    $scope.name = 'string';
    $scope.name = angular.lowercase($scope.name); //把当前字符串转换为小写
})
```

* __angular.bootstrap__  手动启动AngularJS 程序
> [官网API](https://docs.angularjs.org/api/ng/function/angular.bootstrap)
> angular.bootstrap(element, [modules], [config]);
> 其中第一个参数element:是绑定ng-app的dom元素；
> modules：绑定的模块名字
> config：附加的配置

* __angular service__    service 里面是不能直接注入$scope的

```js
    //定义一个service, 按照api 的说法，service的第二个参数放的是一个构造函数，当angular 调用service的时候会自己去实例化它
    angular.module('app', []).service('getName', GetName).controller('myCtrl', function($scope, getName){
        getName.showName();//ben
    })

    function GetName (){
        this.name = "ben"
    }

    GetName.prototype.showName = fuunction (){
        console.log(this.name)
    }
```

* __angular factory__

 ```js
 //定义一个factory,
    angular.module('app', []).factory('getName', function (getName){
        var getName = {
                showName: function () {
                    alert(1);
                }
            }
            return getName;
    })
 ```

## [Service和Factory等的区别](https://segmentfault.com/a/1190000003096933#articleHeader0)

> [stack_overflow的回答](http://stackoverflow.com/questions/15666048/angularjs-service-vs-provider-vs-factory)

## angular  依赖注入


## angular  路由

* __ngRouter和ui-router__的区别

[详细攻略](http://yijiebuyi.com/blog/3aab7ad8bccb22b4a881849c0593d5e2.html)

* __ui-view__ 的三种调用方式

* angular 使用 iframe 报错解决方案 

[方案1](https://stackoverflow.com/questions/26990014/cant-load-url-into-iframe-with-angularjs)

> __(1)__ <ui-view></ui-view>
> __(2)__ <div ui-view></div>
> __(3)__ <div class="ui-view"></div>

* __ui-router__ 的一些使用
> [官网API](https://ui-router.github.io/ng1/docs/0.3.1/index.html#/api/ui.router)

> angular ui-router通过url传值的方法：

```js
 $scope.toDiy = function(item) {
     // 适用于 两个项目中进行切换使用， 如果是一个项目之间切换请使用 $state.go(xx);
            window.location.href = window.location.pathname + '?item=' + item +'#/shop/classifiedList';
        }


    // ui-router带值传输
    // module-config 中的配置
    $state('shop.xx', {
         url:'/classifiedList/:id/:book',
    })
    // 之后在控制器中设置
    $state.go('shop.classifiedList', {id:id, book:'xx'})

```

```html
<!doctype html>
<html ng-app="myApp">
<head>
  <script src="js/angular.js"></script>
  <!-- Include the ui-router script -->
  <script src="js/angular-ui-router.min.js"></script>
  <script>
    // ...and add 'ui.router' as a dependency
    var myApp = angular.module('myApp', ['ui.router']).config(function ($stateProvider, $urlRouterProvider){
        $stateProvider
        .state('box', {
            url: '/box', // 父路由,路径调用的形式  #/box
            templateUrl: 'example.html',
            controller: 'myCtrl', //这里可以放一个控制器的名称或者是一个方法
        })
        .state('box.children', {
            url: '/children',
            templateUrl: 'children.html', //子路由，路径调用的形式  #/box/children
            controller: 'childrenCtrl'
        })
    });
  </script>
</head>
<body>
</body>
</html>
```

* __$cacheFactory__ [详细说明](http://www.cnblogs.com/ys-ys/p/4967404.html)
[堆栈溢出的解释](http://gregpike.net/demos/angular-local-storage/demo/demo.html)

> 如果您有一个请求检索常量数据，例如城市列表。每次用户进入他必须选择城市的表单时，从服务器获取此列表并不是一个好的模式！所以你必须缓存这个列表。cacheFactory是为此完成的！
> 值的注意的是，这是应用程序的缓存服务，而不是浏览器本地的缓存。所以当你刷新浏览器，初始化整个应用程序的时候，之前的缓存数据都会丢失。那么问题就来了，怎么才能刷新/初始化应用程序而不丢失之前保存的数据呢，这个可以使用localStorage或者cookies

* __angular.extend__

> angular.extend(DST, SRC) 依次将第二个参数及后续的参数的第一层属性（不管是简单属性还是对象）拷贝赋给第一个参数的第一层属性，即如果是对象，则是引用的是同一个对象，并返回第一个参数对象

* __$q, defer, promise__
 [详细解释](http://www.tuicool.com/articles/FfaA7bu)
 [另一个版本](http://www.cnblogs.com/xing901022/p/4928147.html)

* __angular.fromJson__
> angular.fromJson({a:'11', b:'cc'}) ==> Object {a: "11", b: "cc"}

* __angular.toJson__
> angular.toJson({a:'11', b:'cc'}) ==> "{"a":"11","b":"cc"}"

## angualr 入坑不完全指南

* __(1)__ ui.router 和 angular 一起被 require 引用的时候，会报错

> 原因解析
> required 原理引入机制没有具体研究，原因就是 router 必须在 angular 框架之后引入
> 解决办法
> 单独先引入 angular 解决问题
