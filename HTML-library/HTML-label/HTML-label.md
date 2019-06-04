# HTML5 标签

注意两点：  
    一个页面只能有一个 **H1** 标签  
    **p**标签内部不能放块标签，即使设置块标签的display为inline，inline-block，呈现的效果依旧是块元素效果。

```js
div {
    display: inline-block
}

<p>前面内容 <div>这是块标签</div>后面内容</p>
```

```
浏览器的审查元素效果：
![p标签内部添加块标签效果](./html.jpg 'p标签内部添加块标签效果')
```



