---
layout: single # 必填，使用的layout
title: Razor视图引擎 # 必填，页面名字
description: Razor视图介绍 # 必填，页面介绍
permalink: /Razor/ # 必填，页面链接地址
# page_author: Zen # 非必填，本页作者
---

* content
{:toc}


### 什么是Razor
Razor 是一种允许您向网页中嵌入基于服务器的代码（Visual Basic 和 C#）的标记语法。

当网页被写入浏览器时，基于服务器的代码能够创建动态内容。在网页加载时，服务器在向浏览器返回页面之前，会执行页面内的基于服务器代码。由于是在服务器上运行，这种代码能执行复杂的任务，比如访问数据库。
Razor 基于 ASP.NET，它为 web 应用程序的创建而设计。它拥有传统 ASP.NET 标记的能力，但更易使用，也更易学习。

### Razor语法

Razor 使用的语法与 PHP 和 ASP 相似。
Razor：

``` csharp
<ul>
@for (int i = 0; i < 10; i++) {
<li>@i</li>
}
</ul>
```


### 如何工作
Razor 是一种简单的编程语法，用于在网页中嵌入服务器端代码。

Razor 语法基于 ASP.NET 框架，该框架是微软的 .NET 框架特别为 web 应用程序开发而设计的组成部分。

Razor 语法赋予您所有 ASP.NET 的能力，但是使用了简化过的语法，如果您是初学者，则更容易学习，如果您是专家，则更有利于提高生产力。

Razor 网页可被描述为带有两种内容的 HTML 页面：HTML 内容和 Razor 代码。

当服务器读取这种页面后，在将 HTML 页面发送到浏览器之前，会首先运行 Razor 代码。这些在服务器上执行的代码能够完成浏览器中无法完成的任务，比如访问服务器数据库。服务器代码能够在页面被发送到浏览器之前创建动态的 HTML 内容。从浏览器来看的话，由服务器代码生成的 HTML 与静态 HTML 内容没有区别。
使用 Razor 语法的 ASP.NET 网页拥有特殊的文件扩展名 cshtml（使用 C# 的 Razor 语法）或者 vbhtml（使用 VB 的 Razor）。

### 参考
- [介绍“Razor”— ASP.NET的一个新视图引擎](http://blog.joycode.com/scottgu/archives/2010/07/20/116030.joy)
- [Razor的@:和&lt;text&gt;语法](http://blog.joycode.com/scottgu/archives/2011/01/11/116330.joy)
- [Razor中的新@model关键字](http://blog.joycode.com/scottgu/archives/2011/01/05/116280.joy)
- [通过Razor实现布局](http://blog.joycode.com/scottgu/archives/2011/01/24/116371.joy)
- [使用Razor实现服务器端注释](http://blog.joycode.com/scottgu/archives/2011/01/26/116412.joy)
- [用Razor实现隐式和显式代码碎块](http://blog.joycode.com/scottgu/archives/2011/01/27/116475.joy)
- [Razor中的@helper语法](http://blog.joycode.com/scottgu/archives/2011/05/25/116617.joy)
- [使用 Razor 语法 (C#) 的 ASP.NET Web 编程简介](http://www.asp.net/web-pages/overview/getting-started/introducing-razor-syntax-c)
