---
layout: post
title: nvidia-Docker安装与使用
category: 技术
tags: nvidia-docker
keywords: nvidia-docker
description: nvidia-docker安装与使用
---

## 安装
1. 安装docker-ce（请参照另外一篇文章）
2. 安装nvidia驱动
到官网查找对应驱动版本，sudo apt-get install nvidia-ver安装
a. 禁用nouveau驱动
```
sudo vim /etc/modprobe.d/blacklist-nouveau.conf
内容如下
blacklist nouveau
option nouveau modeset=0
```
3. 安装cuda(tensorflow等需要)
下载cuda-9.0 和cudnn安装

4. sudo nvidia-docker run -it --name myts -v /data/tensorflow/notebooks -p 8888:8888 -p 6006:6006 tensorflow/tensorflow:latest-gpu 下载运行docker镜像