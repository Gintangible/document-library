# 其他

## 统计

根据用户名时间段统计代码量

```
git log --author=gintangible@163.com --since=2018-01-01 --until=2019-12-31 --pretty=tformat: --numstat | awk '{ add += $1; subs += $2; loc += $1 - $2 } END { printf "added lines: %s, removed lines: %s, total lines: %s\n", add, subs, loc }' -
```

[其他统计方式](https://www.cnblogs.com/chenzhenfj/p/11249164.html)

