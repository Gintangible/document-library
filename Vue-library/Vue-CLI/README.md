## Vue CLI

**1. 查看vue.config.js生成的webpack 配置**

```
vue inspect --mode production | less  /  vue inspect --mode stage | less 
```

通过以上命令看到 `vue-cli` 根据配置文件 `vue.config.js` 生成的webpack 配置。 

注意: | 是管道操作符，less是一个命令，用于翻页查看较长的内容。如果没有 | less ，输出内容太多超过好几屏看不清。加上 | less 就是把前面命令的输出通过管道定向为less命令的输入，这样就可以方便地翻页查看了（查看时通过上线箭头，page down, page up翻页。按 q 退出查看模式。）