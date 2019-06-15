# CSS 重置

> Create by gintangible on **2019-06-06 10:41**
> Recently revised in **2019-06-06 16：37**

现在市场上的浏览器五花八门，各个浏览器的默认样式有些区别。所以在写项目时，有必要统一样式，减少默认样式有可能带来的问题。

目前市场的解决方式有两种方式：

* `reset.css`
* `normalize.css`

## reset.css

重置浏览器样式，减少默认样式有可能带来的问题。以下是在网上找到一份 [`reset.css`](https://www.cnblogs.com/yizuierguo/archive/2009/07/15/1524106.html#3438322), 
最好根据自己的实际项目，改造成适合自己的。

> reset.css

```
/* 清除内外边距 */
body, h1, h2, h3, h4, h5, h6, hr, p, blockquote, /* structural elements 结构元素 */
dl, dt, dd, ul, ol, li, /* list elements 列表元素 */
pre, /* text formatting elements 文本格式元素 */
fieldset, lengend, button, input, textarea, /* form elements 表单元素 */
th, td { /* table elements 表格元素 */
    margin: 0;
    padding: 0;
}

/* 设置默认字体 */
body,
button, input, select, textarea { /* for ie */
    /*font: 12px/1 Tahoma, Helvetica, Arial, "宋体", sans-serif;*/
    font: 12px/1 Tahoma, Helvetica, Arial, "\5b8b\4f53", sans-serif; /* 用 ascii 字符表示，使得在任何编码下都无问题 */
}

h1 { font-size: 18px; /* 18px / 12px = 1.5 */ }
h2 { font-size: 16px; }
h3 { font-size: 14px; }
h4, h5, h6 { font-size: 100%; }

address, cite, dfn, em, var { font-style: normal; } /* 将斜体扶正 */
code, kbd, pre, samp, tt { font-family: "Courier New", Courier, monospace; } /* 统一等宽字体 */
small { font-size: 12px; } /* 小于 12px 的中文很难阅读，让 small 正常化 */

/* 重置列表元素 */
ul, ol { list-style: none; }

/* 重置文本格式元素 */
a { text-decoration: none; }
a:hover { text-decoration: underline; }

abbr[title], acronym[title] { /* 注：1.ie6 不支持 abbr; 2.这里用了属性选择符，ie6 下无效果 */
    border-bottom: 1px dotted;
    cursor: help;
}

q:before, q:after { content: ''; }

/* 重置表单元素 */
legend { color: #000; } /* for ie6 */
fieldset, img { border: none; } /* img 搭车：让链接里的 img 无边框 */
/* 注：optgroup 无法扶正 */
button, input, select, textarea {
    font-size: 100%; /* 使得表单元素在 ie 下能继承字体大小 */
}

/* 重置表格元素 */
table {
    border-collapse: collapse;
    border-spacing: 0;
}

/* 重置 hr */
hr {
    border: none;
    height: 1px;
}

/* 让非ie浏览器默认也显示垂直滚动条，防止因滚动条引起的闪烁 */
html { overflow-y: scroll; }

//解决在chrome中自动完成表单后input出现黄色背景
button,
input[type="button"],
input[type="reset"],
input[type="submit"] {
    -webkit-appearance: none;
}

:-moz-placeholder {
    /* Mozilla Firefox 4 to 18 */
    color: #CECFD2;
    opacity: 1;
}

::-moz-placeholder {
    /* Mozilla Firefox 19+ */
    color: #CECFD2;
    opacity: 1;
}

input:-ms-input-placeholder {
    color: #CECFD2;
    opacity: 1;
}

input::-webkit-input-placeholder {
    color: #CECFD2;
    opacity: 1;
}

input:focus,
select:focus {
    outline: 0;
}
```

## normalize.css

Normalize.css 是一种 CSS reset 的替代方案。Normalize.css 只是一个很小的 CSS 文件，但它在默认的 HTML 元素样式上提供了跨浏览器的高度一致性。
 
* 保护有用的浏览器默认样式而不是完全去掉它们
* 为大部分HTML元素提供一般化的样式
* 修复浏览器自身的bug并保证各浏览器的一致性
* 用一些小技巧优化CSS可用性
* 用注释和详细的文档来解释代码

[下载地址](http://necolas.github.io/normalize.css/)

[github 地址](https://github.com/necolas/normalize.css/blob/master/normalize.css)


使用 npm 安装

`npm install normalize.css`

引用

`import 'normalize.css/normalize.css'`
