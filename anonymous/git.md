# Git

## 文件重命名

将`a.md`重命名为`b.md`

```text
    git mv a.md b.md
```

不能使用系统资源管理器或者终端重命名，否则git只能识别为删除`a.md`并添加`b.md`。


## alias

```shell
# brif commit history
lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
# last commit info
last = log -1 HEAD
# auto add all, commit with "update" and push all to origin
acp = !git add . && git commit -m "update" && git push origin --all
```

## config
```
[core]
    autocrlf = false
    compression = -1
[user]
    email = YourEmailAddress
    name = YourName
[credential]
    helper = manager
[http]
    postBuffer = 524288000000
```