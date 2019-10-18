[TOC]

## [Docker 安装](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

```
#安装前必须执行，否则会出现安装错误
sudo apt-get update
sudo apt-get upgrade

#安装方式一
sudo apt-get install docker-ce docker-ce-cli containerd.io

#安装方式二
apt-get install -y curl
curl -sSL https://get.docker.com/|sudo sh

sudo docker run hello-world

#卸载
apt-get remove -y docker-*
https://blog.csdn.net/Fly_hps/article/details/89760931

#删除安装文件

	#查找docker安装路径
	docker info | grep "Data loop file"

	卸载时将该目录下的所有文件删除(/var/lib/docker)

docker version
```



## 问题

> Cannot connect to the Docker daemon at unix:///var/run/docker.sock. Is the docker daemon running?
>
> Process: 13561 ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock (code=exited, status=1/FAILURE)

[解决方案](http://www.docker.org.cn/thread/72.html)

> 修改/etc/docker/daemon.json文件，并将内容修改为：
>
> {                      
>
>    "storage-driver" : "devicemapper"
> }





## ubuntu 配置阿里源

```text
vim /etc/apt/sources.list

deb http://mirrors.aliyun.com/ubuntu/ xenial main
deb-src http://mirrors.aliyun.com/ubuntu/ xenial main

deb http://mirrors.aliyun.com/ubuntu/ xenial-updates main
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates main

deb http://mirrors.aliyun.com/ubuntu/ xenial universe
deb-src http://mirrors.aliyun.com/ubuntu/ xenial universe
deb http://mirrors.aliyun.com/ubuntu/ xenial-updates universe
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-updates universe

deb http://mirrors.aliyun.com/ubuntu/ xenial-security main
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security main
deb http://mirrors.aliyun.com/ubuntu/ xenial-security universe
deb-src http://mirrors.aliyun.com/ubuntu/ xenial-security universe
```

## 什么是Docker Machine ？

- Docker Machine 是官方提供的一个管理工具，帮助我们在远程机器上安装docker。
- Docker Machine远程安装的前提是：**所有机器必须配置ssh免密码登录。**



## Docker Machine 安装

```
 base=https://github.com/docker/machine/releases/download/v0.16.0 &&
  curl -L $base/docker-machine-$(uname -s)-$(uname -m) >/tmp/docker-machine &&
  sudo mv /tmp/docker-machine /usr/local/bin/docker-machine &&
  chmod +x /usr/local/bin/docker-machine
```

>  docker-machine version

[官方安装文档](https://docs.docker.com/machine/install-machine/)

## Docker Compose 安装

```
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
```

```
sudo chmod +x /usr/local/bin/docker-compose
```

```
docker-compose --version
```



[官网地址](https://docs.docker.com/compose/install/)

## Ubuntu安装Virtualbox 

- 安装Virtualbox

  > sudo dpkg -i virtualbox-6.0_6.0.12-133076~Ubuntu~bionic_amd64.deb 

- 修复缺少的依赖包

  > sudo apt-get install -f
  >
  > -f 参数是修复依赖关系（depends），假如用户的系统上有某个package不满足依赖条件，就会自动修复，安装程序包所依赖的包。

- [VirtualBox下载地址](https://www.virtualbox.org/wiki/Linux_Downloads)



## 参考文章

1. [docker machine介绍和使用-经典](https://www.jianshu.com/p/cc3bb8797d3b)


