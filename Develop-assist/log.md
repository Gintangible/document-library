# 移动端日志

​		在做移动端项目时，由于在移动端无法打开控制台，所以调试`console`数据非常不方便。之前用的是chrome的`inspect`调试，但是只能使用移动版的chrome查看数据，兼容不好，故使用了`vConsole` / `eruda`进行调试。

### 1. vconsole

```
npm install vconsole
```

在引入`vConsole` 模块后，页面前端将会在右下角出现 `vConsole` 的悬停按钮，可展开/收起面板。 为了更好的体验，不让用户看到，在开发环境引入即可。

```javascript
if (process.env.NODE_ENV !== "production") {
  new VConsole();
}
```

### 2. eruda

```javascript
if (process.env.NODE_ENV !== "production") { 
  const eruda = require('eruda');
  eruda.init();
}
```

