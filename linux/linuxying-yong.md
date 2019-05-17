# Linux应用

* [Shadowsocks Server](https://shadowsocks.org/)

快速搭建:

```text
wget --no-check-certificate -O shadowsocks.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks.sh
chmod +x shadowsocks.sh
./shadowsocks.sh 2>&1 | tee shadowsocks.log
```

[json样例\(支持ipv6、多端口\)](https://github.com/liarchgh/VariousNotes/tree/13bea8773e08adf38cc6494f19ed8c7f2f633782/linux/shadowsocks.json):

```javascript
{
"server":"::",
"local_address":"127.0.0.1",
"local_port":1080,
"port_password":{
     "111":"pass1",
     "222":"pass2"
},
"timeout":600,
"method":"aes-256-cfb",
"fast_open":false
}
```

* [Syncloud](https://syncloud.org/)

  私人服务器系统，可直接安装于树莓派上

* [aria2](https://aria2.github.io/)

  多线程下载，可使用磁力链接、种子  
  [教程](https://yorkchou.com/aria2.html)  
  [基础配置文件](http://aria2c.com/usage.html)  
  [BT没速度](http://www.senra.me/solutions-to-aria2-bt-metalink-download-slowly/)

  [AriaNg](https://github.com/mayswind/AriaNg)  
  Aria2的Web前端，放在[服务器](https://www.jianshu.com/p/5e42c1031fb5)、客户机都可以

  [我的配置文件`~/aria2.conf`](https://github.com/liarchgh/VariousNotes/tree/13bea8773e08adf38cc6494f19ed8c7f2f633782/linux/aria2.conf)

* [catimg](https://github.com/posva/catimg)

  终端中低像素显示图片

* [cmatrix](https://github.com/abishekvashok/cmatrix)

  终端下起数字雨，电脑空闲时作壁纸挺好看的

* [dos2unix](http://dos2unix.sourceforge.net/)

  转换换行

* [Vim](https://github.com/vim/vimhttps://www.vim.org/)
* [Git](https://git-scm.com/)
* [python](https://www.python.org/)

  配套pip又有了一套环境

* [w3m](http://w3m.sourceforge.net/)

  终端网页浏览器

* [lynx](https://lynx.browser.org/)

  终端网页浏览器

* [Terminology](https://www.enlightenment.org/about-terminology.md)

  各种终端工具,需要桌面

* [gitbook-cli](https://github.com/GitbookIO/gitbook-cli)

  GitBook终端工具，可导出静态网页和PDF

* ntfs-config && ntfs-3g

  linux写ntfs格式设备所需

  [简单使用](https://www.cnblogs.com/pengdonglin137/p/3477869.html)

  Debian/Ubuntu安装:

  ```text
    sudo apt-get install ntfs-config ntfs-3g
  ```

* [ag](https://github.com/ggreer/the_silver_searcher)

  Debian/Ubuntu安装：

  ```text
    sudo apt-get install silversearcher-ag
  ```

* [7zip](https://www.7-zip.org/)

  Debian/Ubuntu安装：

  ```text
    sudo apt install p7zip-full
  ```

* [npm](https://nodejs.org/en/)

  [linux安装](https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions)

  Debian/Ubuntu安装Node.js 10：

  ```text
    curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
    sudo apt-get install -y nodejs
  ```

* [docker](../anonymous/docker.md)
* [Nginx](https://www.nginx.com/)

  Debian/Ubuntu安装:

  ```text
    sudo apt install nginx
  ```

* [screen](https://www.gnu.org/software/screen/)

  [简单使用](https://blog.csdn.net/hejunqing14/article/details/50338161)

* ssh

  [WSL中密钥权限问题](https://superuser.com/questions/1321072/ubuntu-on-windows-10-ssh-permissions-xxxx-for-private-key-are-too-open):

  ```text
    sudo ssh -i keyfile <user>@ip
  ```

  [端口转发](http://blog.creke.net/722.html) [解决本地只代理了localhost的问题](https://www.cnblogs.com/sparkdev/p/7497388.html)

* [MLDonkey](http://mldonkey.sourceforge.net/Main_Page)

  下载器，支持ed2k、BT等

