# vconsole

​		在做移动端项目时，由于在移动端无法打开控制台，所以调试`console`数据非常不方便。之前用的是chrome的`inspect`调试，但是只能使用移动版的chrome查看数据，兼容不好，故使用了`vConsole` 进行调试。

### 1. 安装

```
npm install vconsoel
```

在引入`vConsole` 模块后，页面前端将会在右下角出现 `vConsole` 的悬停按钮，可展开/收起面板。 为了更好的体验，不让用户看到，在开发环境引入即可。

```
if (process.env.NODE_ENV === "development") {
  new VConsole();
}
```

