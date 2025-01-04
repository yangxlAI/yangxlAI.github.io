---
layout: post
title: 将HF模型转GGUF格式用于Ollama
date: 2025-01-04 08:57:00-0400
description: 如题
tags: NLP
categories: NLP
toc:
  sidebar: left
---


# 将hugginface里的模型转成 GGUF



来源 https://github.com/ggerganov/llama.cpp/discussions/2948

1、 下载 llama.cpp 代码

```
git clone https://github.com/ggerganov/llama.cpp.git
```

创建环境， 安装

```
pip install -r llama.cpp/requirements.txt
```

2、 下载模型

2025年1月， 使用  https://hf-mirror.com/ 下载模型


3、 转换

转换命令如下：
```
python convert_hf_to_gguf.py /root/autodl-tmp/models/Llama3-8B-Chinese-Chat-merged --outfile /root/autodl-tmp/models/Llama3-8B-Chinese-Chat-GGUF/Llama3-8B-Chinese-Chat-q8_0-v1.gguf --outtype q8_0
./llama-quantize ./新模型路径/新模型名.gguf  ./输出路径/4位gguf格式文件名.gguf Q4_K_M 采用4位  如果8位就Q8_K_M
--outtype f16 (16 bit) or --outtype f32 (32 bit) 
```

4、 ollama 使用

https://github.com/ollama/ollama?tab=readme-ov-file#import-from-gguf 

4.1 创建  Modelfile文件 里面写上 `FROM ./vicuna-33b.Q4_0.gguf`  
4.2 `ollama create model_name -f Modelfile`  
4.3 `ollama run model_name`  