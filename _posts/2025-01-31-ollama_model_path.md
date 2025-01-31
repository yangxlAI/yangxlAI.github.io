---
layout: post
title: Ollama下载模型路径存储位置及权限
date: 2025-01-31 08:57:00-0400
description: 如题
tags: NLP
categories: NLP
toc:
  sidebar: left
---

根据网络上的建议，在ubuntu系统里， 我已经完成了以下内容

# 1 配置文件

创建配置文件：

/etc/systemd/system/ollama.service.d/override.conf

内容:

```
[Service]
Environment="OLLAMA_MODELS=/mnt/share/ollama_models"
```

df -h 可得：
```
/dev/nvme0n1p1  3.6T  103G  3.3T   3% /mnt/share
```

运行
```
sudo systemctl daemon-reload
sudo systemctl restart ollama
sudo systemctl status ollama
```

# 出现错误

检查问题， 使用 ` journalctl -xe`

错误内容显示为：

```
1月 31 12:01:40 4x3090 ollama[3094883]: Error: mkdir /mnt/share/ollama_models: permission denied
```

# 分析错误

permission denied 是明显的 **权限错误**

查看ollama程序的执行用户， 我习惯使用 `ps aux | grep ollama`， 得到 用户名 ollama：
```
ollama   3095129  0.1  0.0 19697324 63576 ?      Ssl  12:02   0:01 /usr/local/bin/ollama serve
```



再查看路径的执行权限， 从 /mnt,/mnt/share,/mnt/share/ollama_models 每层看下来：

/mnt 一般不影响 
`
drwxr-xr-x   6 root root       4096 7月  26  2024 mnt
`

/mnt/share 的结果
```
drwxrwx--- 9 root sharegroup 4096 1月  31 11:44 share
```

因此使用
`sudo usermod -a -G sharegroup ollama`

*后续步骤不确定是否多余*

创建 /mnt/share/ollama_models， 查看权限， 我已经修改
```
drwxrwxrwx 3 ollama ollama      4096 1月  31 12:02 ollama_models
```

执行的命令为以下两条：
```
sudo chown -R ollama:ollama /mnt/share/ollama_models    # 修改用户
sudo chmod -R 755  /mnt/share/ollama_models      # 修改权限， 别人用的是755， 用777 好像太放开了~
```

