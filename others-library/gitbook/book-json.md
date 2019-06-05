# 1. 配置概况

## 1.1. 全局配置

1.title

设置书本的标题
`"title" : "Gitbook Use"`

2.author

作者的相关信息
`"author" : "gintangible"`

3.description

本书的简单描述
`"description" : "记录Gitbook的配置和一些插件的使用"`

4.language

Gitbook 使用的语言, 版本 2.6.4 中可选的语言如下：
`en, ar, bn, cs, de, en, es, fa, fi, fr, he, it, ja, ko, no, pl, pt, ro, ru, sv, uk, vi, zh-hans, zh-tw`
例如，配置使用简体中文
`"language" : "zh-hans"`

5.links

在左侧导航栏添加链接信息

```
"links" : {
    "sidebar" : {
        "Home" : "https://www.baidu.com"
    }
}
```

6.styles

自定义页面样式， 默认情况下各 generator 对应的 css 文件

```
"styles": {
    "website": "styles/website.css",
    "ebook": "styles/ebook.css",
    "pdf": "styles/pdf.css",
    "mobi": "styles/mobi.css",
    "epub": "styles/epub.css"
}
```

例如使`<h1> <h2>`标签有下边框， 可以在`website.css`中设置

```
h1 , h2{
    border-bottom: 1px solid #EFEAEA;
}
```

## 1.2. 插件列表 plugins

gitbook 取消了插件系统，无法在 gitbook 上搜索插件。原文如下：

```
In general, the plugin system no longer exists. However, important plugins have become first-class features in the new version. Here is a non-exhaustive list:
    Syntax highlighting (prism)
    Image captions (image-captions)
    Heading anchors (headings)
    Easily selecting code snippet content (copy-code)
    Algolia's search (algolia, lunr)
    Google Analytics (ga)
    Edit on GitHub button (github, github-buttons)
    Page's table of content (atoc, toc)
    Code block filename/tabs (codeblock-filename, code-tabs)

```

```
"plugins": [
    "search",
    "back-to-top-button",
    "expandable-chapters-small",
    "insert-logo"
]
```

添加新插件之间需要运行`gitbook install`来安装新的插件
Gitbook 默认自带有 5 个插件:

- highlight： 代码高亮
- search： 导航栏查询功能（不支持中文）
- sharing：右上角分享功能
- font-settings：字体设置（最上方的"A"符号）
- livereload：为 GitBook 实时重新加载

如果要去除自带的插件， 可以在插件名称前面加`-`

```
"plugins": [
    "-search"
]
```

## 1.3. 插件属性配置 pluginsConfig

配置插件的属性
例如配置 insert-logo 的属性：

```
"pluginsConfig": {
  "insert-logo": {
    "url": "images/logo.png",
    "style": "background: none; max-height: 30px; min-height: 30px"
  }
}
```

# 2. 常用插件

记录一些实用的插件
用法：在book.json中添加"plugins"和"pluginConfig"字段。然后执行 `gitbook install`，或者使用NPM安装 `npm install gitbook-plugin-插件名`，也可以从源码GitHub地址中下载，放到 `node_modules` 文件夹里。
  
## 2.1. Search Pro

支持中文搜索, 需要将默认的 `search`, `lunr` 插件去掉, 注意: 如果标题中有包含的关键字, 标题的样式会有所变化

[Github 地址](https://github.com/gitbook-plugins/gitbook-plugin-search-pro)

```
"plugins": [
    "-lunr",
    "-search",
    "search-pro"
]
```

## 2.2. back-to-top-button 

回到顶部

[Github 地址](https://github.com/stuebersystems/gitbook-plugin-back-to-top-button)

```
{
	"plugins" : [ "back-to-top-button" ]
}
```

## 2.3. 导航目录扩展

### 2.3.1. folding-chapters

支持多层目录，点击导航栏的标题名就可以实现折叠扩展。

[Github 地址](https://github.com/Yakima-Teng/gitbook-plugin-folding-chapters)

```
{
	"plugins" : [ "folding-chapters" ]
}
```

## 2.3.2. expandable-chapters (expandable-chapters-small)


[Github 地址](https://github.com/DomainDrivenArchitecture/gitbook-plugin-expandable-chapters)
[Github 地址](https://github.com/lookdczar/gitbook-plugin-expandable-chapters-small-auto)

可扩展导航章节。支持多层目录，点击箭头才能实现收放目录。`expandable-chapters` 的箭头比 `expandable-chapters-small` 粗

```
{
	"plugins" : [ "expandable-chapters" ]
    "plugins" : [ "expandable-chapters-small" ]
}
```

## 2.4. splitter

侧边栏宽度可调节

[Github 地址](https://github.com/yoshidax/gitbook-plugin-splitter)

```
{
	"plugins" : [ "splitter" ]
}
```

## 2.5. copy-code-button

代码复制按钮

[Github 地址](https://github.com/azu/gitbook-plugin-github-buttons)

```
{
	"plugins" : [ "copy-code-button" ]
}
```

## 2.6. insert-logo

将logo插入到导航栏上方中。设置路径时，设置成绝对路径，不然在其他的文件里，可能会访问不到。

[Github 地址](https://github.com/matusnovak/gitbook-plugin-insert-logo)

```
{
    "plugins": [ "insert-logo" ]
    "pluginsConfig": {
      "insert-logo": {
        "url": "https://github.com/Gintangible/document-library/assets/images/logo.png",
        "style": "background: none; height: 30px; "
      }
    }
}
```

## 2.7. favicon

浏览器标签栏的favicon图标。

[Github 地址](https://github.com/Bandwidth/gitbook-plugin-custom-favicon)

```
{
    "plugins": [
        "favicon"
    ],
    "pluginsConfig": {
        "favicon": {
            "shortcut": "favicon.ico",
        }
    }
}
```

## 2.8. sharing-plus

## 2.9. 页面添加页脚、版权信息

## 2.10. donate

## 2.11. 生成页内目录

## 2.12. 悬浮目录

## 2.13. 其他插件

github-buttons  顶部添加github信息

[Github 地址](https://github.com/azu/gitbook-plugin-github-buttons)

baidu-tongji    百度统计

[Github 地址](https://github.com/huisman6/gitbook-plugin-baidu-tongji)

[了解更多插件](https://www.jianshu.com/p/427b8bb066e6)




