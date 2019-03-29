# Git

## 文件重命名

将`a.md`重命名为`b.md`

```text
    git mv a.md b.md
```

不能使用系统资源管理器或者终端重命名，否则git只能识别为删除`a.md`并添加`b.md`。


## alias
终端命令
```shell
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```

配置文件
```gitconfig
[alias]
    # brif commit history
    lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
    # last commit info
    last = log -1 HEAD
    # auto add all, commit with "update" and push all to origin
    acp = !git add . && git commit -m "update" && git push origin --all
```

## config
```gitconfig
[core]
    autocrlf = false
    compression = -1
[user]
    email = YourEmailAddress
    name = YourName
[credential]
    helper = manager
```

## 技巧

- 只Clone源码，不带提交历史
    ```shell
    git clone --depth=1 git@github.com:EpicGames/UnrealEngine.git
    ```

- [删除之前的提交，只保留最后X次](https://blog.czbix.com/remove-git-history.html)
    ```shell
    git cat-file commit master^X | sed -e '/^parent/ d' > tmpfile
    git rebase --onto $(git hash-object -t commit -w tmpfile) master
    rm -f tmpfile

    # 其中X是要保留的记录条数
    # 这个时候,你的log里已经没有历史的提交了,但是历史的数据还存在于本地,|
    # 要想完全删除的话,执行以下代码
    rm -rf .git/logs
    git gc
    ```
