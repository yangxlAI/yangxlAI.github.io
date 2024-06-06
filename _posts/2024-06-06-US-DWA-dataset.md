---
layout: post
title: 课程大纲与工作技能评分论文与数据
date: 2024-06-06 08:57:00-0400
description: A national longitudinal dataset of skills taught in U.S. higher education curricula 
tags: 教育,数据集,就业
categories: 教育
giscus_comments: true
related_posts: false
---


论文： A national longitudinal dataset of skills taught in U.S. higher education curricula  
链接： https://arxiv.org/abs/2404.13163   
数据(18G)链接： https://figshare.com/articles/dataset/A_national_longitudinal_dataset_of_skills_taught_in_U_S_higher_education_curricula/25632429

研究团队通过自然语言处理技术从超过三百万份课程大纲中提取了工作场所活动（DWAs），这些DWAs是按美国劳工部（DOL）的职业分类来描述的。研究的目的是为了填补高等教育中技能发展的详细记录与工作市场需求之间的空白。

{::nomarkdown}
{% assign jupyter_path = "assets/jupyter/dwa_load_datasets.ipynb" | relative_url %}
{% capture notebook_exists %}{% file_exists assets/jupyter/dwa_load_datasets.ipynb %}{% endcapture %}
{% if notebook_exists == "true" %}
{% jupyter_notebook jupyter_path %}
{% else %}

<p>Sorry, the notebook you are looking for does not exist.</p>
{% endif %}
{:/nomarkdown}

Note that the jupyter notebook supports both light and dark themes.
