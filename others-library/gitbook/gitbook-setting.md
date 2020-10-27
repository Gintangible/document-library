### 1. 配置概况

#### 1.1. 全局配置

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

#### 1.2. 插件列表 plugins

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
"plugins": ["-search"]
```

#### 1.3. 插件属性配置 pluginsConfig

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

### 2. 常用插件

记录一些实用的插件
用法：在 book.json 中添加"plugins"和"pluginConfig"字段。然后执行 `gitbook install`，或者使用 NPM 安装 `npm install gitbook-plugin-插件名`，也可以从源码 GitHub 地址中下载，放到 `node_modules` 文件夹里。

#### 2.1. Search Pro

支持中文搜索, 需要将默认的 `search`, `lunr` 插件去掉, 注意: 如果标题中有包含的关键字, 标题的样式会有所变化

[Github 地址](https://github.com/gitbook-plugins/gitbook-plugin-search-pro)

```
"plugins": [
    "-lunr",
    "-search",
    "search-pro"
]
```

#### 2.2. anchor-navigation-ex

添加 Toc 到侧边悬浮导航以及回到顶部按钮

```
"plugins" : [ "back-to-top-button" ]
```

### 2.3. 导航目录扩展

#### 2.3.1. folding-chapters

支持多层目录，点击导航栏的标题名就可以实现折叠扩展。

[Github 地址](https://github.com/Yakima-Teng/gitbook-plugin-folding-chapters)

```
"plugins" : [ "folding-chapters" ]
```

#### 2.3.2. expandable-chapters (expandable-chapters-small)

[Github 地址](https://github.com/DomainDrivenArchitecture/gitbook-plugin-expandable-chapters)
[Github 地址](https://github.com/lookdczar/gitbook-plugin-expandable-chapters-small-auto)

可扩展导航章节。支持多层目录，点击箭头才能实现收放目录。`expandable-chapters` 的箭头比 `expandable-chapters-small` 粗

```
"plugins" : [ "expandable-chapters" ]
"plugins" : [ "expandable-chapters-small" ]
```

#### 2.4. splitter

侧边栏宽度可调节

[Github 地址](https://github.com/yoshidax/gitbook-plugin-splitter)

```
"plugins" : [ "splitter" ]
```

#### 2.5. copy-code-button

代码复制按钮

[Github 地址](https://github.com/azu/gitbook-plugin-github-buttons)

```
"plugins" : [ "copy-code-button" ]
```

#### 2.6. insert-logo

将 logo 插入到导航栏上方中。设置路径时，设置成绝对路径，不然在其他的文件里，可能会访问不到。

[Github 地址](https://github.com/matusnovak/gitbook-plugin-insert-logo)

```
{
    "plugins": [ "insert-logo" ],
    "pluginsConfig": {
    "insert-logo": {
        "url": "https://github.com/Gintangible/document-library/blob/master/assets/images/logo.png",
        "style": "background: none; height: 30px; "
        }
    }
}
```

#### 2.7. favicon

浏览器标签栏的 favicon 图标。路径设置同 `insert-logo`。

[Github 地址](https://github.com/menduo/gitbook-plugin-favicon)

```
{
    "plugins": ["favicon"],
    "pluginsConfig": {
    "favicon": {
        "shortcut": "favicon.ico",
        }
    }
}
```

#### 2.8. 页面添加页脚、版权信息

##### 2.8.1 tbfed-pagefooter

添加页脚，版权信息

[Github 地址](https://github.com/zhj3618/gitbook-plugin-tbfed-pagefooter)

```
{
    "plugins": [
       "tbfed-pagefooter"
    ],
    "pluginsConfig": {
        "tbfed-pagefooter": {
            "copyright":"Copyright &copy xxxx.com 2017",
            "modify_label": "该文件修订时间：",
            "modify_format": "YYYY-MM-DD HH:mm:ss"
        }
    }
}
```

如果想加入一个URL，自己可以去index.js里，把 `powered by gitbook`，改成
powered by `<a href="你的URL" target="_blank">你的名字</a>`

##### 2.8.2 page-footer

内容比 `tbfed-pagefooter` 多

[Github 地址](https://github.com/skyFi/gitbook-plugin-page-footer)

```
{
    "plugins" : ["page-copyright"],
    "pluginsConfig" : {
        "page-copyright": {
          "description": "modified at",
          "signature": "你的签名",
          "wisdom": "Designer, Frontend Developer & overall web enthusiast",
          "format": "YYYY-MM-dd hh:mm:ss",
          "copyright": "Copyright &#169; 你的名字",
          "timeColor": "#666",
          "copyrightColor": "#666",
          "utcOffset": "8",
          "style": "normal",
          "noPowered": false,
        }
    }
}
```

运行以后有很多信息是原创作者的，这些配置都在你的插件安装目录`**\node_modules\gitbook-plugin-page-copyright` 下的 `index.js` 中，自己可以修改。大部分信息都在 `defaultOption` 中。
那个二维码可以在文件中找到QRcode改成自己的，或者直接把所有的 `efaultOption.isShowQRCode` 改成 `false`。


#### 2.9. sharing-plus

分享当前页面，比默认的 sharing 插件多了一些分享方式。
现在 sharing-plus 插件在 github 搜索不到， 但是 npm 还是可以下载使用的。

```
{
    "plugins": ["-sharing", "sharing-plus"],
    "pluginsConfig": {
        "sharing": {
             "douban": false,
             "facebook": false,
             "google": true,
             "pocket": false,
             "qq": false,
             "qzone": true,
             "twitter": false,
             "weibo": true,
          "all": [
               "douban", "facebook", "google", "instapaper", "linkedin","twitter", "weibo", 
               "messenger","qq", "qzone","viber","whatsapp"
           ]
       }
    }
}
```

#### 2.10. donate

文章最下面的按钮，点击可弹出图片。

[Github 地址](https://github.com/willin/gitbook-plugin-donate)

```
{
    "plugins": ["donate"],
    "pluginsConfig": {
        "donate": {
            "button": "加好友",
            "title": "打赏插件",
            "alipayText": "支付宝打赏",
            "wechatText": "微信打赏",
            "wechat": "https://github.com/Gintangible/document-library/blob/master/assets/images/wx-code.jpg",
            "alipay": "https://github.com/Gintangible/document-library/blob/master/assets/images/wx-code.jpg"
        }
    }
}
```

#### 2.11. 其他插件
[github-buttons](https://github.com/azu/gitbook-plugin-github-buttons) 顶部添加 github 信息

[baidu-tongji](https://github.com/huisman6/gitbook-plugin-baidu-tongji) 百度统计

[back-to-top-button](https://github.com/stuebersystems/gitbook-plugin-back-to-top-button) 回到顶部

[prism](https://github.com/gaearon/gitbook-plugin-prism) 代码高亮

[了解更多插件](https://www.jianshu.com/p/427b8bb066e6)
