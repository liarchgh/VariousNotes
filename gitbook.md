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
有时报错缺失文件，通过[github上的issue](https://github.com/GitbookIO/gitbook/issues/1309)里面的解决方案直接到正常的文件里复制过来就好了

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

#### 本机配置环境
命令很简单，但是需要做很多准备工作，最开始上网上直接搜索到处pdf的教程，都用不了，现在准备按照gitbook-cli的文档来试一试，以下时详细过程(环境:WSL Ubuntu18.04)：

* 直接执行命令
出现提示
```
InstallRequiredError: "ebook-convert" is not installed.
Install it from Calibre: https://calibre-ebook.com
```
* 按照提示
去了[calibre-ebook](https://calibre-ebook.com)的网站，按照[linux的下载页面](https://calibre-ebook.com/download_linux)提示执行了shell命令
```shell
sudo -v && wget -nv -O- https://download.calibre-ebook.com/linux-installer.sh | sudo sh /dev/stdin
```
期间下载`calibre-3.29.0-x86_64.txz`的速度极慢
* 再次执行命令
提示
```
    info: 7 plugins are installed
    info: 6 explicitly listed
    info: loading plugin "highlight"... OK
    info: loading plugin "search"... OK
    info: loading plugin "lunr"... OK
    info: loading plugin "sharing"... OK
    info: loading plugin "fontsettings"... OK
    info: loading plugin "theme-default"... OK
    info: found 1 pages
    info: found 0 asset files
    info: >> generation finished with success in 3.5s !
    info: >> 1 file(s) generated
```
成功~，然而这只是没有图片的情况，我在有图片的项目中导出pdf时提示：
```
    InstallRequiredError: "svgexport" is not installed.
    Install it using: "npm install svgexport -g"
```
* 按照提示执行命令：
```shell
    sudo npm install svgexport -g
```
下载`phantomjs-2.1.1-linux-x86_64.tar.bz2`，速度依然极慢
* 再次执行导出pdf命令成功，然而结果和下面一样，没有汉字

#### Docker
上一种方法配置到一半太浪费事件，我就自己去使用了gitlab的ci服务，会在用户Commit的时候根据工程根目录下`.gitlab-ci.yml`的文件中的配置来编译工程，以下是一次使用的配置
- 成功编译出静态页面并导出
```
    before_script:
    - env
    
    stages:
    - build
    
    ebook:
      stage: build
      image: fellah/gitbook
      script:
        - gitbook build
      artifacts:
        paths:
          - _book/*
```
- 成功编译出静态页面和PDF并导出，然而下载后发现PDF没有汉字
```
    before_script:
    - env
    
    stages:
    - build
    
    ebook:
      stage: build
      image: billryan/gitbook
      script:
        - gitbook build
        - gitbook pdf
      artifacts:
        paths:
          - _book/*
          - ./*.pdf
```

#### 最终决定
就这样吧，暂时使用gitbook，同时gitlab的自动部署也开着。如果之后gitbook免费期结束后加太多限制的话，就用自己服务器配置成gitlab外加github page来自动生成网页部署。

### 拉取gitbook远程分支

```shell
    gitbook fetch
```

我在使用[构建服务器](#gou-jian-fu-wu-qi)时出现了Error
```
Error: ENOENT: no such file or directory, stat'/mnt/c/Users/LeeSue/Documents/Projects/GitBook/Import/unity3dblog/_book/gitbook/gitbook-plugin-sharing/buttons.js'
```

