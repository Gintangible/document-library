## h5网页唤起小程序

基本使用方法，见[微信开放标签文档](https://developers.weixin.qq.com/doc/offiaccount/OA_Web_Apps/Wechat_Open_Tag.html)

**微信版本要求**为：7.0.12及以上。 系统版本要求为：iOS 10.3及以上、Android 5.0及以上。

`Vue` 项目唤起小程序。

###  1. 引入 weixin-js-sdk

```
npm install weixin-js-sdk
```

###  2. 注册组件

按微信 `JS-SDK` 要求绑定**安全域**，并通过 `config` 接口注入权限验证配置。

```
wx.config({
  debug: true, // 开启调试模式,调用的所有api的返回值会在客户端alert出来，若要查看传入的参数，可以在pc端打开，参数信息会通过log打出，仅在pc端时才会打印
  appId: '', // 必填，公众号的唯一标识
  timestamp: , // 必填，生成签名的时间戳
  nonceStr: '', // 必填，生成签名的随机串
  signature: '',// 必填，签名
  jsApiList: [], // 必填，需要使用的JS接口列表
  openTagList: [] // 可选，需要使用的开放标签列表，例如['wx-open-launch-app']
});
```

一般 `appId` `timestamp``nonceStr` `signature` 由后端接口返回。

即：

```
const response = await LoginApi(window.location.href);
wx.config(
    Object.assign(response, {
      // debug: true,
      jsApiList: [
        'onMenuShareAppMessage',
        'onMenuShareTimeline',
      ],
      openTagList: ['wx-open-launch-weapp'],
    })
);
```

###  3. 使用组件

```
<wx-open-launch-weapp
      id="launch-btn"
      username="gh_11111111111"
    >
      <script type="text/wxtag-template">
        <style>
        .btn {
        width: 100%px;
        height: 34px;
        color:#fff;
        font-size: 14px;
        background:#ffa419;
        }
        </style>
        <div class="btn">打开小程序</div>
      </script>
    </wx-open-launch-weapp>
```

`username` 需要使用看起来有效的，如果使用 `gh_111111111111` 真机上是没有出现按钮，改成 `gh_255f8ad2370b` 按钮出现了。

###  4. 解决vue警告

因为组件不是在 `vue` 中注册的，运行的是会报错。需忽视掉组件名。

```
Vue.config.ignoredElements = ['wx-open-launch-weapp'];
```

**注意**：

1. **样式无法写在外面中，只能在script标签内内链写或者行内样式**
2. **无论是内链还是行内 都不支持rem**
3. **不会继承样式**
4. **如果开发标签内需要使用图片，不能用本地图片，得用外网可以访问的图片，要不然会不显示**
5. **path一定要加上 <span style="color:#f00;">.html</span>**
6. **<span style="color:#f00;">真机环境</span>下才能看到效果**
7. **已验证的服务号，已加入JS安全域名**
8. <span style="color:#f00;">组件中的username必须是看起来“有效的”，最好是使用真实小程序原始id</span>