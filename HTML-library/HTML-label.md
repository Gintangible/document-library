# HTML5 标签

## 新增语义化标签

| 标签                  | 描述                             |
| --------------------- | -------------------------------- |
| <hrader></header>     | 定义了文档的头部区域             |
| <footer></footer>     | 定义了文档的尾部区域             |
| <nav></nav>           | 定义文档的导航                   |
| <section></section>   | 定义文档中的节（section、区段）  |
| <article></article>   | 定义页面独立的内容区域           |
| <aside></aside>       | 定义页面的侧边栏内容             |
| <detailes></detailes> | 用于描述文档或文档某个部分的细节 |
| <summary></summary>   | 标签包含 details 元素的标题      |
| <dialog></dialog>     | 定义对话框，比如提示框           |

页面常用的布局方式依旧是DIV+CSS；H5新增的标签，能使用的时候尽量使用的好，这样在页面缺少注释的情况下，再次对页面修改时，也更易看懂。

## 对于页面有两点注意 

1、**H1** 标签最好一个页面只用一次。
2、**p**标签内部不能放块标签，即使设置块标签的display为inline，inline-block，呈现的效果依旧是块元素效果。

```js
div {
    display: inline-block
}

<p>前面内容 <div>这是块标签</div>后面内容</p>
```

浏览器的审查元素效果：
![p标签内部添加块标签效果](./html-1.jpg 'p标签内部添加块标签效果')


