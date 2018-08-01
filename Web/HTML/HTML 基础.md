
## 2 什么是 HEAD 标签？ 


* 作用是包含一些页面元数据、标题、CSS JS 链接等页面信息。
* 特点是其内容不会再浏览器中显示。


**HEAD 中包含的内容及其主要功能如下：**

### 2.1 为页面设置标题

	<title>My test page</title>
	
	

### 2.2 HTML 中的元数据 &lt;meta&gt;  元素

元数据就是描述数据的数据。HTML 元数据是作为 HTML **页面的级别** 的元数据的存在。 HTML有一个“官方的”方式来为一个**文档**添加元数据，——  	&lt;meta&gt; 元素.

例如指定字符集：

	<meta charset="utf-8"> 

或者你也可以指定你自己的元数据
	
	<meta name="mx-title" content="特殊标题"> 

	
	
许多 &lt;meta&gt; 元素包含了name 和 content 特性:

* name 特性指定了meta 元素的类型; 说明该元素包含了什么类型的信息。
* content 指定了实际的元数据内容。



一些常用的元数据包括：

* 添加作者和描述:

		<meta name="author" content="Chris Mills">
		
		
* 对于 name 为 description 的 meta 元素中的数据将会被搜索引擎用于显示在搜索列表。
		
		<meta name="description" content="The MDN Learning Area aims to provide complete beginners to the Web with all they need to know to get started with developing web sites and applications.">
		
	
### 2.3 点自定义图标

通常会以一个16x16像素的 ico 格式的图片作为一个网站的图标，显示在浏览器标签上。

图片的格式也可以是 png 和 jpg 但是 ico 格式的兼容性最好，甚至包括 IE6。


	<link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
	
	
### 2.4 在 HTML 中使用 CSS 和 JavaScript

使用 link 和 script 元素引入 样式和 js。


### 2.5 为文档设置主语言

	<html lang="en-US">

### 2.6 &lt;base&gt; 元素

	<base> 标签描述了基本的链接地址/链接目标，该标签作为HTML文档中所有的链接标签的默认链接:


	

## 3 HTML 文字处理基础

HTML 的主要工作就是编辑文本结构和文本内容，以便在浏览器上正确的显示。本章介绍了适用于文本的不同结构元素。


文档结构化的意义相当明显，未经结构化处理的一段文本，被浏览器处理后将编程一大段只包含空格的文本内容，根本没有可读性。而经过结构化的文本则会被浏览器正确的显示。在结构化的同时还要尽可能的语义化。以便当我们看到这个结构就能大概明白这段文本的显示结果。

接下来是一些基本元素的介绍，就不再列举了。



## 4 超链接

超链接非常重要 ——它们使互联网成为一个互联的网络。

## 5 高级文字格式

## 6 文档与网站构架

**总结：**

**就整理目标来说，这一部分确实是基础的东西，虽然所有的东西都用过，也都看过，但是当把所有东西放在一起来讲时，便是系统化体现。**

**HTML 首先是简单的简单的结构化文本文档。其复杂性便在于如何更优美的实现结构化和语义化。由此延伸出来的学习目标便是从 HTML 的网页结构框架开始，逐个 HTML 网页的所有结构组成，最终使用这些语义化的结构任意的构建自己的网站。**







