# CSS 基础学习

## 默认设置

基础的配置项 可用于重置 HTML 元素的浏览器默认设置

```css
@charset "utf-8";
* {
    width: auto;
    height: auto;
    margin: 0;
    padding: 0;
    border: none;
    background-color: transparent;
    -webkit-tap-highlight-color: transparent;
    font-family: "Microsoft YaHei", "微软雅黑", Heiti, "黑体", Arial, Helvetica, STHeiTi, sans-serif;

    -moz-box-sizing: inherit;
    -webkit-box-sizing: inherit;
    box-sizing: inherit;
}
html { -webkit-text-size-adjust: none; overflow-y: scroll; }
a { text-decoration: none; }
img { max-width: 100%; }
h1,h2,h3,h4,h5,h6 { font-size: 100%; font-weight: 500; }
li,ol,ul { list-style: none; }
em,i { font-style: normal; }
del { text-decoration: line-through; }
input,select,textarea { font-size: 100%; vertical-align: middle; }
input,button,select,textarea { outline: 0; }
input { width: 100%; border: 0 none; }
textarea { resize: none; }
table { border-collapse: collapse; border-spacing: 0; }
caption,th { text-align: left; }
address,caption,cite,code,dfn,em,th,var { font-style: normal; font-weight: 500; }
html, body { font-size: 14px; }
```

## 文字换行断句
```css
/*
允许对长的不可分割的单词进行分割并换行到下一行。
属性允许您允许文本强制文本进行换行-即使这意味着会对单词进行拆分 */
.word_wrap {
    /* 只在允许的断字点换行(浏览器保持默认处理) */
    word-wrap: normal;

    /* 在长单词或URL地址内容进行换行 */
    word-wrap: break-word;
}

/*
规定非中日韩文本的换行规则
在恰当的断字点进行换行  word-break 属性规定自动换行的处理方法 */
.word_break {
    /* 使用浏览器默认的换行规则 */
    word-break: normal;

    /* 允许在单词内换行 */
    word-break: break-all;

    /* 只能在半角空格或连字符处换行 */
    word-break: keep-all;
}

/*
属性规定当文本溢出包含元素时发生的事情
一般这个属性要和 overflow:hidden; white-space: nowrap; 搭配使用 */
.text_overflow {
    /* 修剪文本 */
    text-overflow: clip;

    /* 显示省略符号来代表被修剪的文本 */
    text-overflow: ellipsis;

    /* 使用给定的字符串来代表被修剪的文本 */
    text-overflow: "string";

    /* 继承父级(默认不进行处理) */
    text-overflow: inherit;
}

/*
属性设置如何处理元素内的空白
这个属性声明建立布局过程中如何处理元素中的空白符
值 pre-wrap 和 pre-line 是 CSS 2.1 中新增的 */
.white_space {
    /* 默认 - 空白会被浏览器忽略 */
    white-space: normal;

    /* 空白会被浏览器保留 - 其行为方式类似 HTML 中的 <pre> 标签 */
    white-space: pre;

    /* 文本不会换行 - 文本会在在同一行上继续 - 直到遇到 <br> 标签为止 */
    white-space: nowrap;

    /* 保留空白符序列 - 但是正常地进行换行 */
    white-space: pre-wrap;

    /* 合并空白符序列 - 但是保留换行符 */
    white-space: pre-line;

    /* 规定应该从父元素继承 white-space 属性的值 */
    white-space: inherit;
}
```
### 文本文字显示几行, 多余部分使用省略号忽略
```css
text-overflow: ellipsis;
display: -webkit-box;
-webkit-line-clamp: 2;
-webkit-box-orient: vertical;
```

