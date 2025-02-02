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

docker 报错, 带 `--gpus`时报错， 不带该参数使用CPU不报错

```
docker: Error response from daemon: could not select device driver "" with capabilities: [[gpu]].
```

deepseek回答要安装 **NVIDIA Docker工具包**

现链接如下

https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html

需要安装 cuda\cudatoolkit， cuda安装 有点混乱， cudatoolkit安装方案也不少， 比如 anaconda就可以

写完收工。
