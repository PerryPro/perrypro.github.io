---
layout: post
title: Ubuntu18.03+Docker+Tensorflow GPU版+Pycharm
subtitle:
tags: [tensorflow]
---    

简单叙述如何在docker中运行tensorflow,并通过Pycharm连接docker进行开发    

## 1.安装nvdia显卡驱动，不一定需要安装cuda，但可以通过安装cuda来自动安装显卡驱动    
## 2.安装docker     
## 3.设置docker镜像加速(可选，此步骤的目的是为了加快pull镜像的速度)    
具体可参考：https://www.runoob.com/docker/docker-mirror-acceleration.html
## 4.安装nvidia docker2
**注意** 根据nvidia docker的github页面以及我自己的实验，目前最新版本的docker已经原生支持nvidia gpu的调用，只需要在启动镜像时添加--gpus all参数即可。     
看似无需额外安装nvidia docker，但这种原生支持并不被Pycharm所支持，所以还是得安装nvidia docker2。
## 5.修改docker daemon的配置文件
```
sudo vim /etc/docker/daemon.json
```
将其内容改为
```
{
    "registry-mirrors":["https://registry.docker-cn.com"],
    "default-runtime": "nvidia",
    "runtimes": {
        "nvidia": {
            "path": "/usr/bin/nvidia-container-runtime",
            "runtimeArgs": []
        }
    }
}
```
## 6.重启daemon进程和docker服务
```
sudo systemctl daemon-reload
sudo systemctl restart docker
```
## 7.拉取tensorflow的镜像
执行
```
docker pull tensorflow/tensorflow:2.0.1-gpu-py3
```
## 8.运行tensorflow容器
```
docker run --rm -it tensorflow/tensorflow:2.0.1-gpu-py3 bash
```
可加上-v /example:/inner 将宿主机的/example文件夹挂载到容器的/inner,实现文件数据共享 
## 9.安装Pycharm Pro
## 10.配置Pycharm docker支持
