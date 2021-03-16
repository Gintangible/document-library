## 分支

**1. 创建本地分支**

```bash
git branch 分支名
```

如果分支是master(远程分支)，则是基于master分支创建的本地分支dev。

**2. 切换到本地分支**

```bash
git checkout 分支名
```

**3. 创建本地分支并切换**

```bash
 git checkout -b 分支名 
```

基于当前分支master创建本地分支dev并切换到该分支下。

**4. 提交本地分支到远程仓库**

```bash
git push origin 本地分支名
```

把本地 dev 分支提交到远程仓库，即创建了远程分支dev。

**5. 本地创建分支并切换到该分支**

```bash
git checkout -b dev(本地分支名称) origin/dev(远程分支名称)
```

基于当前分支master创建本地分支dev并切换到该分支下，并与远程dev分支关联。

**6. 删除本地分支**

```bash
git branch -d dev
```

必须保证不在删除的分支上，才能进行删除。

**7. 删除远程分支**。切到master分支

```bash
git push --delete origin xx
```

**8. 关联远程分支**

```bash
git branch --set-upstream-to=origin/xxx xxx
```

