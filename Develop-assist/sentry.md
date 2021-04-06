# 前端日志上报 sentry

自建 `sentry` 服务器。（由后端配置好）

#### 注意事项

1. 利用本地搭建的sentry创建项目的时候，发现dsn那一栏是空的，系统并没有自动生成。需要自己拼接这个dsn。它由以下几部分组成，分别是协议、公钥、私钥、主机、路径（一般为空）、项目id。

```
'{PROTOCOL}://{PUBLIC_KEY}:{SECRET_KEY}@{HOST}/{PATH}{PROJECT_ID}'

//类似这样，把它放在sentry.init中的dsn即可

http://4cf10206ef27409bbb64f68b:a67a0eb5513e43ab883af3f3@localhost:9000/2
```

## 前端配置

根据 `sentey`  服务器创建项目后的提示，在对应的前端项目安装对应的依赖。

```javascript
yarn add @sentry/vue @sentry/tracing

Sentry.init({
    Vue,
    release: config.app_version,
    dsn: '生成项目时会生成',
    autoSessionTracking: true,
    integrations: [
      new Integrations.BrowserTracing(),
    ],

    // We recommend adjusting this value in production, or using tracesSampler
    // for finer control
    tracesSampleRate: 1.0,
});
```



### 上传 map 文件

使用 `@sentry/webpack-plugin` 上传 `map` 文件。

> package.json

```json
"build:sentry": "sentry=true vue-cli-service build --mode production",
```

```javascript
yarn add @sentry/webpack-plugin --dev

// 生产环境构建生成 source map
productionSourceMap: !!process.env.sentry,

chainWebpack: (config) => {
	if (process.env.NODE_ENV === 'production') {
      const fileName = JSON.stringify(require('./package.json').name);
      config.plugin('sentry').use(SentryPlugin, [
        {
          release: process.env.npm_package_version,
          // 必须，array or string，指定sentry-cli扫描的文件夹，它会将js和匹配的map文件上传
          include: `./${fileName}/static/js/`,
          // 可选，重要！！！上传到Sentry的SourceMap及源文件的名称，用于解析时的匹配
          urlPrefix: `~/${fileName}/static/js`,
          // 可选，string, 扫描时所忽略的文件的配置文件所在位置,格式和.gitignore一样
          // ignoreFile: '.sentrycliignore',
          // configFile: 'sentry.properties', //可选，string，sentry-cli的配置文件位置，
          ignore: ['node_modules'],
          deleteAfterCompile: true,
        }
      ]);
	}
}
```

> .sentryclirc

```
[defaults]
url=********
org=sentry
project=test (不要使用连字符)

[auth]
token=**************
```

### 删除项目中的`map`文件

由于我们在`vue.config.js`中开启了`productionSourceMap`，所以每次`yarn build`都会生产`map`文件，这就会导致打包体积很大，并且如果`map`文件被上传到线上，可能存在安全隐患，所以在打包之后删除`map`文件，因为执行`yarn  build`之后已经将`source-map`上传到了`Sentry`，本地打包出来的`map`文件已经没有用了，所以是可以删除的
 1、手动删除
 2、构建命令删除 （`find 打包目录 -name '*.js.map' -delete`）

