# svg

## 1. 创建 icon.vue

在`vue-cli`脚手架的`components`目录下，创建`svgIcon/index.vue`。

> index.vue

```
<template>
    <svg :class="svgClass" aria-hidden="true">
        <use :xlink:href="iconName" />
    </svg>
</template>

<script>
export default {
    name: 'SvgIcon',
    props: {
        iconClass: {
            type: String,
            required: true
        },
        className: {
            type: String,
            default: ''
        }
    },
    computed: {
        iconName() {
            return `#icon-${this.iconClass}`;
        },
        svgClass() {
            if (this.className) {
                return 'svg-icon ' + this.className;
            } else {
                return 'svg-icon';
            }
        }
    }
};
</script>
<style scoped>
.svg-icon {
    width: 1em;
    height: 1em;
    vertical-align: -0.15em;
    fill: currentColor;
    overflow: hidden;
}
</style>
```

## 2. 创建icons文件夹，存放svg文件夹、index.js

> -icons

```
    -svg        ———— 存放svg文件
    index.js
```

> index.js

```
import Vue from 'vue';
import SvgIcon from '@/components/SvgIcon'; // svg组件

// 全局注册
Vue.component('svg-icon', SvgIcon);

const req = require.context('./svg', false, /\.svg$/);
const requireAll = requireContext => requireContext.keys().map(requireContext);
requireAll(req);
```

## 3. main.js 中引入

```
// 引入icon
import './icons';
```

## 4. 修改 loader

仅上面的操作，在页面上看不到svg图片。还需使用和安装svg-sprite。

这里使用webpack loader中的一个`svg-sprite-loader`，可以将多个svg打包成svg-sprite

`npm install svg-sprire-loader --save-dev`

> vue.config.js
```
chainWebpack(config){ 
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
```

如此设置之后，即可使用。

## 5. 在页面中引用

`<svg-icon icon-class="home"></svg-icon>`

**打包之前必须修改路径，不然不会显示svg图**

`assetsPublicPath: '/',`