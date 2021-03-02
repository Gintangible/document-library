# 手机系统设置字体大小影响h5页面字体

**问题描述：**

1. 我们的`h5` 页面是嵌入到 `app` 里面，用 `webview` 实现浏览器打开的，改变系统字体大小，影响 `h5` 页面字体

2. 在手机浏览器打开没有问题

**原因：**

安卓的 `webview` 会出现这个问题，因为 `webview` 是手机内置浏览器的sdk封装出来的组件，因此会受手机系统的影响，但是ios的webview不会出现这个问题。

**解决方法：**

1. 经过测试发现我们用`document.documentElement.style.fonSize`获取出来的都是36px，但是实际上页面字体变大了，说明1px代表的像素变大了。既然问题出现在安卓，那安卓一定会有相应的解决办法: `webview.getSettings().setTextZoom(100)` ，这个方法可以设置webview内部字体的缩放比例,设置为100%也就是按照默认大小来显示，而不会是字体选择中的“大”、“超大”（大于100%）或者“小”（小于100%）。而因为限制了px的缩放比例,我们的长度也最终得以正常呈现。

2. 由于我们的 app 是使用别人的应用，所以让他们去改动会比较麻烦，因此只能我们页面改动：假设你的 html fontsize 设定为 a px，实际显示是 b px，但是你想让他显示是 a px，因此你需要把 html 的 fontsize 调整为 a*a/b px，这样在系统字体大小变化时你还是可以保持设定的布局大小的。

用`window.getComputedStyle(document.querySelector('html'),null).getPropertyValue('font-size')`可以获取到实际的大小，`document.documentElement.html.style.fonSize` 获取的是设定值而不是具体值。

设定完html的fontsize大小后再获取实际的html大小判断是否一致，如果不一致再设定一次大小为a*a/b即可解决。

> adjust-font-size.js

```
// 移除 px 单位
import removePx from './remove-px';

// fix 在安卓环境里，改变系统字体大小，导致页面中的html上的字体大小跟computed 的字体大小不一致
export default function adjustFontSize() {
  const computedFontSize = window.getComputedStyle(document.querySelector('html'), null).getPropertyValue('font-size');
  const cFz2Num = removePx(computedFontSize);
  const htmlFontSize = document.documentElement.style.fontSize;
  const hFz2Num = removePx(htmlFontSize);

  if (computedFontSize !== htmlFontSize) {
    document.documentElement.style.fontSize = `${(hFz2Num * hFz2Num) / cFz2Num}px`;
  }
}

```

