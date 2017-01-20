---
layout: single # 必填，使用的layout
title: 方法 # 必填，页面名字
description: 内置的Power方法 # 必填，页面介绍
permalink: /method/ # 必填，页面链接地址
# page_author: Zen # 非必填，本页作者
---

* content
{:toc}



### 生成URL的方法

| 调用  | 说明 |
|------------------|------------------|
| `@Power.Url.NodeUrl("节点标识符")` |	通过节点标识符生成节点的Url地址|
| `@Power.Url.SubjectCategoryUrl("主题标识符")` |	通过主题标识符生成节点的Url地址|
| `@Power.Url.SiteUrl("站点子域名")` |	通过站点子域名生成站点的Url地址|

### 输出包含链接的节点名称

- 根据指定的节点标识符输出包含链接的节点名称，链接的打开方式从节点设置中取值，生成的HTML结构（节点设置为新窗口打开）类似：`<a href="/tzgg" target="_blank">通知公告</a>`   
``` html
@Power.Url.NodeLink("tzgg")
```

- 根据指定的节点标识符输出包含节点链接的指定文字，链接的打开方式从节点设置中取值，生成的HTML结构（节点设置为原窗口打开）类似：`<a href="/tzgg">更多</a>`
``` html
`@Power.Url.NodeLink("tzgg", "更多")
```	

- 根据指定的节点标识符输出包含链接的节点名称，如果未指定target属性则链接的打开方式从节点设置中取值，生成的HTML结构（节点设置为原窗口打开）类似：`<a href="/tzgg" class="more">更多</a>`
``` html
@Power.Url.NodeLink("tzgg", new { @class = "more" })
```

- 根据指定的节点标识符输出包含节点链接的指定文字，如果未指定target属性则链接的打开方式从节点设置中取值，生成的HTML结构类似：`<a href="/tzgg" class="more" target="_blank">更多</a>`
``` html
@Power.Url.NodeLink("tzgg", "更多", new { @class = "more", target="_blank" })
```

- 根据指定的节点输出包含链接的节点名称，链接的打开方式从节点设置中取值，生成的HTML结构（节点设置为新窗口打开）类似：`<a href="/tzgg" target="_blank">通知公告</a>`
``` html
@Power.Url.NodeLink(Node)
```

- 根据指定的节点输出包含节点链接的指定文字，链接的打开方式从节点设置中取值，生成的HTML结构（节点设置为原窗口打开）类似：`<a href="/tzgg">更多</a>`
``` html
@Power.Url.NodeLink(Node, "更多")
```

- 根据指定的节点输出包含链接的节点名称，如果未指定target属性则链接的打开方式从节点设置中取值，生成的HTML结构（节点设置为原窗口打开）类似：`<a href="/tzgg" class="more">更多</a>`
``` html
@Power.Url.NodeLink(Node, new { @class = "more" })
```

- 根据指定的节点输出包含节点链接的指定文字，如果未指定target属性则链接的打开方式从节点设置中取值，生成的HTML结构类似：`<a href="/tzgg" class="more" target="_blank">更多</a>`
``` html
@Power.Url.NodeLink(Node, "更多", new { @class = "more", target="_blank" })
```



### 输出包含链接的信息公开主题名称

- 根据指定的主题标识符输出包含链接的主题名称，生成的HTML结构，类似：`<a href="/tzgg">通知公告</a>`
``` html
@Power.Url.SubjectCategoryLink("tzgg")	
```

- 根据指定的主题标识符输出包含主题链接的指定文字，生成的HTML结构，类似：`<a href="/tzgg">更多</a>`
``` html
@Power.Url.SubjectCategoryLink("tzgg", "更多")	
```

- 根据指定的主题标识符输出包含链接的主题名称，生成的HTML结构，类似：`<a href="/tzgg" class="more">更多</a>`
``` html
@Power.Url.SubjectCategoryLink("tzgg", new { @class = "more" })	
```

- 根据指定的主题标识符输出包含主题链接的指定文字，生成的HTML结构，类似：`<a href="/tzgg" class="more" target="_blank">更多</a>`
``` html
@Power.Url.SubjectCategoryLink("tzgg", "更多", new { @class = "more", target="_blank" })	
```

- 根据指定的主题输出包含链接的主题名称，生成的HTML结构，类似：`<a href="/tzgg" target="_blank">通知公告</a>`
``` html
@Power.Url.SubjectCategoryLink(Node)	
```

- 根据指定的主题输出包含主题链接的指定文字，生成的HTML结构，类似：`<a href="/tzgg">更多</a>`
``` html
@Power.Url.SubjectCategoryLink(Node, "更多")	
```

- 根据指定的主题输出包含链接的主题名称，生成的HTML结构，类似：`<a href="/tzgg" class="more">更多</a>`
``` html
@Power.Url.SubjectCategoryLink(Node, new { @class = "more" })
```	

- 根据指定的主题输出包含主题链接的指定文字，生成的HTML结构，类似：`<a href="/tzgg" class="more" target="_blank">更多</a> `
``` html
@Power.Url.SubjectCategoryLink(Node, "更多", new { @class = "more", target="_blank" })
```	



### 高亮当前节点
``` html
<a href="@Power.Url.NodeUrl(node.Identifier)" class="@Power.Focus(node.Identifier, "hover")">@node.NodeName</a>
```
**说明：**
- 高亮机制是判断“导航标识符集合``（ViewBag.NavigationIdentifier）``”中是否包含Focus方法的第一个参数中指定的标识符，如果是则输出第二个参数。
- 方法的第一个参数一般使用节点标识符（具有唯一性），内容管理模块会自动把当前页的所有父节点标识符加入到集合中，内容管理模块的视图中不需要初始化`ViewBag.NavigationIdentifier`。
- 方法的第一个参数也可以强制指定固定的字符串，站点首页的默认导航标识符为**`~/`**。
- 对于模块的功能页视图中因为导航标识符集合未初始化，需要手动初始化，在视图顶部代码区加入`ViewBag.NavigationIdentifier.Add(“abc”)`，其中`abc`为页面设计时需要高度的元素指定的标识符，通常为当前页所在菜单元素的标识符。
- 导航标识符集合初始化方法`ViewBag.NavigationIdentifier.Add`支持同一个视图加入多个导航标识符，以使页面中的多个元素高亮。



