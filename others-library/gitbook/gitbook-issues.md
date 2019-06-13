# gitbook issues

## 1. 热更新失败

在使用 `gitbook serve` 启动 `gitbook` 服务后,如果本地文件发生更改,热加会失败。在网上找到了一个解决方案。即：

如果启动服务器后立即删除 `_book` 目录,那么之后再怎么修改本地文件都能顺利重启。

[原文地址](https://www.cnblogs.com/snowdreams1006/p/10834754.html)