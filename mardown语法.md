
# Markdown 不完全指南
> 简单来说就是可以使用这个语法生成html文件

> h1 - h6

# h1
## h2
### h3
#### h4
##### h5
###### h6

> 斜体 && 粗体 && 下划体 && 圆角

*asterisks* or _underscores_ &&
**asterisks** or __underscores__ &&
~~Scratch this.~~ &&
`renders`


>表情包

:bowtie:

* 无序列表
* aa
- aa
+ aa

* 有序列表

1. 列出所有元素：
2. 列出所有元素：
3. 列出所有元素：

* 列表嵌套
1. 列出所有元素：
    - 无序列表元素 A
        1. 元素 A 的有序子列表
    - 前面加四个空格
2. 列表里的多段换行：
    前面必须加四个空格，
    这样换行，整体的格式不会乱
3. 列表里引用：

    > 前面空一行
    > 仍然需要在 >  前面加四个空格

4. 列表里代码段：

    ```
    前面四个空格，之后按代码语法 ``` 书写
    ```

>*   或者直接空八个，引入代码块

* **引用**
> 我是引用的效果哦
> 我是引用的效果哦
> 我是引用的效果哦

> 区域块

```js
    这里放的是js 代码
```

```css
这里放的是css 代码
```

```html
这里放的是css 代码
```

>连接

<https://www.baidu.com>

[连接名字](https://www.baidu.com)
![](https://ss2.bdstatic.com/lfoZeXSm1A5BphGlnYG/skin/5.jpg?2"asdfsadfd")

[![alt text](http://path/to/img.jpg "titlwe")](跳转的连接)

> 单选框

- [x] xx

- [ ] xx

> 表格

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |