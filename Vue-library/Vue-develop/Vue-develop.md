## Vue 开发

`Vue`常见的的开发模式`vue vuex vue-router axios`。

### 1、Vue CLI

版本：3.8.2

[Vue CLI文档](https://cli.vuejs.org/zh/guide/)

1、vue cli 安装

`npm install -g @vue/cli`

2、创建项目

`vue create your-project`

### 项目目录

[目录结构解析](https://www.jianshu.com/p/cf9b56efd3b8)

> 初始化目录：

```
|-- dist —————————————————————————————— 打包后文件夹            
|-- public ———————————————————————————— 静态文件夹                                   
|   |-- favicon.ico                     
|   |-- index.html                 ———— 入口页面
|-- src ——————————————————————————————— 源码目录         
|   |--assets                      ———— 模块资源
|   |--components                  ———— vue公共组件
|   |--views                       ———— 页面文件
|   |--App.vue                     ———— 页面入口文件
|   |--main.js                     ———— 入口文件，加载公共组件
|   |--router.js                   ———— 路由配置
|   |--store.js                    ———— 状态管理  
|-- vue.config.js ————————————————————— 配置文件 
|-- .eslintrc.js —————————————————————— ES-lint校验                   
|-- .gitignore ———————————————————————— git忽略上传的文件格式   
|-- babel.config.js ——————————————————— babel语法编译                        
|-- package.json —————————————————————— 项目基本信息 
|-- postcss.config.js ————————————————— CSS预处理器(此处默认启用autoprefixer) 
```

对初始化目录做下优化：

> 优化目录：

```
|-- dist —————————————————————————————— 打包后文件夹            
|-- public ———————————————————————————— 静态文件夹                                   
|   |-- favicon.ico                     
|   |-- index.html                 ———— 入口页面
|-- src ——————————————————————————————— 源码目录
|   |--api                         ———— 接口统一管理文件夹
        -- api.js                  ———— 接口文件
|   |--assets                      ———— 模块资源
|   |--components                  ———— vue公共组件
|   |--mockjs                      ———— 数据模拟
|   |--router                      ———— 路由文件夹
        -- index.js                ———— 路由文件
|   |--store                       ———— 状态文件夹  
        -- index.js                ———— 状态文件       
|   |--style                       ———— 样式文件  
        -- common.scss             ———— 公共样式
|   |--utils                       ———— 工具文件夹
        -- fetch.js                ———— 工具函数
|   |--views                       ———— 页面文件
|   |--App.vue                     ———— 页面入口文件
|   |--main.js                     ———— 入口文件，加载公共组件
|-- .env      ————————————————————————— 线上环境 
|-- .env.development —————————————————— 测试环境    
|-- .env.production ——————————————————— 生产环境     
|-- vue.config.js ————————————————————— 配置文件 
|-- .eslintrc.js —————————————————————— ES-lint校验                   
|-- .gitignore ———————————————————————— git忽略上传的文件格式   
|-- babel.config.js ——————————————————— babel语法编译                        
|-- package.json —————————————————————— 项目基本信息 
|-- postcss.config.js ————————————————— CSS预处理器(此处默认启用autoprefixer) 
```

对于多环境配置，目前无正式数据，先琢磨着弄，[先参考这个](https://blog.csdn.net/qq_36407748/article/details/82050976)

当前[初始模板](https://github.com/Gintangible/vue-template)

> vue.config.js

```
const path = require('path');

function resolve(dir) {
    return path.join(__dirname, dir);
}

module.exports = {
    configureWebpack: {
        resolve: {
            // 添加别名
            alias: {
                '@': resolve('src'),
                assets: resolve('src/assets'),
                components: resolve('src/components'),
                views: resolve('src/views')
            }
        }
    },
    // 通用 mixin.scss var.scss 等引入.PS：结尾文件加;
    css: {
        loaderOptions: {
          sass: {
            prependData: `@import "@/styles/mixin.scss";`
          }
        }
    },
    chainWebpack(config) {
        // set svg-sprite-loader
        config.module
            .rule('svg')
            .exclude.add(resolve('src/icons'))
            .end();
        config.module
            .rule('icons')
            .test(/\.svg$/)
            .include.add(resolve('src/icons'))
            .end()
            .use('svg-sprite-loader')
            .loader('svg-sprite-loader')
            .options({
                symbolId: 'icon-[name]'
            })
            .end();
    },
    devServer: {
        proxy: {
            '/api': {
                target: 'http://m.baidu.com',//目标地址
                ws: true, //// 是否启用websockets
                changeOrigin: true, //开启代理：在本地会创建一个虚拟服务端，然后发送请求的数据，并同时接收请求的数据，这样服务端和服务端进行数据的交互就不会有跨域问题
                pathRewrite: {'^/api': '/'}    //这里重写路径
            }

        }
    }
};
```