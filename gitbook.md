# GitBook

## [命令行工具基本使用](https://github.com/GitbookIO/gitbook/blob/master/docs/setup.md)

### 安装
```shell
    npm install -g gitbook-cli
```
可能需要sudo

### 帮助
```shell
    gitbook help
```

### 初始化目录
```shell
    gitbook init
```

### 构建服务器
```shell
    gitbook serve
```

动态，不会生成静态页面

### 构建静态网页
```shell
    gitbook build
```
生成的静态网页在工程目录的`_book`目录中

### 导出pdf

```shell
    gitbook pdf 工程目录
```

命令很简单，但是需要做很多准备工作，最开始上网上直接搜索到处pdf的教程，都用不了，现在准备按照gitbook-cli的文档来试一试，以下时详细过程(环境:WSL Ubuntu18.04)：

* 直接执行命令
出现提示
```
InstallRequiredError: "ebook-convert" is not installed.
Install it from Calibre: https://calibre-ebook.com
```
按照提示去了[calibre-ebook](https://calibre-ebook.com)的网站，按照[linux的下载页面](https://calibre-ebook.com/download_linux)提示执行了shell命令
```
sudo -v && wget -nv -O- https://download.calibre-ebook.com/linux-installer.sh | sudo sh /dev/stdin
```

### 拉取gitbook远程分支

```shell
    gitbook fetch
```

我在使用[构建服务器](#构建服务器)时出现了Error
```
Error: ENOENT: no such file or directory, stat'/mnt/c/Users/LeeSue/Documents/Projects/GitBook/Import/unity3dblog/_book/gitbook/gitbook-plugin-sharing/buttons.js'
```

