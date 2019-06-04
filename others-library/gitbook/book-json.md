# 1、配置概况

## 1.1. 全局配置

1.title
设置书本的标题
`"title" : "Gitbook Use"`
2.author
作者的相关信息
`"author" : "mingyue"`
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
