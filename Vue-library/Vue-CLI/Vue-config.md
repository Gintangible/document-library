## Vue.config.js

**1. 在webpack注入一个全局变量**

```
chainWebpack: (config) => {
   if (process.env.NODE_ENV === "development") {
      config.plugin('define').tap((definitions) => {
        const args = definitions[0]['process.env'];
        args.VUE_APP_XX = JSON.stringify(process.env.NODE_ENV);
        return definitions;
      });
   }
},
```

设置之后，即可在 `vue`中可以通过 `process.env.VUE_APP_XX` 获取到对应的信息。

**2. 压缩打包大小**

```
module.exports = {
    productionSourceMap: false,
}
```

在设置了 `productionSourceMap`之后，就不会生成map文件，map文件的作用在于：项目打包后，代码都是经过压缩加密的，如果运行时报错，输出的错误信息无法准确得知是哪里的代码报错。也就是说map文件相当于是查看源码的一个东西。如果不需要定位问题，并且不想被看到源码，就把 `productionSourceMap `置为 `false`，既可以减少包大小，也可以加密源码。