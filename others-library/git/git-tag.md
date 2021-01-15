## git tag

### 1.创建tag：

创建 tag 是基于本地分支的 commit，而且与分支的推送是两回事，就是说分支已经推送到远程了，但是你的 tag 并没有，如果把 tag 推送到远程分支上，需要另外执行 tag 的推送命令。

> 创建本地tag

```
git tag <tagName> 
```

> 推送到远程仓库

```
git push origin <tagName>
```

> 推送的全部本地标签

```
git push origin --tags
```

以上是基于本地当前分支的最后的一个commit 创建的 tag ，但是如果不想以最后一个，只想以某一个特定的提交为tag ，也是可以的，只要你知道commit 的id。

```
git log --pretty=oneline
```

```
git tag -a <tagName> <commitId>
```

### 2.查看标签

> 查看本地某个 tag 的详细信息

```
git show <tagName>
```

> 查看本地所有 tag

```
git tag 或者 git tag -l
```

> 查看远程所有 tag

```
git ls-remote --tags origin
```

### 3.删除标签

> 本地 tag 的删除

```
git tag -d <tagName>
```

> 远程 tag 的删除

```
git push origin :<tagName>
```

### 4.检出标签

```
git checkout -b <branchName> <tagName>
```

因为 tag 本身指向的就是一个 commit，所以和根据commit id 检出分支是一个道理。

但是需要特别说明的是，如果我们想要修改 tag检出代码分支，那么虽然分支中的代码改变了，但是 tag标记的 commit还是同一个，标记的代码是不会变的，这个要格外的注意。

其它

> 指定标签信息

```
git tag -a <tagname> -m "XXX..."
```

> 切换标签

```
git checkout [tagname] 
```