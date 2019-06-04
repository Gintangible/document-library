# 1. 配置概况

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

[插件地址](https://docs.gitbook.com/v2-changes/important-differences)
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

[插件地址](https://docs.gitbook.com/v2-changes/important-differences)
[Github 地址](https://github.com/stuebersystems/gitbook-plugin-back-to-top-button)

```
{
	"plugins" : [ "back-to-top-button" ]
}
```

## 2.3. baidu-tongji

百度统计

[插件地址](https://docs.gitbook.com/v2-changes/important-differences)
[Github 地址](
https://github.com/huisman6/gitbook-plugin-baidu-tongji)


