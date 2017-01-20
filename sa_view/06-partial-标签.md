---
layout: single # 必填，使用的layout
title: 标签 # 必填，页面名字
description: 标签介绍 # 必填，页面介绍
permalink: /partial/ # 必填，页面链接地址
# page_author: Zen # 非必填，本页作者
---

* content
{:toc}

## 通用标签调用 {#partialCommon}

``` csharp
@Power.Partial("PartialViewName", new { Parameter1 = 10, Parameter2 = true, Parameter3 = "abc" ... })
```

### 标签查找顺序

``` html
~/Views/[siteIdentifier]/[ModuleName]/Shared/[PartialViewName].cshtml
~/Views/[siteIdentifier]/Shared/[PartialViewName].cshtml
~/Views/_Common/[ModuleName]/Shared/[PartialViewName].cshtml
~/Views/_Common/Shared/[PartialViewName].cshtml
```

**举例：**

如果某个站点（标识符为`Education`）的某个节点列表页（属于内容管理模块`ContentManage`）中调用了名为**“文章列表”**的标签，则标签查找的顺序为：

``` html
~/Views/Education/ContentManage/Shared/文章列表.cshtml
~/Views/Education/Shared/文章列表.cshtml
~/Views/_Common/ContentManage/Shared/文章列表.cshtml
~/Views/_Common/Shared/文章列表.cshtml
```

> 可以将通用的标签放置在``~/Views/_Common/``下，通过在站点和模块目录创建同名的标签来达到相同的调用方式但在各站点或模块下不同的显示结果。
>
> 因为标签路径会进行缓存，新建、改名、删除标签文件时，不会按标签查找顺序重新查找而只会读取缓存中的路径，所以需要清空缓存后才会起作用。

### 标签参数

标签参数是指 ``new { Parameter1 = 10, Parameter2 = true, Parameter3 = "abc" ... }`` 大括号中指定的参数。


**说明**
- 标签参数是完全自定义的，建议使用英文单词或词组为参数命名。
- 标签参数在指定时与顺序无关，可任意排列前后顺序，参数间使用逗号分隔。
- 标签参数对于大小写不敏感，在调用参数赋值或者标签内部获取参数时大小写可以不一致，但建议使用大小写一致的方式并使用Pascal命名法。
- 标签文件中通过``ViewParams.ParameterName``来进行调用，如果是直接输出请使用``@ViewParams.ParameterName``方式调用。
- 标签参数赋值通常可以使用数值型、布尔型、字符串、枚举值等方式进行赋值。

### 扩展字段
可以通过`@Model.ExtendObject.***`的方式来调用扩展字段的值。


## 默认列表标签 {#partialList}

**说明**
- 使数据查询与HTML元素呈现分离。
- 标签文件中不需要写数据查询，全部通过列表标签调用方法的相关固定参数控制。
- 数据相关的参数是系统固定的，通过参数控制可以满足绝大部分的数据查询。
- 标签中仅包含列表输出的一个列表项（比如li）。
- 仍然可以传递其他参数来控制标签中的html元素或样式。

### 标签调用

|                   调用                      |               说明                            |
|---------------------------------------------|------------------------------------------------------------|
| ``@Power.ArticleList("列表标签名")``      | 调用文章列表标签，无控制参数，全部使用默认值，一般用于测试使用。 | 
| ``@Power.ArticleList("列表标签名", new {})`` | 调用文章列表标签，通过参数进行控制。 | 
| ``@Power.PhotoList("列表标签名")``       | 	调用图片列表标签，无控制参数，全部使用默认值，一般用于测试使用。 | 
| ``@Power.PhotoList("列表标签名", new {})``	 | 调用图片列表标签，通过参数进行控制。 | 
| ``@Power.VideoList("列表标签名")``	     	 | 调用视频列表标签，无控制参数，全部使用默认值，一般用于测试使用。 | 
| ``@Power.VideoList("列表标签名", new {})``	 | 调用视频列表标签，通过参数进行控制。 | 
| ``@Power.ContentList("列表标签名")``        | 	调用内容列表标签，无控制参数，全部使用默认值，一般用于测试使用。 | 
| ``@Power.ContentList("列表标签名", new {})`` | 	调用内容列表标签，通过参数进行控制。 | 

### 默认约定

- 列表标签显示的内容均为已审核的内容。
- 列表标签调用的站点均为已启用的站点。

### 标签数据查询参数

|    参数名    	|         参数类型       	| 参数类型         	|         	参数默认值         	|
|------------------|:---------------:|---------------------|------------------|
| Count    |	int       |   	显示的条数。     |	10     |
| Node	   |   string,node,int,int[] |	可以传递节点标示符，、节点实体、节   点id、节点id集合。 节点标示符支持多值传递 多值传递 。 具体参考 如何指定节点查询 。|	Null|
| Site| 	int,string	 | 可以使用siteid，以及站点标示符进行设置,或者采用 多值传递 的字符串。如果设置为 0 ，那么就不限制站点，会显示所有站点的数据。| currentSite 默认为当前站点。| 
| Keyword	| string| 	传递关键词。 文章支持模糊搜索标题、内容字段。 图片、视频、内容支持模糊搜索标题、简介字段。| 	Null| 
| Tag| 	string| 	传递标记名称，支持 多值传递。根据标签筛选数据。| 	Null| 
| DateRange| 	string| 	日期范围 | 	Null| 
| IncludeChildNodes （参数名待确认）|	bool	| 是否包含子节点中的数据。如果指定了多个节点，那么每个指定的节点都会包含其子节点的内容。| true| 
| Illustrated （参数名待确认）| bool | 是否只获取带有内容图片的数据。| false |
| RefNode （参数名待确认）	| bool | 是否包含引用节点。 | false <br/> 如果指定了多个节点，那么每个指定的节点都会包含其引用节点的内容。 |
| Sort | string |	排序字段， 默认使用倒叙排序，支持 多值传递 。	 | PublishTime。 |
| SortOrder	| string | 排序类型，支持 多值传递 。<br/>Asc 表述采用正序排序。<br/>Desc 采用倒叙排序。<br/>排序方式和排序字段一一对应，可以按照多个字段进行排序，参见 使用多字段排序 。| “Desc”|
| Interval   |	int	  |    间隔行数      |  |
| HighRank   |	int	  |    高排名行数     |  |
| Split      | int    |    分隔行数      |  |


