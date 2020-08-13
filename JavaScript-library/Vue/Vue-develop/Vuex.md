## Vuex

`Vuex` 的基本使用可以用下方方式。更复杂的建议看 **[官方文档](https://vuex.vuejs.org/zh/)**。

npm 安装

`npm install vuex --save`

### 1. 创建store文件夹

创建 `store` 文件夹，存放状态文件。

```
|-- store ————————————————————————————— 状态文件夹
    |--modules                     ———— 模块资源
        |-- moduleA.js             ———— a状态文件                         
|   |-- getters.js                 ———— 属性暴露  
|   |-- index.js                   ———— 入口文件
```

state 数据源
mutation 非常类似于事件。
Action 提交的是 mutation，而不是直接变更状态。
Action 可以包含任意异步操作。


> moduleA.js

```
const moduleA = {
    state: {
        a: 'test'
    },
    mutations: {
        SET_A: (state, valueA) => {
            state.a = valueA;
        }
    },
    actions: {
        set_a({ commit }, valueA) {
             commit('SET_A', valueA);
        }
    }
}

export default moduleA;
```

> getters.js

```
const getters = {
    a: state => state.moduleA.a
}

export default getters;
```

> index.js

```
import Vue from 'vue';
import Vuex from 'vuex';
import getters from './getters';
import moduleA from './modules/moduleA';

Vue.use(Vuex);

const store = new Vuex.Store({
    modules: {
       moduleA
    },
    getters
});

export default store;
```

### 2. main.js 引入

> main.js

```
import Vue from 'vue';
import store from './store';

/* eslint-disable no-new */
new Vue({
    router,
    store,
    render: h => h(App)
}).$mount('#app');
```

### 3. 组件内部使用

> component.vue

```
// 触发方法
this.$store.dispatch('set_a', 'valueA');

// 获取单个getters
computed: {
    getA() {  
        return this.$store.state.moduleA.a;
    }
},

// 获取多个getters
import { mapGetters } from 'vuex';

computed: {
    ...mapGetters(['a'])
}
```
