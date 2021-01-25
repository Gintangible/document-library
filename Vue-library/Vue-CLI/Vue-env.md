# Vue .env

`package.json` 里的 `scripts` 配置 serve build，通过 `--mode xxx` 来执行不同环境。



- `yarn serve` 启动本地

- `yarn stage` 打包测试

- `yarn build` 打包正式



```json
"serve": "vue-cli-service serve",
"serve:prod": "vue-cli-service serve --mode production",
"stage": "vue-cli-service build --mode stage",
"build": "vue-cli-service build --mode production",
```



**##### 配置介绍**

`.env.xx` 中变量要以 `VUE_APP_` 开头，在代码中可以通过 `process.env.VUE_APP_` 访问。



在项目根目录中新建`.env.*`



> .env.development 本地开发环境配置

```
NODE_ENV=development
```



`.env.stage` 、`.env.production` 类似 `.env.development`。在这里只定义了基础的 `VUE_APP_ENV`, 其他变量统一放在 `src/config/env.*.js` 中进行管理。（***\*修改起来方便，不需要重启项目，符合开发习惯\****。）

如下：

```
// 通用配置 common.js
module.exports = {
  app_name: 'vue-h5-template',
  app_version: '0.1.0',
  // HTTP请求超时时间，单位为毫秒，默认值为5分钟
  request_timeout: 5 * 60 * 1000,
};


// 本地环境配置
module.exports = {
  debug: true,
  mocking: true,
  base_url: 'https://test.xxx.com',
  base_url_api: '',
};

... stage

... production

// index.js
const env = process.env.VUE_APP_ENV || 'development';
const defaultConfig = require('./common');
/* eslint-disable */
const envConfig = require(`/env.${env}`);
/* eslint-enable */
const config = { ...defaultConfig, ...envConfig };

export default config;
```

