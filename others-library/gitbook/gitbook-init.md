# gitbook 

### 安装

```
npm install gitbook-cli -g
```

  安装完成之后，可以使用下面的命令来检验是否安装成功。 

```
gitbook -V
```

<p style="color:#f00;">注意如果使用的高版本的node，运行会出错，最好使用低版本的node （8.9.4是ok的） </p>
**启动 `gitbook`** 

```
gitbook init 
```

自动创建`summary.md`中新添加的目录。

**浏览器预览**

```
gitbook serve
```

 输入上面命令后，既可浏览器中预览书籍。[热更新](./gitbook-issues.md#hot-updata)

 **本地构建**

```
gitbook build
```

运行该命令后会在书籍的文件夹中生成一个 `_book` 文件夹, 里面的内容即为生成的 html 文件。

