# Linux应用

* [aria2](https://aria2.github.io/)

  多线程下载，可使用磁力链接、种子  
  [教程](https://yorkchou.com/aria2.html)  
  [基础配置文件](http://aria2c.com/usage.html)  
  [BT没速度](http://www.senra.me/solutions-to-aria2-bt-metalink-download-slowly/)

  [AriaNg](https://github.com/mayswind/AriaNg)  
  Aria2的Web前端，放在[服务器](https://www.jianshu.com/p/5e42c1031fb5)、客户机都可以
  
  我的配置文件`~/aria2.conf`:
  ```text
  ## '#'开头为注释内容, 选项都有相应的注释说明, 根据需要修改 ##
  ## 被注释的选项填写的是默认值, 建议在需要修改时再取消注释  ##
  
  ## 文件保存相关 ##
  
  # 日志文件
  log=/home/pi/.aria2/aria2.log
  # 日志级别
  log-level=notice
  # 文件的保存路径(可使用绝对路径或相对路径), 默认: 当前启动位置
  dir=/home/pi/Space/aria2
  # 启用磁盘缓存, 0为禁用缓存, 需1.16以上版本, 默认:16M
  disk-cache=32M
  # 文件预分配方式, 能有效降低磁盘碎片, 默认:prealloc
  # 预分配所需时间: none < falloc ? trunc < prealloc
  # falloc和trunc则需要文件系统和内核支持
  # NTFS建议使用falloc, EXT3/4建议trunc, MAC 下需要注释此项
  # file-allocation=falloc
  # 断点续传
  continue=true
  # 检查完整性
  check-integrity=true
  
  ## 下载连接相关 ##
  
  # 最大同时下载任务数, 运行时可修改, 默认:5
  max-concurrent-downloads=50
  # 同一服务器连接数, 添加时可指定, 默认:1
  max-connection-per-server=16
  # 最小文件分片大小, 添加时可指定, 取值范围1M -1024M, 默认:20M
  # 假定size=10M, 文件为20MiB 则使用两个来源下载; 文件为15MiB 则使用一个来源下载
  min-split-size=10M
  # 单个任务最大线程数, 添加时可指定, 默认:5
  split=200
  # 整体下载速度限制, 运行时可修改, 默认:0
  # max-overall-download-limit=4M
  # 单个任务下载速度限制, 默认:0
  #max-download-limit=0
  # 整体上传速度限制, 运行时可修改, 默认:0
  #max-overall-upload-limit=0
  # 单个任务上传速度限制, 默认:0
  #max-upload-limit=0
  # 禁用IPv6, 默认:false
  #disable-ipv6=true
  # 连接超时时间, 默认:60
  #timeout=60
  # 最大重试次数, 设置为0表示不限制重试次数, 默认:5
  #max-tries=5
  # 设置重试等待的秒数, 默认:0
  #retry-wait=0
  
  ## 进度保存相关 ##
  
  # 从会话文件中读取下载任务
  input-file=/home/pi/.aria2/aria2.session
  # 在Aria2退出时保存`错误/未完成`的下载任务到会话文件
  save-session=/home/pi/.aria2/aria2.session
  # 定时保存会话, 0为退出时才保存, 需1.16.1以上版本, 默认:0
  save-session-interval=60
  
  ## RPC相关设置 ##
  
  # 启用RPC, 默认:false
  enable-rpc=true
  # 允许所有来源, 默认:false
  rpc-allow-origin-all=true
  # 允许非外部访问, 默认:false
  rpc-listen-all=true
  # 事件轮询方式, 取值:[epoll, kqueue, port, poll, select], 不同系统默认值不同
  #event-poll=select
  # RPC监听端口, 端口被占用时可以修改, 默认:6800
  rpc-listen-port=6543
  # 设置的RPC授权令牌, v1.18.4新增功能, 取代 --rpc-user 和 --rpc-passwd 选项
  rpc-secret=lisu.io
  # 设置的RPC访问用户名, 此选项新版已废弃, 建议改用 --rpc-secret 选项
  #rpc-user=<USER>
  # 设置的RPC访问密码, 此选项新版已废弃, 建议改用 --rpc-secret 选项
  #rpc-passwd=<PASSWD>
  # 是否启用 RPC 服务的 SSL/TLS 加密,
  # 启用加密后 RPC 服务需要使用 https 或者 wss 协议连接
  #rpc-secure=true
  # 在 RPC 服务中启用 SSL/TLS 加密时的证书文件,
  # 使用 PEM 格式时，您必须通过 --rpc-private-key 指定私钥
  #rpc-certificate=/path/to/certificate.pem
  # 在 RPC 服务中启用 SSL/TLS 加密时的私钥文件
  #rpc-private-key=/path/to/certificate.key
  
  ## BT/PT下载相关 ##
  
  # 当下载的是一个种子(以.torrent结尾)时, 自动开始BT任务, 默认:true
  follow-torrent=true
  # BT监听端口, 当端口被屏蔽时使用, 默认:6881-6999
  listen-port=51413
  # 单个种子最大连接数, 默认:55
  bt-max-peers=100
  # 打开DHT功能, PT需要禁用, 默认:true
  enable-dht=true
  # 打开IPv6 DHT功能, PT需要禁用
  #enable-dht6=false
  # DHT网络监听端口, 默认:6881-6999
  #dht-listen-port=6881-6999
  # DHT(IPV4)文件
  dht-file-path=/home/pi/.aria2/dht.dat
  # DHT(IPV6)文件
  dht-file-path=/home/pi/.aria2/dht6.dat
  # 本地节点查找, PT需要禁用, 默认:false
  bt-enable-lpd=true
  # 种子交换, PT需要禁用, 默认:true
  enable-peer-exchange=true
  # 每个种子限速, 对少种的PT很有用, 默认:50K
  bt-request-peer-speed-limit=100M
  # 客户端伪装, PT需要
  peer-id-prefix=-TR2770-
  user-agent=Transmission/2.77
  # 当种子的分享率达到这个数时, 自动停止做种, 0为一直做种, 默认:1.0
  seed-ratio=0
  # 最小做种时间
  seed-time=4320
  # 强制保存会话, 即使任务已经完成, 默认:false
  # 较新的版本开启后会在任务完成后依然保留.aria2文件
  #force-save=false
  # BT校验相关, 默认:true
  #bt-hash-check-seed=true
  # 继续之前的BT任务时, 无需再次校验, 默认:false
  bt-seed-unverified=true
  # 保存磁力链接元数据为种子文件(.torrent文件), 默认:false
  bt-save-metadata=true
  bt-tracker=udp://tracker.coppersurfer.tk:6969/announce,udp://exodus.desync.com:6969/announce,udp://tracker.opentrackr.org:1337/announce,udp://tracker.internetwarriors.net:1337/announce,udp://9.rarbg.to:2710/announce,udp://tracker.vanitycore.co:6969/announce,udp://public.popcorn-tracker.org:6969/announce,udp://explodie.org:6969/announce,udp://tracker.mg64.net:6969/announce,udp://mgtracker.org:6969/announce,udp://ipv4.tracker.harry.lu:80/announce,udp://tracker.tiny-vps.com:6969/announce,udp://thetracker.org:80/announce,udp://bt.xxx-tracker.com:2710/announce,udp://tracker.torrent.eu.org:451/announce,udp://tracker.cypherpunks.ru:6969/announce,udp://open.stealth.si:80/announce,udp://tracker.port443.xyz:6969/announce,udp://retracker.lanta-net.ru:2710/announce,udp://open.demonii.si:1337/announce,udp://tracker4.itzmx.com:2710/announce,udp://tracker1.itzmx.com:8080/announce,udp://tracker.iamhansen.xyz:2000/announce,http://open.acgnxtracker.com:80/announce,http://0d.kebhana.mx:443/announce,udp://zephir.monocul.us:6969/announce,udp://tracker.uw0.xyz:6969/announce,udp://tracker.kamigami.org:2710/announce,udp://pubt.in:2710/announce,https://evening-badlands-6215.herokuapp.com:443/announce,http://tracker.city9x.com:2710/announce,http://t.nyaatracker.com:80/announce,http://retracker.telecom.by:80/announce,http://retracker.mgts.by:80/announce,http://omg.wtftrackr.pw:1337/announce,http://explodie.org:6969/announce,wss://tracker.openwebtorrent.com:443/announce,wss://tracker.iamhansen.xyz:443/announce,wss://tracker.fastcast.nz:443/announce,wss://tracker.btorrent.xyz:443/announce,ws://tracker.btsync.cf:2710/announce,udp://z.crazyhd.com:2710/announce,udp://trackerxyz.tk:1337/announce,udp://tracker1.wasabii.com.tw:6969/announce,udp://tracker.zer0day.to:1337/announce,udp://tracker.xku.tv:6969/announce,udp://tracker.tvunderground.org.ru:3218/announce,udp://tracker.swateam.org.uk:2710/announce,udp://tracker.skyts.net:6969/announce,udp://tracker.sandrotracker.biz:6969/announce,udp://tracker.qt.is:6969/announce,udp://tracker.piratepublic.com:1337/announce,udp://tracker.open-internet.nl:6969/announce,udp://tracker.justseed.it:1337/announce,udp://tracker.halfchub.club:6969/announce,udp://tracker.files.fm:6969/announce,udp://tracker.dutchtracking.com:6969/announce,udp://tracker.ds.is:6969/announce,udp://tracker.dler.org:6969/announce,udp://tracker.desu.sh:6969/announce,udp://tracker.cyberia.is:6969/announce,udp://tracker.bluefrog.pw:2710/announce,udp://tracker-2.msm8916.com:6969/announce,udp://t.agx.co:61655/announce,udp://sd-95.allfon.net:2710/announce,udp://retracker.nts.su:2710/announce,udp://retracker.coltel.ru:2710/announce,udp://peerfect.org:6969/announce,udp://packages.crunchbangplusplus.org:6969/announce,udp://p4p.arenabg.com:1337/announce,udp://oscar.reyesleon.xyz:6969/announce,udp://open.facedatabg.net:6969/announce,udp://ipv6.open-internet.nl:6969/announce,udp://inferno.demonoid.pw:3418/announce,http://tracker1.itzmx.com:8080/announce,http://tracker.vanitycore.co:6969/announce,http://tracker.torrentyorg.pl:80/announce,http://tracker.mg64.net:6881/announce,http://tracker.internetwarriors.net:1337/announce,http://tracker.electro-torrent.pl:80/announce,http://therightsize.net:1337/announce,http://share.camoe.cn:8080/announce,http://open.acgtracker.com:1096/announce,http://mgtracker.org:6969/announce
  ```

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

* [docker](https://www.docker.com/)

  [linux安装](https://docs.docker.com/install/)

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

