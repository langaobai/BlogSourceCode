title: MongoDB
author: LanGaoBai
author_id: defaultAuthorId
language: zh-CN
tags:
  - MongDB
  - BSON
categories:
  - MongDB
date: 2018-03-10 18:07:00
updated: 2018-03-11 09:59:00
---

### 介绍

最近学习到React-Native，需要学习一下Facebook推出的f8app例子；

> MongoDB介绍

MongoDB 是一个基于分布式文件存储的数据库。由**C++语言编写**。**旨在为WEB**应用提供可扩展的高性能数据存储解决方案。

MongoDB **是一个介于关系数据库和非关系数据库之间的产品**，是非关系数据库当中功能最丰富，最像关系数据库的(*听着像小品界最会唱歌的小沈阳*)。他支持的数据结构非常松散，是类似json的bson(**Binary Serialized Document Format**)**是一种二进制形式的存储格式**，因此可以存储比较复杂的数据类型。

Mongo最大的特点是他支持的查询语言非常强大，**其语法有点类似于面向对象的查询语言**，几乎可以实现类似关系数据库单表查询的绝大部分功能，而且还支持对数据建立索引。

这里不得不说一下，其实他是NoSQL(NoSQL = Not Only SQL,意即“不仅仅是SQL”)数据库的一种。

扩展一下，HBase数据库也是NoSQL的一种。

> 特点

1. 支持RUBY，PYTHON，JAVA，C++，PHP，C#等多种语言。
2. 文件存储格式为BSON（一种JSON的扩展）。[JSON与BSON](http://blog.langaobai.top/2018/03/10/json与bson的区别/)
3. 可通过网络访问。


此处抄于百度词条，如果有错，不要找我...

### 安装

而其中需要用到MongDB，我下载的是3.6版本的，需要下载的请点击[MongoDB](https://www.mongodb.com/download-center#atlas)

一路点击<kbd>Next</kbd>就可以了，当然前提是你知道你要安装在什么地方。

直达最后，安装界面提示你，可能要花些时间，但是这个时间很说不准，万一卡了呢，那么你只能关闭了，不过不要担心，下次开机的时候，其实你已经安装好了，不行你就再装一遍。

### API学习

安装好以后，我们就该学习了，[MongoDB API](https://docs.mongodb.com/)

未完待续...

