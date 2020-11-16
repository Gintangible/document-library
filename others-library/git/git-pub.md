##  git 公钥

### 1. 一般流程

配置用户名

```
git config --global user.name "username"
```

配置邮箱 

```
git config --global user.email "useremail@.com"
```

此时，会在C:\Users\Administrator目录下生成`.gitconfig`配置文件。

```
ssh-keygen -t rsa -C "useremail@.com"
```

按3次Enter。生成公钥和私钥（`id_rsa` 和`id_rsa.pub`）。

公钥路径。` C:\Users\Administrator\.ssh `

然后再`github -> setting -> SSH keys`上添加公钥。

### 2. 生成多个ssh key

```
ssh-keygen -t rsa -C "useremail@.com"  -f ~/.ssh/newname 
```

此时会在`.ssh`文件夹下生成`newname` 和`newname.pub`

在`.ssh`文件夹，创建 `config` 文件（不需要后缀名）。

```
# github 
Host github.com
HostName github.com
User gintangible
IdentityFile C:/Users/admin/.ssh/id_rsa
IdentitiesOnly yes
 
# njzhyl(guwx@njzhyl.cn)
Host dev.njzhyl.cn
HostName dev.njzhyl.cn
User guxw
IdentityFile C:/Users/admin/.ssh/njzhyl
IdentitiesOnly yes
```

验证`ssh`

```
ssh -T hostname
```

如果得到如下提示，表示这个ssh公钥已经获得了权限。

```
`Hi USERNAME! You've successfully authenticated, but github does not provide shell access.`
```

<span style="color:#f00;">**注意**：</span>生成密钥要在`git bash` 里生成，`window` 窗口是不行的。





