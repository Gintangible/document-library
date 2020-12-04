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

