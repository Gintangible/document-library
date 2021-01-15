## git

## 其他

提交时转换为LF，检出时不转换

git config --global core.autocrlf input

提交检出均不转换

git config --global core.autocrlf false

git checkout -b xx 本地分支名  origin/远程分支名