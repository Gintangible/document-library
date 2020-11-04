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

在`.ssh`文件夹，创建 `config` 文件（需验证下）。

```
Host gitlab.com
HostName gitlab.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa_accountName

Host github.com
HostName github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa_accountName
```

验证`ssh`

```
ssh -T gintangible@gitee.com
ssh -T gintangible@github.com
```









