---
layout: single # 必填，使用的layout
title: 技巧 # 必填，页面名字
description: 助你一飞冲天 # 必填，页面介绍
permalink: /tips/ # 必填，页面链接地址
# page_author: Zen # 非必填，本页作者
---

* content
{:toc}

### 字符串插值 {#String-Interpolation}

模板标签中支持C# 6.0的语法，其中字符串插值（String Interpolation）特性可以方便的用来进行字符串的拼接。基本的用法为字符串前加上$符号，字符串中的动态值使用{}大括号括起来。

``` html
// 普通拼接字符串
linkTitle1 = "标题：" + Model.Title + "\r\n点击数：" + Model.Hits + "\r\n发表时间：" + Model.PublishTime.ToString("yyyy-mm-dd");

// 字符串插值方式
linkTitle2 = $"标题：{Model.Title}\r\n点击数：{Model.Hits}\r\n发表时间：{Model.PublishTime.ToString("yyyy-mm-dd")}";
```

### 条件属性 {#condition}

Razor引擎会根据属性是否是null值或者布尔值来呈现Html元素中的属性，如果属性为null值则属性本身不会呈现出来，如果属性是布尔型值，同样也会根据值是true或false来呈现相应的值或者不呈现。

```html
@{
    string red = "red";
    string green = "";
    string blue = null;

    bool enable = true;
    bool active = false;
}
<div class="@red"></div>
<div class="@green"></div>
<div class="@blue"></div>
<input type="checkbox" name="abc" checked="@enable" />
<input type="checkbox" name="def" checked="@active" />
```

生成的Html：

``` html
<div class="red"></div>
<div class=""></div>
<div></div>
<input type="checkbox" name="abc" checked="checked" />
<input type="checkbox" name="def" />
```
**注意：**
>如果值为空字符串（”“），属性也是会呈现出来，虽然未指定值。


## 待续



