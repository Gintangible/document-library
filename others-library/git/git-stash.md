##  git branch

### 相关命令

`git stash list`：查看缓存的`stash`列表

`git stash save xx` ：以`xx`名缓存`stash`。

`git stash pop` ：将最近的缓存的`stash`取出来

 `git stash apply`：取出缓存`stash`，但不会把存储从存储列表中删除，默认使用第一个存储 

`git stash apply stash@{$num}`：取出`stash@{$num}`缓存

`git stash drop stash@{$num}`：丢弃`stash@{$num}`缓存，从列表中删除这个缓存

`git stash clear`：删除所有缓存的`stash`







