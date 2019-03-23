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

### [插件](https://github.com/e-alfred/ocdownloader)