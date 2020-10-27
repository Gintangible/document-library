---
typora-root-url: ..\..
---

## gitbook issues

<h3 id="hot-updata">1. 热更新失败</h3>
在使用 `gitbook serve` 启动 `gitbook` 服务后,如果本地文件发生更改,热加会失败。在网上找到了一个解决方案。即：

如果启动服务器后立即删除 `_book` 目录,那么之后再怎么修改本地文件都能顺利重启。

[原文地址](https://www.cnblogs.com/snowdreams1006/p/10834754.html)

<h3 id="gitbook-fail">2. gitbook -V 报错</h3>

![gitbook-fail](/others-library/gitbook/images/gitbook-fail.png)

此问题是`node`版本问题，只需下载低版本的`node`就可以了，`8.9.4`是满足要求的。