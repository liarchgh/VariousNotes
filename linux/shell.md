# Shell学习

## 技巧

* [文件名中包含空格](https://blog.csdn.net/keypeople/article/details/78147288)

  临时修改环境变量`IFS`，即`IFS: The Internal Field Separator that is used for word splitting after expansion and to split lines into words with the read built-in command. The default value is “<space><tab><new-line>”.`

  ```text
    GLOBAL_IFS=${IFS}
    # IFS=$(echo -en "\n\b")
    IFS=$'\n'
    for file in `find . -type f`; do
        echo "file: ${file}"
    done
    IFS=${GLOBAL_IFS}
  ```

