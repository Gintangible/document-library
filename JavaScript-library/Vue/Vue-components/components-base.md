# 组件通信

## 1. 父子间通信

父组件通过 `props` 属性给子组件通信。

> parent.vue

```
<parent>
    <child :child-com="父组件内容"></child>
</parent>
```

子组件通过 `props` 来接受数据。

> child.vue

```
props: {
    childCom: {
        type: String,
        default: '子组件'
    }
}
```

## 2. 子组件与父组件通信

vue2.0只允许单向数据传递，我们通过出发事件来改变组件的数据。

> child.vue

```
<div @click="open"></div>

methods: {
    open() {
        //触发parentDoSomeThing方法，'the msg'为向父组件传递的数据
        this.$emit('parentDoSomeThing','the msg'); 
    }
}
```

> parent.vue

```
<child @parentDoSomeThing="parentDo" :msg="msg"></child>

methods: {
    parentDo(msg) {
        this.msg = msg;
    }
}
```

## 3. 兄弟组件之间通信

实例化一个vue实例，相当于一个第三方。即创建一个 `bus` 函数，实现兄弟通信。

知识点：

* 使用vm.$emit('事件名称'，'传入参数')，作为发送消息的那一方；
* 使用vm.$on('事件名称'，'回调函数')，作为接收消息的那一方。

> bus.js

```
import Vue from 'vue';
var bus = new Vue();

export default bus;
```

> gege.vue


```
<div @click="didiToDo"></div>

import bus from 'bus.js';
methods: {
    didiToDo() {
        vm.$emit('sendDidi', '我是哥哥');
    }
}
```

> didi.vue

```
<div></div>

import bus from 'bus.js';

mounted() {
    this.didiDoing();
},
methods: {
    didiDoing() {
        vm.$on('sendDidi', data => {
            console.log(data);
        });
    }
}
```