- `@Row.Index` 行索引：整型，表示当前行数
- `@Row.PositionLiteral` 行位置文本：字符串，首行时值为`first`，尾行时值为`last`，其他行为`null`
- `@Row.IsInterval` 是否间隔行：布尔型，判断当前行是否为间隔行，通过间隔行数（`@Param.Interval`）来控制
- `@Row.IntervalLiteral` 间隔行文本：字符串，如果是间隔行，则值为`interval`，否则为`null`
- `@Row.IsHighRank` 是否高排名行：布尔型，判断当前行是否是高排名行，通过高排名行数（`@Param.HighRank`）来控制
- `@Row.HighRankLiteral` 高排名行文本：字符串，如果是高排名行，则值为`highrank`，否则为null
- `@Row.IsSplit` 是否分隔行：布尔型，判断当前行是否是分隔行，通过分隔行数（`@Param.Split`）来控制，如果当前行是尾行且正好分隔，那么此值仍然为否，即不在尾行处标识分隔行。



### 多值传递

可以采用，号分隔的方法传递多个参数。

例如传递多个节点标示符时可以使用 `Node="tpxw,spxw,dzyw" `。


### 日期范围

日期范围是以当前日期为基准点，查询某个时间范围段的内容。

- 1d 一天之内的内容。
- 1w 一周之内的内容。
- 1m 一个月之内的内容。
- 1y 1年之内的内容。

> **注意**
>
> 不能使用这种方式来获取年月日的点击数排行， 日期范围筛选的是文章的发布时间， 使用这种方式只能获取到例如今年发布的文章点击数排行前10， 而不是今年点击数前10的文章。


### 使用多字段排序 
在查询时可以根据多个字段进行排序，例如使用点击数和内容发布日期进行排序。
``` csharp
@Power.ArticleList("标准列表",new{ Node="news", Sort="Hints,PublishTime"});
```
也可以针对不同字段指定不同的排序。 例如指定使用**优先级倒叙**和**发布时间正序**
``` csharp
@Power.ArticleList("标准列表" ,new { Node="news" ,Sort="Priority,PublishTime",SortOrder="desc,asc"})
```
`SortOrder` 中的值和 `Sort` 中的一一对照。

### 如何指定节点查询
在查询时可以使用多种方式指定要查询的节点。

#### 指定节点id
``` csharp
@Power.ArticleList("标准列表" ,new{ Node=1 })
```

#### 指定多个节点id
``` csharp
@Power.ArticleList("标准列表" ,new{ Node=“[1,2]” })
```

#### 指定节点标识符
``` csharp
@Power.ArticleList("标准列表" ,new{ Node="jddt" })
```

#### 指定多个节点标识符
``` csharp
@Power.ArticleList("标准列表" ,new{ Node="jddt，news" })
```

#### 指定节点实体
``` csharp
@Power.ArticleList("标准列表" ,new{ Node=node })
```

>不建议设计师直接使用这个接口，一般开发人员在循环节点时采用此方式会有更好的性能。



### 用户故事

- 访问者可以查看当前站点下指定栏目的多条信息列表。
`@Power.ArticleList("标准列表",new{Node="jgdt",Count=7})`

- 管理员可以指定文章的优先级，访问者访问时按照优先级进行排序。
`@Power.ArticleList("标准列表",new{Node="jgdt",Sourt="Priority,PublistTime",Count=7})`

- 访问者可以看到当前站点下的最新的10条文章。
`@Power.ArticleList("标准列表")`

- 访问者可以三天之内的**最新公告**栏目下的内容列表，并按照优先级排序。
`@Power.ArticleList("标准列表",new{ Node="zxgg",DateRange="3d"})`

- 访问者在主页上查看所有的**友情链接**栏目下的**友情链接**
`@Power.ArticleList（"标准列表" ,new {Node="yqlj",Count=99,IncludeChildNodes=false})`

- 输入一个足够大的数量，显示全部内容。不显示子栏目下的内容。
访问者可以在主页上查看**首页热门缩略图**，管理员在后台标记**首页缩略图**的文章。
`@Power.ArticleList("幻灯片",new {Node="news",Tag="首页缩略图" ,Count=5,Illustrated=true})`

### 列表标签控制参数

| 参数名   | 参数类型 | 参数说明 | 参数默认值 |
|------------------|:---------------:|---------------------|------------------|
| Index   | int     | 当前行索引，索引值从1开始。	 |
| RowMark <br/>（参数名待确认）| string| 当前行的标志。 首行：first 中间各行：null（空） 尾行：last 只有一条数据，既是首行又是尾行：first last|	

> 为什么不能直接使用 `@Power.ArticleList("首页标签", new { Count = 10, Node = "zwdt, 21, zfgzpy" })` 来指定标示符是`zwdt,zfgzpy`，节点id是`21`。
>
> ——无法直接判断 21 是节点id ，因为节点标示符本身也可以是数字，例如使用某年的年份。 所以这里不能支持。 如果这样写， 那么将会查找标示符是21的节点。


## 站点类相关标签

待补充 


## 节点类相关标签

### 节点字段读取
待补充 

### 节点扩展字段
待补充 






