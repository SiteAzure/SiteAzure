---
layout: single # 必填，使用的layout
title: 规范 # 必填，页面名字
description: 统一约束的模板、标签的书写规范 # 必填，页面介绍
permalink: /guideline/ # 必填，页面链接地址
# page_author: Zen # 非必填，本页作者
---

* content
{:toc}

- 统一使用 javascript:; 作为空链接以方便检查。
- 视图中尽可能不要包含javascript脚本代码或者html元素中的内联javascript代码。如果可能则应该提取成非介入式的js调用方式，或者提取成单独的js文件。

