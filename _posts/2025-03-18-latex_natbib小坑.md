---
layout: post
title: Latex natbib引用包的小坑
date: 2025-03-18 08:57:00-0400
description: 如题
tags: 写作
categories: 开发工具
toc:
  sidebar: left
---

# natbib

```
\usepackage[numbers]{natbib}     
```

author-year太长， numbers 报错 Latex Error: Option clash for package natbib 

大模型答不上来， 自行查到

https://tex.stackexchange.com/questions/367391/option-clash-for-package-squarenatbib


```
\usepackage{natbib}
\setcitestyle{square, comma, numbers,sort&compress, super}
```
