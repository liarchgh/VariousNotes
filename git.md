# Git

## 文件重命名

将`a.md`重命名为`b.md`
```
    git mv a.md b.md
```
不能使用系统资源管理器或者终端重命名，否则git只能识别为删除`a.md`并添加`b.md`。