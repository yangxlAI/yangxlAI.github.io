---
layout: post
title: docker GPU报错
date: 2025-02-02 08:57:00-0400
description: 如题
tags: docker
categories: 开发工具
toc:
  sidebar: left
---

# 报错 GPU
docker 报错, 带 `--gpus`时报错， 不带该参数使用CPU不报错

```
docker: Error response from daemon: could not select device driver "" with capabilities: [[gpu]].
```

deepseek回答要安装 **NVIDIA Docker工具包**

现链接如下

https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html

需要安装 cuda\cudatoolkit， cuda安装 有点混乱， cudatoolkit安装方案也不少， 比如 anaconda就可以

# 报错 libnvidia-ml.so.1

前面安装正常， 有些docker镜像正常， 但有的失败， 报错 `load library failed: libnvidia-ml.so.1: cannot open shared object file`

查询到 https://github.com/NVIDIA/nvidia-container-toolkit/issues/305 链接，最后一层， 建议重装

just reinstalling docker-ce using sudo apt-get install --reinstall docker-ce 

# A100的nv-fabricmanager

不敢动~ 所以没试出方案。

另外， 个人所购服务器 启动docker极快， 该服务器明明更强，但很慢，原因不明。