* [css的line-clamp属性是什么？如何使用？](http://www.php.cn/css-tutorial-412556.html)
* [对于无法支持的浏览器，我们可以使用JavaScript来实现效果。JavaScript代码，Clamp.js的下载地址点击即可跳转查看](https://github.com/josephschmitt/Clamp.js)

## 字体阴影

格式:
```
text-shadow: h-shadow v-shadow blur color;
```

参数含义:

值 | 描述
--- | ---
h-shadow | 必需 - 水平阴影的位置 - 允许负值
v-shadow | 必需 - 垂直阴影的位置 - 允许负值
blur | 可选 - 模糊距离
color | 可选 - 阴影的颜色

```css
.text_shadow {
    text-shadow: 5px 5px 5px #FF0000;
}
```

## 盒子阴影

格式:
```
box-shadow: h-shadow v-shadow blur spread color inset;
```

参数含义:

值 | 描述
--- | ---
h-shadow | 必需 - 水平阴影的位置 - 允许负值
v-shadow | 必需 - 垂直阴影的位置 - 允许负值
blur | 可选 - 模糊距离
spread | 可选 - 阴影的尺寸
color | 可选 - 阴影的颜色
inset | 可选 - 将外部阴影 (outset) 改为内部阴影

```css
/* 正常阴影 */
.box_shadow {
    -moz-box-shadow: 0 0 4px #888;
    box-shadow: 0 0 4px #888;
}

/* 内部阴影 + inset */
.box_shadow {
    -moz-box-shadow: 0 0 4px #888 inset;
    box-shadow: 0 0 4px #888 inset;
}
```


## 透明度
```css
/* 完全透明 */
.opacity-0 {
    filter: alpha(opacity=0);
    -moz-opacity: 0;
    opacity: 0;
}
/* 50%透明 */
.opacity-50 {
    filter: alpha(opacity=50);
    -moz-opacity: .5;
    opacity: .5;
}
/* 不透明 */
.opacity-100 {
    filter: alpha(opacity=100);
    -moz-opacity: 1;
    opacity: 1;
}
```


## 盒子各区域的定义选择

使盒子可以允许以特定的方式定义匹配某个区域的特定元素

```css
/*
为元素设定的宽度和高度决定了元素的边框盒
就是说，为元素指定的任何内边距和边框都将在已设定的宽度和高度内进行绘制
通过从已设定的宽度和高度分别减去边框和内边距才能得到内容的宽度和高度 */
.box_sizing_borderbox {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
}

/*
这是由 CSS2.1 规定的宽度高度行为
宽度和高度分别应用到元素的内容框
在宽度和高度之外绘制元素的内边距和边框 */
.box_sizing_contentbox {
    -webkit-box-sizing: content-box;
    -moz-box-sizing: content-box;
    box-sizing: content-box;
}

/* 规定应从父元素继承 box-sizing 属性的值 */
.box_sizing_inherit {
    -webkit-box-sizing: inherit;
    -moz-box-sizing: inherit;
    box-sizing: inherit;
}
```


## 溢出处理

可以对盒子的溢出内容进行处理

```css
/* 默认值。内容不会被修剪，会呈现在元素框之外。 */
.overflow_style_visible { overflow: visible; }

/* 内容会被修剪，并且其余内容是不可见的。 */
.overflow_style_hidden { overflow: hidden; }

/* 内容会被修剪，但是浏览器会显示滚动条以便查看其余的内容。 */
.overflow_style_scroll { overflow: scroll; }

/* 如果内容被修剪，则浏览器会显示滚动条以便查看其余的内容。 */
.overflow_style_auto { overflow: auto; }

/* 规定应该从父元素继承 overflow 属性的值。 */
.overflow_style_inherit { overflow: inherit; }
```

**PS:**

给盒子使用 `overflow: hidden;` 样式后, 盒子内部下一级的 `float: left;` 可以不需要进行清除浮动


## 盒子外轮廓 在边框外面的边框
```css
/* outline 轮廓 是绘制于元素周围的一条线, 位于边框边缘的外围, 可起到突出元素的作用 */
.outline_red_solid { outline: 1px solid red; }
```

**学习链接:**
* [w3school](http://www.w3school.com.cn/cssref/pr_outline.asp)


## 盒子圆角框
```css
.border_radius {
    -webkit-border-radius: 3px;
    -moz-border-radius: 3px;
    border-radius: 3px;
}
```


## 用户是否可选择
```css
.user_select_none {
    -webkit-user-select: none;
    -moz-user-select: none;
    -ms-user-select: none;
    user-select: none;
}
.user_select_text {
    -webkit-user-select: text;
    -moz-user-select: text;
    -ms-user-select: text;
    user-select: text;
}
.user_select_all {
    -webkit-user-select: all;
    -moz-user-select: all;
    -ms-user-select: all;
    user-select: all;
}
.user_select_element {
    -webkit-user-select: element;
    -moz-user-select: element;
    -ms-user-select: element;
    user-select: element;
}
```


## 鼠标样式
常用于鼠标动作 如 `:hover` 鼠标悬停
```css
/* 默认光标(通常是一个箭头) */
.mouse_style_cursor_default:hover { cursor: default; }

/* 默认浏览器设置的光标 */
.mouse_style_cursor_auto:hover { cursor: auto; }

/* 光标呈现为十字线 */
.mouse_style_cursor_crosshair:hover { cursor: crosshair; }

/* 光标呈现为指示链接的指针(一只手) */
.mouse_style_cursor_pointer:hover { cursor: pointer; }

/* 此光标指示某对象可被移动 */
.mouse_style_cursor_move:hover { cursor: move; }

/* 此光标指示矩形框的边缘可被向右(东)移动 */
.mouse_style_cursor_e-resize:hover { cursor: e-resize; }

/* 此光标指示矩形框的边缘可被向上及向右移动(北/东) */
.mouse_style_cursor_ne-resize:hover { cursor: ne-resize; }

/* 此光标指示矩形框的边缘可被向上及向左移动(北/西) */
.mouse_style_cursor_nw-resize:hover { cursor: nw-resize; }

/* 此光标指示矩形框的边缘可被向上(北)移动 */
.mouse_style_cursor_n-resize:hover { cursor: n-resize; }

/* 此光标指示矩形框的边缘可被向下及向右移动(南/东) */
.mouse_style_cursor_se-resize:hover { cursor: se-resize; }

/* 此光标指示矩形框的边缘可被向下及向左移动(南/西) */
.mouse_style_cursor_sw-resize:hover { cursor: sw-resize; }

/* 此光标指示矩形框的边缘可被向下移动(南) */
.mouse_style_cursor_s-resize:hover { cursor: s-resize; }

/* 此光标指示矩形框的边缘可被向左移动(西) */
.mouse_style_cursor_w-resize:hover { cursor: w-resize; }

/* 此光标指示文本 */
.mouse_style_cursor_text:hover { cursor: text; }

/* 此光标指示程序正忙(通常是一只表或沙漏) */
.mouse_style_cursor_wait:hover { cursor: wait; }

/* 此光标指示可用的帮助(通常是一个问号或一个气球) */
.mouse_style_cursor_help:hover { cursor: help; }
```


## 隐藏并且需要存在的盒子
```css
.HideExistBox {
    display: block !important;
    overflow: hidden !important;
    position: fixed !important;
    top: -1px !important;
    left: -1px !important;
    right: auto !important;
    bottom: auto !important;
    z-index: -999999999 !important;
    width: 1px !important;
    height: 1px !important;
    filter: alpha(opacity=0) !important;
    -moz-opacity: 0 !important;
    opacity: 0 !important;
}
```

## 锁定窗口尺寸 一般使用在 html 和 body 元素上
```css
.LockWindowSize {
    display: block !important;
    overflow: hidden !important;
    position: relative !important;
    width: 100%;
    height: auto;
}
```

## 旋转
```css
.rotate-0 {
    -webkit-transform:rotate(0deg);
    -moz-transform:rotate(0deg);
    -ms-transform:rotate(0deg);
    -o-transform:rotate(0deg);
    transform:rotate(0deg);
}
.rotate-90 {
    -webkit-transform:rotate(90deg);
    -moz-transform:rotate(90deg);
    -ms-transform:rotate(90deg);
    -o-transform:rotate(90deg);
    transform:rotate(90deg);
}
.rotate-180 {
    -webkit-transform:rotate(180deg);
    -moz-transform:rotate(180deg);
    -ms-transform:rotate(180deg);
    -o-transform:rotate(180deg);
    transform:rotate(180deg);
}
.rotate-270 {
    -webkit-transform:rotate(270deg);
    -moz-transform:rotate(270deg);
    -ms-transform:rotate(270deg);
    -o-transform:rotate(270deg);
    transform:rotate(270deg);
}
.rotate-360 {
    -webkit-transform:rotate(360deg);
    -moz-transform:rotate(360deg);
    -ms-transform:rotate(360deg);
    -o-transform:rotate(360deg);
    transform:rotate(360deg);
}
```

## 水平翻转
```css
.flipx {
    -webkit-transform:scaleX(-1);
    -moz-transform:scaleX(-1);
    -o-transform:scaleX(-1);
    transform:scaleX(-1);
    /*IE*/
    filter:FlipH;
}
/*垂直翻转*/
.flipy {
    -webkit-transform:scaleY(-1);
    -moz-transform:scaleY(-1);
    -o-transform:scaleY(-1);
    transform:scaleY(-1);
    /*IE*/
    filter:FlipV;
}
```

## 加载Gif图片
```css
.LoadingGif {
    background-image: url('https:/ytsimg.gitee.io/Blog/yts_github_io/html/icon_loading.png');
    background-size: 3em 3em;
    background-repeat: no-repeat;
    background-position: center;

    -webkit-animation: LoadingGifRotate 2s infinite linear;
    -moz-animation: LoadingGifRotate 2s infinite linear;
    -o-animation: LoadingGifRotate 2s infinite linear;
    animation: LoadingGifRotate 2s infinite linear;
}
    @-webkit-keyframes LoadingGifRotate {
        0% {
            -webkit-transform: rotate(0deg);
            -moz-transform: rotate(0deg);
            -ms-transform: rotate(0deg);
            -o-transform: rotate(0deg);
            transform: rotate(0deg);
        }
        100% {
            -webkit-transform: rotate(360deg);
            -moz-transform: rotate(360deg);
            -ms-transform: rotate(360deg);
            -o-transform: rotate(360deg);
            transform: rotate(360deg);
        }
    }
    @-moz-keyframes LoadingGifRotate {
        0% {
            -webkit-transform: rotate(0deg);
            -moz-transform: rotate(0deg);
            -ms-transform: rotate(0deg);
            -o-transform: rotate(0deg);
            transform: rotate(0deg);
        }
        100% {
            -webkit-transform: rotate(360deg);
            -moz-transform: rotate(360deg);
            -ms-transform: rotate(360deg);
            -o-transform: rotate(360deg);
            transform: rotate(360deg);
        }
    }
    @-o-keyframes LoadingGifRotate {
        0% {
            -webkit-transform: rotate(0deg);
            -moz-transform: rotate(0deg);
            -ms-transform: rotate(0deg);
            -o-transform: rotate(0deg);
            transform: rotate(0deg);
        }
        100% {
            -webkit-transform: rotate(360deg);
            -moz-transform: rotate(360deg);
            -ms-transform: rotate(360deg);
            -o-transform: rotate(360deg);
            transform: rotate(360deg);
        }
    }
    @keyframes LoadingGifRotate {
        0% {
            -webkit-transform: rotate(0deg);
            -moz-transform: rotate(0deg);
            -ms-transform: rotate(0deg);
            -o-transform: rotate(0deg);
            transform: rotate(0deg);
        }
        100% {
            -webkit-transform: rotate(360deg);
            -moz-transform: rotate(360deg);
            -ms-transform: rotate(360deg);
            -o-transform: rotate(360deg);
            transform: rotate(360deg);
        }
    }
```

## 详细信息的扩展
```css
.DetailsExpanded {}
    .DetailsExpanded .UpperLayer {
        position: relative;
        z-index: 100;
    }
    .DetailsExpanded.Show .Summary::before {
        display: block;
        position: fixed;
        top: 0;
        right: 0;
        bottom: 0;
        left: 0;
        z-index: 99;
        cursor: default;
        content: " ";
        background: transparent;
    }
```

## 悬浮固定
```css
.SuspensionFixationALLWindow {
    display: block;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;

    z-index: 0;
    cursor: default;
    background: transparent;
}
```

## 绝对定位-水平垂直居中
```css
.AbsHorizontalVerticalCenter {
    display: block;
    position: absolute;
    z-index: 1;
    top: 50%;
    left: 50%;
    -webkit-transform: translate(-50%, -50%);
    -moz-transform: translate(-50%, -50%);
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
}
```


## 响应式样式
```css
@media screen and (max-width: 320px) { html { font-size: 21.33px; } body { font-size: 9px; } }
@media screen and (min-width: 320px) { html { font-size: 21.33px; } body { font-size: 9px; } }
@media screen and (min-width: 360px) { html { font-size: 24.00px; } body { font-size: 9.50px; } }
@media screen and (min-width: 384px) { html { font-size: 25.60px; } body { font-size: 10.00px; } }
@media screen and (min-width: 400px) { html { font-size: 26.67px; } body { font-size: 11.00px; } }
@media screen and (min-width: 480px) { html { font-size: 32.00px; } body { font-size: 12.00px; } }
@media screen and (min-width: 540px) { html { font-size: 32.00px; } body { font-size: 14.00px; } }
@media screen and (min-width: 650px) { html { font-size: 32.00px; } body { font-size: 16.00px; } }
@media screen and (min-width: 750px) { html { font-size: 32.00px; } body { font-size: 16.00px; } }
@media screen and (min-width: 880px) { html { font-size: 32.00px; } body { font-size: 16.00px; } }
/* 手机端样式 */
@media screen and (max-width: 1200px) {
    .Style_IsMobile_Hide { display: none !important; }
}
/* 电脑端样式 */
@media screen and (min-width: 1200px) {
    .Style_IsPC_Hide { display: none !important; }
    .Style_IsPC_Opacity {
        filter: alpha(opacity=0) !important;
        -moz-opacity: 0 !important;
        opacity: 0 !important;
    }
}
```
