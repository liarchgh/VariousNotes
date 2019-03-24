# NAS搭建

## [NextCloud搭建网盘](https://nextcloud.com/)

### [安装](https://jingyan.baidu.com/article/86f4a73ebd6e9437d7526961.html)
- 拉去nextcloud镜像
    ```shell
    docker pull nextcloud
    ```

- 新建容器并运行
    ```shell
    docker run --name MyNextcloud -p 81:80 -v /owncloud:/var/www/html/data -d nextcloud
    ```
    -- name：设定容器名称为nextcloud  
    -p 81:80 ：端口映射，将宿主机81端口映射到容器中的80端口  
    -v /owncloud:/var/www/html/data 将容器中项目的data目录映射到本地/owncloud目录下方便配置  
    -d nextcloud，就是刚刚所拉取的镜像名称

- 启动容器终端
    ```shell
    docker exec -it MyNextcloud /bin/bash
    ```
- 安装插件
  下载插件压缩包后解压至`/var/www/html/custom_apps`下，并把目录名中的版本号删掉

### [配置]()

- 修改trusted_domains  
    即可以通过什么域名访问
    ```json
    'trusted_domains' =>
    array (
        '192.168.1.111:81',
        '192.168.2.222:81',
    ),
    ```

### 插件

- [ocdownloader](https://github.com/e-alfred/ocdownloader)
    能够搭配aria2做离线下载

## [Plex Media Server](https://www.plex.tv/)

### [安装](https://www.smarthomebeginner.com/install-plex-using-docker/)
    
使用[官方docker](https://github.com/plexinc/pms-docker)时，按照[官方文档](https://www.plex.tv/media-server-downloads/)一直无法运行创建出的容器，无奈之下使用了找到的[另一个docker](https://github.com/linuxserver/docker-plex)

- 拉取镜像
```shell
docker pull linuxserver/docker-plex
```

- 创建容器
选线具体含义、格式在[文档](https://github.com/linuxserver/docker-plex/blob/master/README.md)中写的有  
`--net`网络类型，本来想只映射必要端口，懒得弄了
```shell
docker create \
--name=plex \
--net=host \
-e PUID=1000 \
-e PGID=1000 \
-e VERSION=docker \
-v /plex/config:/config \
-v /plex/data/tvshows:/data/tvshows \
-v /plex/data/movies:/data/movies \
-v /plex/transcode:/transcode \
--restart unless-stopped \
linuxserver/plex
```

- 运行镜像
```shell
docker run plex
```

- 使用plex服务
任意设备登录`http://<plex's ip>:32400/web`