## Vue

> Create by **gintangible** on **2019-6-10 14:47**  
> Recently revised in **2019-6-6 16:47**

**1. 组件不验证**

`Vue` 中如果想使用其他应用的SDK定义的组件，直接使用的话，`Vue` 编译会报错，提示该组件未注册，如想使用，在 `main.js` 中添加如下代码：

```
Vue.config.ignoredElements = ['wx-open-launch-weapp'];
```

