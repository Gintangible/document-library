## computed Object

**问题描述：**computed监听Vuex中state对象中的对象属性时，监听不生效的问题。

**问题代码：**

```vue
computed: {
   ...mapState({
      dataInfo: (state) => state.dataInfo,
   }),
}

mutations: {
	updateDataInfo(state, data) {
        state.dataInfo = Object.assign(state.dataInfo, data);
    },
	// 或者
	updateDataInfo(state, name) {
		state.dataInfo.name = name;
	},
}
```

**原因：**

​	1. `computed` 属性监听对象时候，若对象的引导地址未改变，那么 `computed` 将不会检测到。

比如object中的某个key对应的value变化了，computed检测不出来。

​	2. **Object.assign** 方法用于将所有可枚举属性的值从一个或多个源对象复制到目标对象。他将<span style="color: #f00;">返回目标对象</span>。

**解决方法：**

```javascript
state.dataInfo = Object.assign({}, state.dataInfo, data);
// or
state.dataInfo = {...state.dataInfo, ...data};
```


