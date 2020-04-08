---
tags:
  - daily
date: 2020-04-04
title: centos安装docker
vssue-title: 固定的 Issue 标题
---
使用docker,安装nginx服务器，并部署自己的小demo
<!-- more -->

### 1.安装依赖包
```
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
```
![1.jpg](https://i.loli.net/2020/04/04/jryG12x4mDJwo8b.png)

### 2.设置阿里云镜像
```
sudo yum-config-manager --add-repo https://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo 
```
![2.jpg](https://i.loli.net/2020/04/04/3vcSI5EkyA9eUBb.png)

### 3.安装docker-ce
```
sudo yum install docker-ce -y
```
![3.jpg](https://i.loli.net/2020/04/04/47OFPsnkzQf8mYi.png)

### 4.启动docker-ce
```
sudo systemctl enable docker
sudo systemctl start docker
```
![4.jpg](https://i.loli.net/2020/04/04/oCAXhH5c29gslkf.png)
![5.jpg](https://i.loli.net/2020/04/04/KpNdAUGEXtOPBkT.png)

### 5.查看docker版本
```
docker version
```
![6.jpg](https://i.loli.net/2020/04/04/7yNZgwFCJphHkqO.png)

### 6.搜索镜像
```
docker search nginx
```
![7.jpg](https://i.loli.net/2020/04/04/PDQdN9jqha85UV6.png)

### 7.拉取镜像
```
docker pull nginx
```
![docker_pull_nginx.jpg](https://i.loli.net/2020/04/04/5zWG2eNRiLrYZMy.png)

### 8.查看镜像
```
docker images
```
![docker_images.jpg](https://i.loli.net/2020/04/04/aErW9Vbl78xsXzK.png)

### 9.接下来就不截图了，和命令是一样的。
```
# 启动nginx容器,-p映射端口,-d守护式进程,将nginx容器的静态目录挂载到主机目录，方便修改，要确保主机确实有该目录和文件。目录： /opt/docker-nginx/html,文件：/opt/docker-nginx/nginx.conf
docker run -p 80:80 -v /opt/docker-nginx/html:/usr/share/nginx/html -v /opt/docker-nginx/nginx.conf:/etc/nginx/nginx.conf -d nginx

# 然后想修改静态界面，就去/opt/docker-nginx/html目录下更改，想修改配置文件，就去/opt/docker-nginx/nginx.conf修改就行了。
```

### 10.界面展示
![10hours.png](https://i.loli.net/2020/04/04/xOrWSQfjmFdHBXq.png)
网站地址：[10hours.cn](http://10hours.cn)  
这是我调用printf520网站提供的接口，展示各个媒体的热榜。

