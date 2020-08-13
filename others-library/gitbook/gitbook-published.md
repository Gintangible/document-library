## gitbook 部署

`Gitbook` 的资料文档使用的是 Digital Ocean 的主机，而 DO 家的很多地址被墙了，导致往往无法访问。因此除了将书籍发布到 GitBook.io 以外，能不能部署到其他地方？这时我找到了一个渠道——将书籍发布到 `GitHub Pages`。

* [Github Pages教程 X](#)

由于 `gitbook` 书籍可以通过 `gitbook` 本地构建出 site 格式，所以可以直接将构建好的书籍直接放到 GitHub Pages 中托管，之后，便可以通过如下地址访问书籍：

`<username>.github.io/<project>`

在网上查找[资料](https://blog.csdn.net/simplehouse/article/details/78766513)后，只需两步就可以完成 `gitbook` 部署： 生成网站 + 一键部署。

### 1. 生成网站

通过 `gitbook build` 将书籍内容输出到默认目录，即当前目录的 `_book` 目录。

`gitbook build`

### 2. 讲书籍部署到 gh-pages 分支

这里用到的是 `gh-pages` 插件。它可以将文件夹一键发布到 GitHub 项目下的 gh-pages 分支中。目前只能发布到 `gh-pages` 分支上，如何一键发布到其他分支上，请看 [`插件`](https://github.com/tschaub/gh-pages) 文档。

安装 `gh-pages`：

`npm install -g gh-pages`

一键发布：

`gh-pages -d _book`

然后 _book 下的所有文档都会部署到 `gh-pages` 分支上。