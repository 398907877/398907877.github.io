---
layout:     post
title:      Centos 7利用Docker搭建Nextcloud
subtitle:   Centos 7利用Docker搭建Nextcloud
date:       2020-11-23
author:     吴佳俊
header-img: img/Nextcloud_Logo.svg.png
catalog: true
tags:
    - wujiajun
    - Nextcloud
    - Docker
    - Nextcloud
---








## Centos 7利用Docker搭建Nextcloud



![img](http://bluetears.cn-bj.ufileos.com/%E7%BD%91%E7%AB%99%E4%BD%BF%E7%94%A8%2F%E6%96%87%E7%AB%A0_nextcloud%2Flogo.jpg)

#### 1、官方命令拉取安装Docker



```
yum install -y yum-utils device-mapper-persistent-data lvm2

yum-config-manager –add-repo https://download.docker.com/linux/centos/docker-ce.repo

curl -fsSL https://get.docker.com | bash -s docker –mirror Aliyunz
```





#### 2、设置启动Docker并设置开机启动



```
systemctl start docker
```



```
systemctl enable docker
```

#### 3、拉取nextcloud docker镜像



```
docker pull nextcloud
```

#### 4、创建容器并启动



```
docker run --restart=always --name nextcloud -p 5000:80 -v /nextcloud:/var/www/html/data -d nextcloud
```



```
参数解释：
```



```
--restart=always：容器自动重启，宿主机启动时候同时启动容器
```



```
--name：容器名字
```



```
-p：端口映射，前面为宿主机端口，后面为容器端口
```



```
-v：存储目录映射，前面为宿主机目录，后面为容器目录
```



```
-d：后台形式运行
```

#### 5、输入IP（或者域名）：5000登陆nextcloud后台进行设置使用

![img](http://bluetears.cn-bj.ufileos.com/%E7%BD%91%E7%AB%99%E4%BD%BF%E7%94%A8%2F%E6%96%87%E7%AB%A0_nextcloud%2F%E7%99%BB%E5%BD%95%E7%95%8C%E9%9D%A2.jpg)

![img](http://bluetears.cn-bj.ufileos.com/%E7%BD%91%E7%AB%99%E4%BD%BF%E7%94%A8%2F%E6%96%87%E7%AB%A0_nextcloud%2F%E6%8E%A7%E5%88%B6%E5%8F%B0.jpg)

#### 6、其他命令



```
docker ps #展示已运行容器
```

```
docker start 容器ID #启动容器
```

```
docker stop 容器ID #停止容器
```

```
docker restart 容器ID #重启容器
```

```
docker images  #展示已下载的注册表
```

```
docker rmi  容器ID #删除容器
```

```
docker ps -a  #列出所有已创建容器，包含未运行
```

```
docker rm 容器名  #删除指定容器
```



