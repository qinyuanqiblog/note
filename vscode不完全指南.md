
<!--

/*
 *-------------------------------------------------------------
 * @File  : Visual_Studio_Code 配置
 * @Author: QinYuanqi
 * @Email : qinyuanqiuse@gmail.com
 * @GitHub: qinyuanqiblog.github.io
 * @Date  :2017-03-22 23:35:43
 * @Last Modified by: QinYuanqi
 * @Last Modified time: 2017-12-14 14:46:34
 *-------------------------------------------------------------
 */

-->

# Visual Studio Code 入门简介

### 下载地址

* [传送门](https://code.visualstudio.com/)

* [官网api](https://github.com/Microsoft/vscode-tips-and-tricks)

* [awesome-vscode](https://github.com/viatsko/awesome-vscode)

## 常用插件介绍

* [Visual Studio Code 插件库](https://marketplace.visualstudio.com)

### 代码补全
<!-- 2018.3.8 v1.21 版本不需要把这个功能集成到里面去了， 所以不需要了 -->
* [Auto Close Tag ](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-close-tag) 自动关闭标签

![](https://raw.githubusercontent.com/formulahendry/vscode-auto-close-tag/master/images/usage.gif)

* [Auto Rename Tag ](https://marketplace.visualstudio.com/items?itemName=formulahendry.auto-rename-tag) 自动重命名标签

![](https://raw.githubusercontent.com/formulahendry/vscode-auto-rename-tag/master/images/usage.gif)

* [HTML Snippets](https://marketplace.visualstudio.com/items?itemName=abusaidm.html-snippets) html代码片段

* [JavaScript ES6 code snippets](https://marketplace.visualstudio.com/items?itemName=xabikos.JavaScriptSnippets) es6代码片段

* [jQuery Code Snippets](https://marketplace.visualstudio.com/items?itemName=donjayamanne.jquerysnippets) jQuery 代码片段

* [Path Intellisense](https://marketplace.visualstudio.com/items?itemName=christian-kohler.path-intellisense) 自动补全路径

![](http://i.giphy.com/iaHeUiDeTUZuo.gif)

* [HTML CSS Class Completion](https://marketplace.visualstudio.com/items?itemName=Zignd.html-css-class-completion) 自动搜索工程下的所有class，并生成提示列表

* [CSS Peek](https://marketplace.visualstudio.com/items?itemName=pranaygp.vscode-css-peek) 跳转到css 定义

>类似的插件还有
> [Class autocomplete for HTML](https://marketplace.visualstudio.com/items?itemName=AESSoft.aessoft-class-autocomplete)
> [HTML CSS Support](https://marketplace.visualstudio.com/items?itemName=ecmel.vscode-html-css)

* [Guides](https://marketplace.visualstudio.com/items?itemName=spywhere.guides)  缩进辅助线
> ps 其实可以不装这个插件，直接开启vscode 默认设置即可, 我一般使用 Indenticator 这个插件来配合 默认的设置即可
> 经过实验发现， 自带的缩进辅助线有一些bug，缩进到第四列的时候，缩进线会变大一倍，同理八列的时候也是一样的，应该是设计的时候就是这样的把

```js
"editor.renderIndentGuides": true,
```

* [Indenticator](https://marketplace.visualstudio.com/items?itemName=SirTori.indenticator) 高亮当前缩进辅助线

* [filesize](https://marketplace.visualstudio.com/items?itemName=mkxml.vscode-filesize) 在状态栏显示文件大小

![](https://cldup.com/_Y52O-UfkK.jpg)

* [Rainbow Brackets](https://marketplace.visualstudio.com/items?itemName=2gua.rainbow-brackets) 给括号添加颜色[不维护了， 建议添加下面那个]

![](http://www.2gua.info/static/uploads/20160509171502.gif)
>类似的插件有
> [Bracket Pair Colorizer](https://marketplace.visualstudio.com/items?itemName=CoenraadS.bracket-pair-colorizer)
![](https://github.com/CoenraadS/BracketPair/raw/master/images/example.png)

* [Multiple clipboards for VSCode](https://marketplace.visualstudio.com/items?itemName=slevesque.vscode-multiclip) 多个剪切板 ctrl + alt + v

* [SVG Viewer](https://marketplace.visualstudio.com/items?itemName=cssho.vscode-svgviewer) SVG查看器

![](https://github.com/cssho/vscode-svgviewer/raw/master/img/preview.png)

* [Color Picker](https://marketplace.visualstudio.com/items?itemName=anseki.vscode-color) 取色器

![](https://github.com/anseki/vscode-color/raw/master/s-01.gif)

* [CodeMetrics](https://marketplace.visualstudio.com/items?itemName=kisstkondoros.vscode-codemetrics) 计算js 代码复杂度

* [Output Colorizer](https://marketplace.visualstudio.com/items?itemName=IBM.output-colorizer) 让集成的输出栏目字体高亮

* [Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) 代码拼写检查器

### 代码格式化

* [Beautify](https://marketplace.visualstudio.com/items?itemName=HookyQR.beautify) 保存自动美化代码

* [Minify](https://marketplace.visualstudio.com/items?itemName=HookyQR.minify) 压缩代码

* [HTMLHint](https://marketplace.visualstudio.com/items?itemName=mkaufman.HTMLHint) HTML校验

![](https://raw.githubusercontent.com/Microsoft/vscode-htmlhint/master/htmlhint/images/hero.png)

* [stylelint](https://marketplace.visualstudio.com/items?itemName=shinnn.stylelint)  css验证插件

* 温馨提示：
> stylelint 默认没有验证规则，so,需要自己写配置了
> 已经封装好的验证插件 npm install stylelint-config-standard (相关设置可以在手册中查看，很详细，可以添加和修改相关规则)

* [CSScomb](https://marketplace.visualstudio.com/items?itemName=mrmlnc.vscode-csscomb) CSS，Less，SCSS或Sass的编码样式格式化程序

* [ESLint](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) Javascript代码校验

* [TSLint](https://marketplace.visualstudio.com/items?itemName=eg2.tslint)  TypeScript 代码校验

* [Alignment](https://marketplace.visualstudio.com/items?itemName=annsk.alignment)  alignment 对齐

* [chang-case](https://cloud.githubusercontent.com/assets/2899448/10712456/3c5e29b6-7a9c-11e5-9ce4-7eb944889696.gif) 命名格式化插件

* [caniuse](https://marketplace.visualstudio.com/items?itemName=akamud.vscode-caniuse) css兼容性查询

### 代码注释

* [vscode-fileheader](https://marketplace.visualstudio.com/items?itemName=mikey.vscode-fileheader) 添加javascript文件头部注释

![](https://github.com/zhaopengme/vscode-fileheader/raw/master/fileheader.gif)

* [Document This](https://marketplace.visualstudio.com/items?itemName=joelday.docthis) TypeScript和JavaScript文件生成详细的JSDoc注释

* [change-case](https://marketplace.visualstudio.com/items?itemName=wmaurer.change-case) js 命名转换 比如驼峰转化成小写的写法

![](https://github.com/joelday/vscode-docthis/raw/master/images/demo.gif)

* [Output Colorizer](https://marketplace.visualstudio.com/items?itemName=IBM.output-colorizer)  控制台主题插件

![](https://raw.githubusercontent.com/IBM-Bluemix/vscode-log-output-colorizer/master/github-assets/screenshot-4.jpg)

### 代码调试

* [Debugger for Chrome](https://marketplace.visualstudio.com/items?itemName=msjsdiag.debugger-for-chrome) 谷歌调试器  配置完成后，需要关闭谷歌浏览器之后再开启调试功能方可使用

![](https://cdn.rawgit.com/Microsoft/vscode-chrome-debug/master/images/demo.gif)

* [Code Runner](https://marketplace.visualstudio.com/items?itemName=formulahendry.code-runner) 运行选中的代码

![](https://github.com/formulahendry/vscode-code-runner/raw/master/images/usage.gif)
![](https://github.com/formulahendry/vscode-code-runner/raw/master/images/usageRunByLanguage.gif)

* [Debugger for Firefox](https://marketplace.visualstudio.com/items?itemName=hbenl.vscode-firefox-debug) 火狐调试器

* [REST Client](https://marketplace.visualstudio.com/items?itemName=humao.rest-client) http调试

![](https://github.com/Huachao/vscode-restclient/raw/master/images/usage.gif)

* [Sort Lines](https://marketplace.visualstudio.com/items?itemName=Tyriar.sort-lines)

![](https://github.com/Tyriar/vscode-sort-lines/raw/master/images/usage-animation.gif)

### 代码测试

* [Wallaby.js](https://marketplace.visualstudio.com/items?itemName=WallabyJs.wallaby-vscode)  一个测试框架

### Markdown相关

* [markdownlint](https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint) Markdown 验证插件

* [Auto-Open Markdown Preview ](https://marketplace.visualstudio.com/items?itemName=hnw.vscode-auto-open-markdown-preview) Markdown实时预览

* [Instant Markdown](https://marketplace.visualstudio.com/items?itemName=dbankier.vscode-instant-markdown) Markdown浏览器预览

### 浏览器相关

* [View In Browser](https://marketplace.visualstudio.com/items?itemName=qinjia.view-in-browser) 在浏览器中查看html文件  快捷键 ctrl + f1 默认谷歌浏览器
* [open in browser](https://marketplace.visualstudio.com/items?itemName=techer.open-in-browser) 上面那个不行就使用这个  快捷键 alt + b 默认谷歌浏览器

### git相关插件

* [Git History](https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory)  git 历史

![](https://raw.githubusercontent.com/DonJayamanne/gitHistoryVSCode/master/images/gitLogv2.gif)

* [Git Blame](https://marketplace.visualstudio.com/items?itemName=waderyan.gitblame)  git Blame  看看是谁的锅

![](https://github.com/wadeanderson7/vscode-gitblame/raw/master/images/GitBlamePreview.gif)

* [GitLens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) gitLens  必装 ，超好用

* [Better Merge](https://marketplace.visualstudio.com/items?itemName=pprice.better-merge) 更好的处理git冲突

### sublime相关

* [Monokai Extended](https://marketplace.visualstudio.com/items?itemName=Scatolina.theme-monokaiextended) Monokai个主题

* [Sublime Text Keymap](https://marketplace.visualstudio.com/items?itemName=ms-vscode.sublime-keybindings) 同步sublime的快捷键

### 项目管理

* [Project Manager](https://marketplace.visualstudio.com/items?itemName=alefragnani.project-manager)

> 按下 F1 输入 Edit Projects 如下编辑，一个json 对应的是一个需要打开的项目 , 配置完成之后可以通过  Project Manage: List Project Open选项来打开对应的项目

```arr
[
    {
        "name": "sass",
        "rootPath": "E:\\sass",
        "paths": [],
        "group": ""
    },
     {
        "name": "module",
        "rootPath": "E:\\fff",
        "paths": [],
        "group": ""
    }
]
```

### 同步相关配置和插件

* [Settings Sync](https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync) 同步Visual Studio Code的各种配置 发现同步效果不是很完美， 有些插件没有同步

### vue相关

* [vue](https://marketplace.visualstudio.com/items?itemName=liuji-jim.vue) 语法高亮

* [Vue 2 Snippets](https://marketplace.visualstudio.com/items?itemName=hollowtree.vue-snippets) Vue 2 Snippets代码片段

* [vetur](https://marketplace.visualstudio.com/items?itemName=octref.vetur)   自己看api把

* [如何配置并利用vsCode编写符合Standard标准的代码](https://juejin.im/post/59ec17bdf265da4309444e05) vue如何配置并利用vsCode编写符合Standard标准的代码

* [VueHelper](https://marketplace.visualstudio.com/items?itemName=oysun.vuehelper) Vue，Vue-router和Vuex的代码片段

* [vue-beautify ](https://marketplace.visualstudio.com/items?itemName=peakchen90.vue-beautify) vue美化插件

![](https://github.com/peakchen90/vue-beautify/raw/master/source/preview.gif)

### 娱乐性插件

* [background](https://marketplace.visualstudio.com/items?itemName=shalldie.background) 改变背景图片

![](https://raw.githubusercontent.com/shalldie/vscode-background/master/gif/show.gif)

* [Emoji](https://marketplace.visualstudio.com/items?itemName=Perkovec.emoji) 添加表情

![](https://github.com/Perkovec/Emoji/raw/master/example.gif)

## 主题推荐

* [vscode-icons ](https://marketplace.visualstudio.com/items?itemName=robertohuertasm.vscode-icons) 侧栏主题推荐

![](https://raw.githubusercontent.com/vscode-icons/vscode-icons/master/images/screenshot.gif)

## GIT 功能区

* 按照提示操作就好，甘怕铁

## degugger API

* [官网教程](https://code.visualstudio.com/docs/editor/debugging)

[emment快捷键](https://docs.emmet.io/cheat-sheet/)

## 一些快捷键 (基于sublimeTestkeymaps上的)

* ctrl + z 撤销
* ctrl + y 恢复
* ctrl + shift + u 打开输出面板
* ctrl + shift + y 打开控制台面板
* ctrl + l 选中当前行
* ctrl + o 打开当前文件根目录
* ctrl + q 快速切换
* ctrl + b  隐藏侧栏
* ctrl + shift + v  md格式文件直接预览
* 以下设置需要修改快捷键
> ctrl + shift + y  打开问题栏
> ctrl + shift + u  打开输出栏
> ctrl + shift + i  打开调式控制台
> ctrl + shift + o  打开终端


* shift + f12  在函数名处按下此快捷键，可以快速查看函数的定义

## 常用lunch.json设置

```json
{
    "version": "0.2.0",
    "configurations": [{
            "name": "local for Chrome",
            "type": "chrome",
            "request": "launch",
            "webRoot": "${workspaceRoot}",
            "file": "${file}"
        },
        {
            "name": "service for Chrome",
            "type": "chrome",
            "request": "launch",
            "url": "http://localhost:55555/${relativeFile}",
            "webRoot": "${workspaceRoot}"
        }
    ]
}
```

## 常用tasks.json设置

```json
{
    "version": "0.1.0",
    "tasks": [{
        "taskName": "gulp-service",
        "command": "gulp",
        "isShellCommand": true,
        "windows": {
            "args": [
                "service"
            ]
        }
    }, {
        "taskName": "gulp-size",
        "command": "gulp",
        "isShellCommand": true,
        "windows": {
            "args": [
                "size"
            ]
        }
    }]
}
```

## 用户设置

> 个性设置，可自行更改

```json
{
      //当前参考线的颜色设置
     "indenticator.color.dark": "#ff6700",
     // 是否开启默认缩进辅助线
     "editor.renderIndentGuides": true,
     // 是否显示空格
     "editor.renderWhitespace": "none",
     //允许在任何文件中设置断点
     "debug.allowBreakpointsEverywhere": true,
     //允许内联显示调试信息
     "debug.inlineValues": true,
     //设置默认字体大小
     "editor.fontSize": 16,
     //迷你菜单是否开启
     "editor.minimap.enabled": true,
     //设置Beautify插件自执行[保存自动格式化]
     "editor.formatOnSave": true,
     "editor.tabCompletion": true,
     //控制代码片段提示的位置
     "editor.snippetSuggestions": "top",
     //控制换行方式
     "editor.wordWrap": "on",
     //插件自动更新
     "extensions.autoUpdate": true,
     //自动保存
     "files.autoSave": "afterDelay",
     //修改fileheader模板
     "fileheader.tpl": "/*\r\n *-------------------------------------------------------------\r\n * @File  : Describe the file  \r\n * @Author: {author} \r\n * @Email : qinyuanqiuse@gmail.com \r\n * @GitHub: qinyuanqiblog.github.io \r\n * @Date  : {createTime} \r\n * @Last Modified by:   {lastModifiedBy} \r\n * @Last Modified time: {updateTime} \r\n *-------------------------------------------------------------\r\n */\r\n",
     //fileheader插件相关配置
     "fileheader.Author": "QinYuanqi",
     "fileheader.LastModifiedBy": "QinYuanqi",
     //是否使用git
     "git.enabled": false,
     //设置外部终端路径
     "terminal.external.windowsExec": "C:\\Users\\Public\\Desktop\\Cygwin64 Terminal",
     //设置内部终端
     "terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe",
     //工作区主题
     "workbench.colorTheme": "Monokai Extended",
     //侧栏主题
     "workbench.iconTheme": "vscode-icons",
     //侧栏位置
     "workbench.sideBar.location": "right",
     "workbench.editor.closeOnFileDelete": false,
     //工作区的一些个性化设置
     "workbench.experimental.colorCustomizations": {
         "statusBarBackground": "#0373ff",
         //"editorWhitespaces": "#ff0000",
         "editorCursor": "#ff0000"
         // "editorLineNumbers": "#ff6803"
         //"editorLineNumbers": "#b12457"
     },
     // 基于活动编辑器控制窗口标题。基于上下文替换变量:
     // ${activeEditorShort}: 例如 myFile.txt
     // ${activeEditorMedium}: 例如 myFolder/myFile.txt
     // ${activeEditorLong}:  例如 /Users/Development/myProject/myFile.txt
     // ${rootName}: 例如 myProject
     // ${rootPath}: 例如 /Users/Development/myProject
     // ${appName}: 例如 VS Code
     // ${dirty}: 一个更新指示器，指示活动编辑器是否更新
     // ${separator}: 一个条件分隔符("-")，仅在左右是具有值的变量时才显示
     "window.title": "${appName}${separator}${rootName}${separator}${activeEditorShort}${dirty}",
     "window.zoomLevel": 1,
     //同步vscode 相关设置
     "sync.gist": "a4df52dbcf74cddad55b9ba5b11921ce",
     "sync.lastUpload": "2017-04-10T14:52:45.942Z",
     "sync.version": 262,
     "sync.lastDownload": "",
     "sync.autoDownload": false,
     "sync.autoUpload": false,
     "sync.showSummary": true,
     "sync.forceDownload": false,
     "sync.anonymousGist": false,
     "sync.host": "",
     "sync.pathPrefix": "",
     //Csscomb 自定义规则校验
     "csscomb.preset": {

        "exclude": [
            ".git/**",
            "node_modules/**",
            "bower_components/**"
        ],
        // Whether to add a semicolon after the last value/mixin.
        "always-semicolon": true,
        // Set indent for code inside blocks, including media queries and nested rules.
        "block-indent": "    ",
        // Unify case of hexadecimal colors.
        "color-case": "lower",
        // Whether to expand hexadecimal colors or use shorthands.
        "color-shorthand": true,
        // Unify case of element selectors.
        "element-case": "lower",
        // Add/remove line break at EOF.
        "eof-newline": true,
        // Add/remove leading zero in dimensions.
        "leading-zero": false,
        // Unify quotes style.
        "quotes": "single",
        // Remove all rulesets that contain nothing but spaces.
        "remove-empty-rulesets": true,
        // Set space after `:` in declarations.
        "space-after-colon": " ",
        // Set space after combinator (for example, in selectors like `p > a`).
        "space-after-combinator": " ",
        // Set space after `{`.
        "space-after-opening-brace": "\n",
        // Set space after selector delimiter.
        "space-after-selector-delimiter": "\n",
        // Set space before `}`.
        "space-before-closing-brace": "\n",
        // Set space before `:` in declarations.
        "space-before-colon": "",
        // Set space before combinator (for example, in selectors like `p > a`).
        "space-before-combinator": " ",
        // Set space before `{`.
        "space-before-opening-brace": " ",
        // Set space before selector delimiter.
        "space-before-selector-delimiter": "",
        // Set space between declarations (i.e. `color: tomato`).
        "space-between-declarations": "\n",
        // Whether to trim trailing spaces.
        "strip-spaces": true,
        // Whether to remove units in zero-valued dimensions.
        "unitless-zero": true,
        // Whether to align prefixes in properties and values.
        "vendor-prefix-align": true,
        // Sort properties in particular order.
        "sort-order": [
            // 参考腾讯的规范
            [
                "display",
                "visibility",
                "float",
                "clear",
                "overflow",
                "overflow-x",
                "overflow-y",
                "clip",
                "zoom"
            ],
            [
                "table-layout",
                "empty-cells",
                "caption-side",
                "border-spacing",
                "border-collapse",
                "list-style",
                "list-style-position",
                "list-style-type",
                "list-style-image"
            ],
            [
                "-webkit-box-orient",
                "-webkit-box-direction",
                "-webkit-box-decoration-break",
                "-webkit-box-pack",
                "-webkit-box-align",
                "-webkit-box-flex"
            ],
            [
                "position",
                "top",
                "right",
                "bottom",
                "left",
                "z-index"
            ],
            [
                "margin",
                "margin-top",
                "margin-right",
                "margin-bottom",
                "margin-left",
                "-webkit-box-sizing",
                "-moz-box-sizing",
                "box-sizing",
                "border",
                "border-width",
                "border-style",
                "border-color",
                "border-top",
                "border-top-width",
                "border-top-style",
                "border-top-color",
                "border-right",
                "border-right-width",
                "border-right-style",
                "border-right-color",
                "border-bottom",
                "border-bottom-width",
                "border-bottom-style",
                "border-bottom-color",
                "border-left",
                "border-left-width",
                "border-left-style",
                "border-left-color",
                "-webkit-border-radius",
                "-moz-border-radius",
                "border-radius",
                "-webkit-border-top-left-radius",
                "-moz-border-radius-topleft",
                "border-top-left-radius",
                "-webkit-border-top-right-radius",
                "-moz-border-radius-topright",
                "border-top-right-radius",
                "-webkit-border-bottom-right-radius",
                "-moz-border-radius-bottomright",
                "border-bottom-right-radius",
                "-webkit-border-bottom-left-radius",
                "-moz-border-radius-bottomleft",
                "border-bottom-left-radius",
                "-webkit-border-image",
                "-moz-border-image",
                "-o-border-image",
                "border-image",
                "-webkit-border-image-source",
                "-moz-border-image-source",
                "-o-border-image-source",
                "border-image-source",
                "-webkit-border-image-slice",
                "-moz-border-image-slice",
                "-o-border-image-slice",
                "border-image-slice",
                "-webkit-border-image-width",
                "-moz-border-image-width",
                "-o-border-image-width",
                "border-image-width",
                "-webkit-border-image-outset",
                "-moz-border-image-outset",
                "-o-border-image-outset",
                "border-image-outset",
                "-webkit-border-image-repeat",
                "-moz-border-image-repeat",
                "-o-border-image-repeat",
                "border-image-repeat",
                "padding",
                "padding-top",
                "padding-right",
                "padding-bottom",
                "padding-left",
                "width",
                "min-width",
                "max-width",
                "height",
                "min-height",
                "max-height"
            ],
            [
                "font",
                "font-family",
                "font-size",
                "font-weight",
                "font-style",
                "font-variant",
                "font-size-adjust",
                "font-stretch",
                "font-effect",
                "font-emphasize",
                "font-emphasize-position",
                "font-emphasize-style",
                "font-smooth",
                "line-height",
                "text-align",
                "-webkit-text-align-last",
                "-moz-text-align-last",
                "-ms-text-align-last",
                "text-align-last",
                "vertical-align",
                "white-space",
                "text-decoration",
                "text-emphasis",
                "text-emphasis-color",
                "text-emphasis-style",
                "text-emphasis-position",
                "text-indent",
                "-ms-text-justify",
                "text-justify",
                "letter-spacing",
                "word-spacing",
                "-ms-writing-mode",
                "text-outline",
                "text-transform",
                "text-wrap",
                "-ms-text-overflow",
                "text-overflow",
                "text-overflow-ellipsis",
                "text-overflow-mode",
                "-ms-word-wrap",
                "word-wrap",
                "-ms-word-break",
                "word-break"
            ],
            [
                "color",
                "background",
                "filter:progid:DXImageTransform.Microsoft.AlphaImageLoader",
                "background-color",
                "background-image",
                "background-repeat",
                "background-attachment",
                "background-position",
                "-ms-background-position-x",
                "background-position-x",
                "-ms-background-position-y",
                "background-position-y",
                "-webkit-background-clip",
                "-moz-background-clip",
                "background-clip",
                "background-origin",
                "-webkit-background-size",
                "-moz-background-size",
                "-o-background-size",
                "background-size"
            ],
            [
                "outline",
                "outline-width",
                "outline-style",
                "outline-color",
                "outline-offset",
                "opacity",
                "filter:progid:DXImageTransform.Microsoft.Alpha(Opacity",
                "-ms-filter:\\'progid:DXImageTransform.Microsoft.Alpha",
                "-ms-interpolation-mode",
                "-webkit-box-shadow",
                "-moz-box-shadow",
                "box-shadow",
                "filter:progid:DXImageTransform.Microsoft.gradient",
                "-ms-filter:\\'progid:DXImageTransform.Microsoft.gradient",
                "text-shadow"
            ],
            [
                "-webkit-transition",
                "-moz-transition",
                "-ms-transition",
                "-o-transition",
                "transition",
                "-webkit-transition-delay",
                "-moz-transition-delay",
                "-ms-transition-delay",
                "-o-transition-delay",
                "transition-delay",
                "-webkit-transition-timing-function",
                "-moz-transition-timing-function",
                "-ms-transition-timing-function",
                "-o-transition-timing-function",
                "transition-timing-function",
                "-webkit-transition-duration",
                "-moz-transition-duration",
                "-ms-transition-duration",
                "-o-transition-duration",
                "transition-duration",
                "-webkit-transition-property",
                "-moz-transition-property",
                "-ms-transition-property",
                "-o-transition-property",
                "transition-property",
                "-webkit-transform",
                "-moz-transform",
                "-ms-transform",
                "-o-transform",
                "transform",
                "-webkit-transform-origin",
                "-moz-transform-origin",
                "-ms-transform-origin",
                "-o-transform-origin",
                "transform-origin",
                "-webkit-animation",
                "-moz-animation",
                "-ms-animation",
                "-o-animation",
                "animation",
                "-webkit-animation-name",
                "-moz-animation-name",
                "-ms-animation-name",
                "-o-animation-name",
                "animation-name",
                "-webkit-animation-duration",
                "-moz-animation-duration",
                "-ms-animation-duration",
                "-o-animation-duration",
                "animation-duration",
                "-webkit-animation-play-state",
                "-moz-animation-play-state",
                "-ms-animation-play-state",
                "-o-animation-play-state",
                "animation-play-state",
                "-webkit-animation-timing-function",
                "-moz-animation-timing-function",
                "-ms-animation-timing-function",
                "-o-animation-timing-function",
                "animation-timing-function",
                "-webkit-animation-delay",
                "-moz-animation-delay",
                "-ms-animation-delay",
                "-o-animation-delay",
                "animation-delay",
                "-webkit-animation-iteration-count",
                "-moz-animation-iteration-count",
                "-ms-animation-iteration-count",
                "-o-animation-iteration-count",
                "animation-iteration-count",
                "-webkit-animation-direction",
                "-moz-animation-direction",
                "-ms-animation-direction",
                "-o-animation-direction",
                "animation-direction"
            ],
            [
                "content",
                "quotes",
                "counter-reset",
                "counter-increment",
                "resize",
                "cursor",
                "-webkit-user-select",
                "-moz-user-select",
                "-ms-user-select",
                "user-select",
                "nav-index",
                "nav-up",
                "nav-right",
                "nav-down",
                "nav-left",
                "-moz-tab-size",
                "-o-tab-size",
                "tab-size",
                "-webkit-hyphens",
                "-moz-hyphens",
                "hyphens",
                "pointer-events"
            ]
        ]
     }
 }
```

> 20170914的文档
```json
{

    "TortoiseSVN.tortoiseSVNProcExePath": "D:\\java\\svn\\bin\\TortoiseProc.exe",
    "editor.minimap.showSlider": "always",
    // 控制文件和目录在资源管理器中的排列方式。
    ///filesFirst - Sort files before folders
    //mixed - Sort files and folders without separation
    //modified - Sort by last modified time
    //type - Sort by file type
    "explorer.sortOrder": "modified",

    // 设置搜索忽略的文件夹
    "search.exclude": {
        "**/kuwanh5": true
    },
    // beautiful 设置
    "beautify.config": {
        // "newline_between_rules": true,
        "space_around_combinator": true
    },
    //当前参考线的颜色设置
    "indenticator.color.dark": "#ff6700",
    // 是否开启默认缩进辅助线
    "editor.renderIndentGuides": true,
    // 是否显示空格
    "editor.renderWhitespace": "none",
    //禁止 css 和 scss 的默认校验规则， 启用
    "css.validate": false,
    "scss.validate": false,
    // "stylelint.config": {
    //     "extends": "C:\\Users\\Administrator\\AppData\\Roaming\\npm\\node_modules\\stylelint-config-standard"
    // },
    //允许在任何文件中设置断点
    "debug.allowBreakpointsEverywhere": true,
    //允许内联显示调试信息
    "debug.inlineValues": true,
    //设置默认字体大小
    "editor.fontSize": 16,
    //迷你菜单是否开启
    "editor.minimap.enabled": true,
    //设置Beautify插件自执行[保存自动格式化]
    //"editor.formatOnSave": true,
    "editor.tabCompletion": true,
    //控制代码片段提示的位置
    "editor.snippetSuggestions": "top",
    //控制换行方式
    "editor.wordWrap": "on",
    //插件自动更新
    "extensions.autoUpdate": true,
    //自动保存
    "files.autoSave": "afterDelay",
    //修改fileheader模板
    "fileheader.tpl": "/*\\r\\n *-------------------------------------------------------------\r\n * @File  : Describe the file  \r\n * @Author: {author} \r\n * @Email : qinyuanqiuse@gmail.com \r\n * @GitHub: qinyuanqiblog.github.io \r\n * @Date  : {createTime} \r\n * @Last Modified by:   {lastModifiedBy} \r\n * @Last Modified time: {updateTime} \r\n *-------------------------------------------------------------\r\n */\r\n",
    //fileheader插件相关配置
    "fileheader.Author": "QinYuanqi",
    "fileheader.LastModifiedBy": "QinYuanqi",
    //是否使用git
    "git.enabled": false,
    //设置外部终端路径
    "terminal.external.windowsExec": "C:\\Program Files\\Git\\bin\\bash.exe",
    //设置内部终端
    // "terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe",
    "terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe",
    //设置新打开窗口的大小
    "window.newWindowDimensions": "maximized",
    //工作区主题
    "workbench.colorTheme": "Monokai Extended",
    //侧栏主题
    "workbench.iconTheme": "vscode-icons",
    //侧栏位置
    "workbench.sideBar.location": "right",
    "workbench.editor.closeOnFileDelete": false,
    //工作区的一些个性化设置
    "workbench.colorCustomizations": {
        "editorCursor.foreground": "#ff0000",
        "tab.activeBackground": "#666",
        //"editor.lineHighlightBackground": "#999",
        // "activityBar.foreground": "#ff0000",
        //设置git status状态的颜色
        // "activityBarBadge.background": "#f60",
        // "activityBar.background": "#fff",

        // "editorLineNumber.foreground": "#ff6803",
        // "editorLineNumber.foreground": "#b12457",
        "statusBar.background": "#0373ff"

    },
    // 基于活动编辑器控制窗口标题。基于上下文替换变量:
    // ${activeEditorShort}: 例如 myFile.txt
    // ${activeEditorMedium}: 例如 myFolder/myFile.txt
    // ${activeEditorLong}:  例如 /Users/Development/myProject/myFile.txt
    // ${rootName}: 例如 myProject
    // ${rootPath}: 例如 /Users/Development/myProject
    // ${appName}: 例如 VS Code
    // ${dirty}: 一个更新指示器，指示活动编辑器是否更新
    // ${separator}: 一个条件分隔符("-")，仅在左右是具有值的变量时才显示
    "window.title": "${appName}${separator}${rootName}${separator}${activeEditorShort}${dirty}",
    "window.zoomLevel": 1,
    //同步vscode 相关设置
    "sync.gist": "",
    "sync.lastUpload": "2017-04-21T00:21:03.285Z",
    "sync.version": 262,
    "sync.lastDownload": "",
    "sync.autoDownload": false,
    "sync.autoUpload": false,
    "sync.showSummary": true,
    "sync.forceDownload": false,
    "sync.anonymousGist": false,
    "sync.host": "",
    "sync.pathPrefix": "",
    //Csscomb 自定义规则校验
    "csscomb.preset": {
        "exclude": [
            ".git/**",
            "node_modules/**",
            "bower_components/**"
        ],
        // Whether to add a semicolon after the last value/mixin.
        "always-semicolon": true,
        // Set indent for code inside blocks, including media queries and nested rules.
        "block-indent": "    ",
        // Unify case of hexadecimal colors.
        "color-case": "lower",
        // Whether to expand hexadecimal colors or use shorthands.
        "color-shorthand": true,
        // Unify case of element selectors.
        "element-case": "lower",
        // Add/remove line break at EOF.
        "eof-newline": true,
        // Add/remove leading zero in dimensions.
        "leading-zero": false,
        // Unify quotes style.
        "quotes": "single",
        // Remove all rulesets that contain nothing but spaces.
        "remove-empty-rulesets": true,
        // Set space after `:` in declarations.
        "space-after-colon": " ",
        // Set space after combinator (for example, in selectors like `p > a`).
        "space-after-combinator": " ",
        // Set space after `{`.
        "space-after-opening-brace": "\n",
        // Set space after selector delimiter.
        "space-after-selector-delimiter": "\n",
        // Set space before `}`.
        "space-before-closing-brace": "\n",
        // Set space before `:` in declarations.
        "space-before-colon": "",
        // Set space before combinator (for example, in selectors like `p > a`).
        "space-before-combinator": " ",
        // Set space before `{`.
        "space-before-opening-brace": " ",
        // Set space before selector delimiter.
        "space-before-selector-delimiter": "",
        // Set space between declarations (i.e. `color: tomato`).
        "space-between-declarations": "\n",
        // Whether to trim trailing spaces.
        "strip-spaces": true,
        // Whether to remove units in zero-valued dimensions.
        "unitless-zero": true,
        // Whether to align prefixes in properties and values.
        "vendor-prefix-align": true,
        // Sort properties in particular order.
        "sort-order": [
            // 参考腾讯的规范
            [
                "display",
                "visibility",
                "float",
                "clear",
                "overflow",
                "overflow-x",
                "overflow-y",
                "clip",
                "zoom"
            ],
            [
                "position",
                "top",
                "right",
                "bottom",
                "left",
                "z-index"
            ],
            [
                "table-layout",
                "empty-cells",
                "caption-side",
                "border-spacing",
                "border-collapse",
                "list-style",
                "list-style-position",
                "list-style-type",
                "list-style-image"
            ],
            [
                "-webkit-box-orient",
                "-webkit-box-direction",
                "-webkit-box-decoration-break",
                "-webkit-box-pack",
                "-webkit-box-align",
                "-webkit-box-flex"
            ],
            [
                "margin",
                "margin-top",
                "margin-right",
                "margin-bottom",
                "margin-left",
                "-webkit-box-sizing",
                "-moz-box-sizing",
                "box-sizing",
                "border",
                "border-width",
                "border-style",
                "border-color",
                "border-top",
                "border-top-width",
                "border-top-style",
                "border-top-color",
                "border-right",
                "border-right-width",
                "border-right-style",
                "border-right-color",
                "border-bottom",
                "border-bottom-width",
                "border-bottom-style",
                "border-bottom-color",
                "border-left",
                "border-left-width",
                "border-left-style",
                "border-left-color",
                "-webkit-border-radius",
                "-moz-border-radius",
                "border-radius",
                "-webkit-border-top-left-radius",
                "-moz-border-radius-topleft",
                "border-top-left-radius",
                "-webkit-border-top-right-radius",
                "-moz-border-radius-topright",
                "border-top-right-radius",
                "-webkit-border-bottom-right-radius",
                "-moz-border-radius-bottomright",
                "border-bottom-right-radius",
                "-webkit-border-bottom-left-radius",
                "-moz-border-radius-bottomleft",
                "border-bottom-left-radius",
                "-webkit-border-image",
                "-moz-border-image",
                "-o-border-image",
                "border-image",
                "-webkit-border-image-source",
                "-moz-border-image-source",
                "-o-border-image-source",
                "border-image-source",
                "-webkit-border-image-slice",
                "-moz-border-image-slice",
                "-o-border-image-slice",
                "border-image-slice",
                "-webkit-border-image-width",
                "-moz-border-image-width",
                "-o-border-image-width",
                "border-image-width",
                "-webkit-border-image-outset",
                "-moz-border-image-outset",
                "-o-border-image-outset",
                "border-image-outset",
                "-webkit-border-image-repeat",
                "-moz-border-image-repeat",
                "-o-border-image-repeat",
                "border-image-repeat",
                "padding",
                "padding-top",
                "padding-right",
                "padding-bottom",
                "padding-left",
                "width",
                "min-width",
                "max-width",
                "height",
                "min-height",
                "max-height"
            ],
            [
                "font",
                "font-family",
                "font-size",
                "font-weight",
                "font-style",
                "font-variant",
                "font-size-adjust",
                "font-stretch",
                "font-effect",
                "font-emphasize",
                "font-emphasize-position",
                "font-emphasize-style",
                "font-smooth",
                "line-height",
                "text-align",
                "-webkit-text-align-last",
                "-moz-text-align-last",
                "-ms-text-align-last",
                "text-align-last",
                "vertical-align",
                "white-space",
                "text-decoration",
                "text-emphasis",
                "text-emphasis-color",
                "text-emphasis-style",
                "text-emphasis-position",
                "text-indent",
                "-ms-text-justify",
                "text-justify",
                "letter-spacing",
                "word-spacing",
                "-ms-writing-mode",
                "text-outline",
                "text-transform",
                "text-wrap",
                "-ms-text-overflow",
                "text-overflow",
                "text-overflow-ellipsis",
                "text-overflow-mode",
                "-ms-word-wrap",
                "word-wrap",
                "-ms-word-break",
                "word-break"
            ],
            [
                "color",
                "background",
                "filter:progid:DXImageTransform.Microsoft.AlphaImageLoader",
                "background-color",
                "background-image",
                "background-repeat",
                "background-attachment",
                "background-position",
                "-ms-background-position-x",
                "background-position-x",
                "-ms-background-position-y",
                "background-position-y",
                "-webkit-background-clip",
                "-moz-background-clip",
                "background-clip",
                "background-origin",
                "-webkit-background-size",
                "-moz-background-size",
                "-o-background-size",
                "background-size"
            ],
            [
                "outline",
                "outline-width",
                "outline-style",
                "outline-color",
                "outline-offset",
                "opacity",
                "filter:progid:DXImageTransform.Microsoft.Alpha(Opacity",
                "-ms-filter:\\'progid:DXImageTransform.Microsoft.Alpha",
                "-ms-interpolation-mode",
                "-webkit-box-shadow",
                "-moz-box-shadow",
                "box-shadow",
                "filter:progid:DXImageTransform.Microsoft.gradient",
                "-ms-filter:\\'progid:DXImageTransform.Microsoft.gradient",
                "text-shadow"
            ],
            [
                "-webkit-transition",
                "-moz-transition",
                "-ms-transition",
                "-o-transition",
                "transition",
                "-webkit-transition-delay",
                "-moz-transition-delay",
                "-ms-transition-delay",
                "-o-transition-delay",
                "transition-delay",
                "-webkit-transition-timing-function",
                "-moz-transition-timing-function",
                "-ms-transition-timing-function",
                "-o-transition-timing-function",
                "transition-timing-function",
                "-webkit-transition-duration",
                "-moz-transition-duration",
                "-ms-transition-duration",
                "-o-transition-duration",
                "transition-duration",
                "-webkit-transition-property",
                "-moz-transition-property",
                "-ms-transition-property",
                "-o-transition-property",
                "transition-property",
                "-webkit-transform",
                "-moz-transform",
                "-ms-transform",
                "-o-transform",
                "transform",
                "-webkit-transform-origin",
                "-moz-transform-origin",
                "-ms-transform-origin",
                "-o-transform-origin",
                "transform-origin",
                "-webkit-animation",
                "-moz-animation",
                "-ms-animation",
                "-o-animation",
                "animation",
                "-webkit-animation-name",
                "-moz-animation-name",
                "-ms-animation-name",
                "-o-animation-name",
                "animation-name",
                "-webkit-animation-duration",
                "-moz-animation-duration",
                "-ms-animation-duration",
                "-o-animation-duration",
                "animation-duration",
                "-webkit-animation-play-state",
                "-moz-animation-play-state",
                "-ms-animation-play-state",
                "-o-animation-play-state",
                "animation-play-state",
                "-webkit-animation-timing-function",
                "-moz-animation-timing-function",
                "-ms-animation-timing-function",
                "-o-animation-timing-function",
                "animation-timing-function",
                "-webkit-animation-delay",
                "-moz-animation-delay",
                "-ms-animation-delay",
                "-o-animation-delay",
                "animation-delay",
                "-webkit-animation-iteration-count",
                "-moz-animation-iteration-count",
                "-ms-animation-iteration-count",
                "-o-animation-iteration-count",
                "animation-iteration-count",
                "-webkit-animation-direction",
                "-moz-animation-direction",
                "-ms-animation-direction",
                "-o-animation-direction",
                "animation-direction"
            ],
            [
                "content",
                "quotes",
                "counter-reset",
                "counter-increment",
                "resize",
                "cursor",
                "-webkit-user-select",
                "-moz-user-select",
                "-ms-user-select",
                "user-select",
                "nav-index",
                "nav-up",
                "nav-right",
                "nav-down",
                "nav-left",
                "-moz-tab-size",
                "-o-tab-size",
                "tab-size",
                "-webkit-hyphens",
                "-moz-hyphens",
                "hyphens",
                "pointer-events"
            ]
        ]
    },
    "git.confirmSync": false,
    "workbench.startupEditor": "newUntitledFile",
    "vsicons.dontShowNewVersionMessage": true
}
```

<!-- 20171110个人设置 -->
```json
{
    "workbench.commandPalette.history": 100000,
    "workbench.editor.labelFormat": "medium",
    "background.enabled": false,
    // "background.style":{
    //     "opacity":0.3,
    //     // "background-position": "top right",
    //     "background-size": "100% 100%"
    // },
    // "background.useDefault": false,
    // "background.customImages": ["https://ss0.bdstatic.com/94oJfD_bAAcT8t7mm9GUKT-xh_/timg?image&quality=100&size=b4000_4000&sec=1505442527&di=d39f50e0d416f243df5c44515777c1b3&src=http://5b0988e595225.cdn.sohucs.com/q_mini,c_zoom,w_640/images/20170724/66eb531fe66943ad9f5bd1804fa00e5d.jpeg"],
    // "background.customImages": ["file:///D:/company/workspace/html/466661.jpg"
    // ],
    // "background.customImages": ["file:///C:/Users/Administrator/Desktop/KkBwdjblbjmlhgt.jpg"
    // ],

    "TortoiseSVN.tortoiseSVNProcExePath": "D:\\java\\svn\\bin\\TortoiseProc.exe",
    "editor.minimap.showSlider": "always",
    // 控制文件和目录在资源管理器中的排列方式。
    ///filesFirst - Sort files before folders
    //mixed - Sort files and folders without separation
    //modified - Sort by last modified time
    //type - Sort by file type
    "explorer.sortOrder": "modified",
    // 设置搜索忽略的文件夹
    "search.exclude": {
        "**/kuwanh5": true
    },
    // beautiful 设置
    "beautify.config": {
        // "newline_between_rules": true,
        "space_around_combinator": true
    },
    //当前参考线的颜色设置
    "indenticator.color.dark": "#ff6700",
    // 是否开启默认缩进辅助线
    "editor.renderIndentGuides": true,
    // 是否显示空格
    "editor.renderWhitespace": "none",
    //禁止 css 和 scss 的默认校验规则， 启用
    "css.validate": false,
    "scss.validate": false,
    // "stylelint.config": {
    //     "extends": "C:\\Users\\Administrator\\AppData\\Roaming\\npm\\node_modules\\stylelint-config-standard"
    // },
    //允许在任何文件中设置断点
    "debug.allowBreakpointsEverywhere": true,
    //允许内联显示调试信息
    "debug.inlineValues": true,
    //设置默认字体大小
    "editor.fontSize": 16,
    //迷你菜单是否开启
    "editor.minimap.enabled": true,
    //设置Beautify插件自执行[保存自动格式化]
    //"editor.formatOnSave": true,
    "editor.tabCompletion": true,
    //控制代码片段提示的位置
    "editor.snippetSuggestions": "top",
    //控制换行方式
    "editor.wordWrap": "on",
    //插件自动更新
    "extensions.autoUpdate": true,
    //自动保存
    "files.autoSave": "afterDelay",
    //修改fileheader模板
    "fileheader.tpl": "/*\\r\\n *-------------------------------------------------------------\r\n * @File  : Describe the file  \r\n * @Author: {author} \r\n * @Email : qinyuanqiuse@gmail.com \r\n * @GitHub: qinyuanqiblog.github.io \r\n * @Date  : {createTime} \r\n * @Last Modified by:   {lastModifiedBy} \r\n * @Last Modified time: {updateTime} \r\n *-------------------------------------------------------------\r\n */\r\n",
    //fileheader插件相关配置
    "fileheader.Author": "QinYuanqi",
    "fileheader.LastModifiedBy": "QinYuanqi",
    //是否使用git
    "git.enabled": false,
    //设置外部终端路径
    "terminal.external.windowsExec": "C:\\Program Files\\Git\\bin\\bash.exe",
    //设置内部终端
    // "terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe",
    "terminal.integrated.shell.windows": "C:\\Program Files\\Git\\bin\\bash.exe",
    //设置新打开窗口的大小
    "window.newWindowDimensions": "maximized",
    //工作区主题
    "workbench.colorTheme": "Monokai Extended",
    //侧栏主题
    "workbench.iconTheme": "vscode-icons",
    //侧栏位置
    "workbench.sideBar.location": "right",
    "workbench.editor.closeOnFileDelete": false,
    //工作区的一些个性化设置
    "workbench.colorCustomizations": {
        "editorCursor.foreground": "#ff0000",
        "tab.activeBackground": "#666",
        //"editor.lineHighlightBackground": "#999",
        // "activityBar.foreground": "#ff0000",
        //设置git status状态的颜色
        // "activityBarBadge.background": "#f60",
        // "activityBar.background": "#fff",
        // "editorLineNumber.foreground": "#ff6803",
        // "editorLineNumber.foreground": "#b12457",
        "statusBar.background": "#0373ff"
    },
    // 基于活动编辑器控制窗口标题。基于上下文替换变量:
    // ${activeEditorShort}: 例如 myFile.txt
    // ${activeEditorMedium}: 例如 myFolder/myFile.txt
    // ${activeEditorLong}:  例如 /Users/Development/myProject/myFile.txt
    // ${rootName}: 例如 myProject
    // ${rootPath}: 例如 /Users/Development/myProject
    // ${appName}: 例如 VS Code
    // ${dirty}: 一个更新指示器，指示活动编辑器是否更新
    // ${separator}: 一个条件分隔符("-")，仅在左右是具有值的变量时才显示
    "window.title": "${appName}${separator}${rootName}${separator}${activeEditorShort}${dirty}",
    "window.zoomLevel": 1,
    //同步vscode 相关设置
    "sync.gist": "",
    "sync.lastUpload": "2017-04-21T00:21:03.285Z",
    "sync.version": 262,
    "sync.lastDownload": "",
    "sync.autoDownload": false,
    "sync.autoUpload": false,
    "sync.showSummary": true,
    "sync.forceDownload": false,
    "sync.anonymousGist": false,
    "sync.host": "",
    "sync.pathPrefix": "",
    //Csscomb 自定义规则校验
    "csscomb.preset": {
        "exclude": [
            ".git/**",
            "node_modules/**",
            "bower_components/**"
        ],
        // Whether to add a semicolon after the last value/mixin.
        "always-semicolon": true,
        // Set indent for code inside blocks, including media queries and nested rules.
        "block-indent": "    ",
        // Unify case of hexadecimal colors.
        "color-case": "lower",
        // Whether to expand hexadecimal colors or use shorthands.
        "color-shorthand": true,
        // Unify case of element selectors.
        "element-case": "lower",
        // Add/remove line break at EOF.
        "eof-newline": true,
        // Add/remove leading zero in dimensions.
        "leading-zero": false,
        // Unify quotes style.
        "quotes": "single",
        // Remove all rulesets that contain nothing but spaces.
        "remove-empty-rulesets": true,
        // Set space after `:` in declarations.
        "space-after-colon": " ",
        // Set space after combinator (for example, in selectors like `p > a`).
        "space-after-combinator": " ",
        // Set space after `{`.
        "space-after-opening-brace": "\n",
        // Set space after selector delimiter.
        "space-after-selector-delimiter": "\n",
        // Set space before `}`.
        "space-before-closing-brace": "\n",
        // Set space before `:` in declarations.
        "space-before-colon": "",
        // Set space before combinator (for example, in selectors like `p > a`).
        "space-before-combinator": " ",
        // Set space before `{`.
        "space-before-opening-brace": " ",
        // Set space before selector delimiter.
        "space-before-selector-delimiter": "",
        // Set space between declarations (i.e. `color: tomato`).
        "space-between-declarations": "\n",
        // Whether to trim trailing spaces.
        "strip-spaces": true,
        // Whether to remove units in zero-valued dimensions.
        "unitless-zero": true,
        // Whether to align prefixes in properties and values.
        "vendor-prefix-align": true,
        // Sort properties in particular order.
        "sort-order": [
            // 参考腾讯的规范
            [
                "display",
                "visibility",
                "float",
                "clear",
                "overflow",
                "overflow-x",
                "overflow-y",
                "clip",
                "zoom"
            ],
            [
                "position",
                "top",
                "right",
                "bottom",
                "left",
                "z-index"
            ],
            [
                "table-layout",
                "empty-cells",
                "caption-side",
                "border-spacing",
                "border-collapse",
                "list-style",
                "list-style-position",
                "list-style-type",
                "list-style-image"
            ],
            [
                "-webkit-box-orient",
                "-webkit-box-direction",
                "-webkit-box-decoration-break",
                "-webkit-box-pack",
                "-webkit-box-align",
                "-webkit-box-flex"
            ],
            [
                "margin",
                "margin-top",
                "margin-right",
                "margin-bottom",
                "margin-left",
                "-webkit-box-sizing",
                "-moz-box-sizing",
                "box-sizing",
                "border",
                "border-width",
                "border-style",
                "border-color",
                "border-top",
                "border-top-width",
                "border-top-style",
                "border-top-color",
                "border-right",
                "border-right-width",
                "border-right-style",
                "border-right-color",
                "border-bottom",
                "border-bottom-width",
                "border-bottom-style",
                "border-bottom-color",
                "border-left",
                "border-left-width",
                "border-left-style",
                "border-left-color",
                "-webkit-border-radius",
                "-moz-border-radius",
                "border-radius",
                "-webkit-border-top-left-radius",
                "-moz-border-radius-topleft",
                "border-top-left-radius",
                "-webkit-border-top-right-radius",
                "-moz-border-radius-topright",
                "border-top-right-radius",
                "-webkit-border-bottom-right-radius",
                "-moz-border-radius-bottomright",
                "border-bottom-right-radius",
                "-webkit-border-bottom-left-radius",
                "-moz-border-radius-bottomleft",
                "border-bottom-left-radius",
                "-webkit-border-image",
                "-moz-border-image",
                "-o-border-image",
                "border-image",
                "-webkit-border-image-source",
                "-moz-border-image-source",
                "-o-border-image-source",
                "border-image-source",
                "-webkit-border-image-slice",
                "-moz-border-image-slice",
                "-o-border-image-slice",
                "border-image-slice",
                "-webkit-border-image-width",
                "-moz-border-image-width",
                "-o-border-image-width",
                "border-image-width",
                "-webkit-border-image-outset",
                "-moz-border-image-outset",
                "-o-border-image-outset",
                "border-image-outset",
                "-webkit-border-image-repeat",
                "-moz-border-image-repeat",
                "-o-border-image-repeat",
                "border-image-repeat",
                "padding",
                "padding-top",
                "padding-right",
                "padding-bottom",
                "padding-left",
                "width",
                "min-width",
                "max-width",
                "height",
                "min-height",
                "max-height"
            ],
            [
                "font",
                "font-family",
                "font-size",
                "font-weight",
                "font-style",
                "font-variant",
                "font-size-adjust",
                "font-stretch",
                "font-effect",
                "font-emphasize",
                "font-emphasize-position",
                "font-emphasize-style",
                "font-smooth",
                "line-height",
                "text-align",
                "-webkit-text-align-last",
                "-moz-text-align-last",
                "-ms-text-align-last",
                "text-align-last",
                "vertical-align",
                "white-space",
                "text-decoration",
                "text-emphasis",
                "text-emphasis-color",
                "text-emphasis-style",
                "text-emphasis-position",
                "text-indent",
                "-ms-text-justify",
                "text-justify",
                "letter-spacing",
                "word-spacing",
                "-ms-writing-mode",
                "text-outline",
                "text-transform",
                "text-wrap",
                "-ms-text-overflow",
                "text-overflow",
                "text-overflow-ellipsis",
                "text-overflow-mode",
                "-ms-word-wrap",
                "word-wrap",
                "-ms-word-break",
                "word-break"
            ],
            [
                "color",
                "background",
                "filter:progid:DXImageTransform.Microsoft.AlphaImageLoader",
                "background-color",
                "background-image",
                "background-repeat",
                "background-attachment",
                "background-position",
                "-ms-background-position-x",
                "background-position-x",
                "-ms-background-position-y",
                "background-position-y",
                "-webkit-background-clip",
                "-moz-background-clip",
                "background-clip",
                "background-origin",
                "-webkit-background-size",
                "-moz-background-size",
                "-o-background-size",
                "background-size"
            ],
            [
                "outline",
                "outline-width",
                "outline-style",
                "outline-color",
                "outline-offset",
                "opacity",
                "filter:progid:DXImageTransform.Microsoft.Alpha(Opacity",
                "-ms-filter:\\'progid:DXImageTransform.Microsoft.Alpha",
                "-ms-interpolation-mode",
                "-webkit-box-shadow",
                "-moz-box-shadow",
                "box-shadow",
                "filter:progid:DXImageTransform.Microsoft.gradient",
                "-ms-filter:\\'progid:DXImageTransform.Microsoft.gradient",
                "text-shadow"
            ],
            [
                "-webkit-transition",
                "-moz-transition",
                "-ms-transition",
                "-o-transition",
                "transition",
                "-webkit-transition-delay",
                "-moz-transition-delay",
                "-ms-transition-delay",
                "-o-transition-delay",
                "transition-delay",
                "-webkit-transition-timing-function",
                "-moz-transition-timing-function",
                "-ms-transition-timing-function",
                "-o-transition-timing-function",
                "transition-timing-function",
                "-webkit-transition-duration",
                "-moz-transition-duration",
                "-ms-transition-duration",
                "-o-transition-duration",
                "transition-duration",
                "-webkit-transition-property",
                "-moz-transition-property",
                "-ms-transition-property",
                "-o-transition-property",
                "transition-property",
                "-webkit-transform",
                "-moz-transform",
                "-ms-transform",
                "-o-transform",
                "transform",
                "-webkit-transform-origin",
                "-moz-transform-origin",
                "-ms-transform-origin",
                "-o-transform-origin",
                "transform-origin",
                "-webkit-animation",
                "-moz-animation",
                "-ms-animation",
                "-o-animation",
                "animation",
                "-webkit-animation-name",
                "-moz-animation-name",
                "-ms-animation-name",
                "-o-animation-name",
                "animation-name",
                "-webkit-animation-duration",
                "-moz-animation-duration",
                "-ms-animation-duration",
                "-o-animation-duration",
                "animation-duration",
                "-webkit-animation-play-state",
                "-moz-animation-play-state",
                "-ms-animation-play-state",
                "-o-animation-play-state",
                "animation-play-state",
                "-webkit-animation-timing-function",
                "-moz-animation-timing-function",
                "-ms-animation-timing-function",
                "-o-animation-timing-function",
                "animation-timing-function",
                "-webkit-animation-delay",
                "-moz-animation-delay",
                "-ms-animation-delay",
                "-o-animation-delay",
                "animation-delay",
                "-webkit-animation-iteration-count",
                "-moz-animation-iteration-count",
                "-ms-animation-iteration-count",
                "-o-animation-iteration-count",
                "animation-iteration-count",
                "-webkit-animation-direction",
                "-moz-animation-direction",
                "-ms-animation-direction",
                "-o-animation-direction",
                "animation-direction"
            ],
            [
                "content",
                "quotes",
                "counter-reset",
                "counter-increment",
                "resize",
                "cursor",
                "-webkit-user-select",
                "-moz-user-select",
                "-ms-user-select",
                "user-select",
                "nav-index",
                "nav-up",
                "nav-right",
                "nav-down",
                "nav-left",
                "-moz-tab-size",
                "-o-tab-size",
                "tab-size",
                "-webkit-hyphens",
                "-moz-hyphens",
                "hyphens",
                "pointer-events"
            ]
        ]
    },
    "git.confirmSync": false,
    "workbench.startupEditor": "newUntitledFile",
    "vsicons.dontShowNewVersionMessage": true,
    "guides.enabled": false,
    "sublimeTextKeymap.promptV3Features": true,
    "workbench.panel.location": "bottom"
}

```