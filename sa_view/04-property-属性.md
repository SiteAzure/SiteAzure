---
layout: single # 必填，使用的layout
title: 属性 # 必填，页面名字
description: ViewBag、CurrentSite # 必填，页面介绍
permalink: /property/ # 必填，页面链接地址
# page_author: Zen # 非必填，本页作者
---

* content
{:toc}

### 页面属性


``` csharp
@ViewBag.***
```


| 调用 | 说明 | 默认取值 |
| ------------ | ------------ | ------------ |
| ``@ViewBag.PageTitle`` | 页面标题	| 首页：站点标题 <br/> 节点：节点名称[_父节点名称][_祖先节点名称]_站点标题 <br/> 内容：内容标题_节点名称[_父节点名称][_祖先节点名称]_站点标题 |
| ``@ViewBag.MetaKeywords``	 | META关键词 | 	首页：站点META关键词节点<br>站点META关键词 <br> 内容：内容关键词 |
| ``@ViewBag.MetaDescription``	 | META网页描述   |  首页：站点META网页描述<br> 节点：站点META网页描述 <br> 内容：内容简介，如果内容简介为空则使用内容标题 |

### 站点属性

``` csharp
@CurrentSite.Instance.***
```

| 调用 |说明 | 默认取值 |
| ------------ | ------------ | ------------ |
| ``@CurrentSite.Instance.SiteTitle``| 站点标题 | |
| ``@CurrentSite.Instance.LogoUrl``	| 站点LOGO地址 | |
| ``@CurrentSite.Instance.Copyright`` | 站点版权信息 | 版权信息支持HTML代码，直接输出HTML代码使用``@Html.Raw(CurrentSite.Instance.Copyright)`` | 


### Request


| 调用 |说明 | 默认取值 |
| ``@Request.QueryString["keyword"]`` | 获取请求中的``keyword``参数的值 |
|||
