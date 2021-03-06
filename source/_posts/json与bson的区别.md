title: json与bson的区别
author: LanGaoBai
author_id: defaultAuthorId
language: zh-CN
tags:
  - JSON
  - BSON
categories:
  - 数据格式
date: 2018-03-10 18:56:00
---
### 简介
bson是由10gen开发的一个数据格式，目前主要用于mongoDB中，是mongoDB的数据存储格式。bson基于json格式，选择json进行改造的原因主要是json的通用性及json的schemaless(无模式)的特性。

### bson主要方向

#### 更快的遍历速度

对json格式来说，太大的json结构会导致数据遍历非常慢。在json中，要跳过一个文档进行数据读取，需要对此文档进行扫描才行，需要进行麻烦的数据结构匹配，比如括号的匹配。 

而bson对json的一大改进就是，它会将json的每一个元素的长度存在元素的头部，这样你只需要读取到元素长度就能直接seek到指定的点上进行读取了。

#### 操作更简易

对json来说，数据存储是无类型的，比如你要修改基本一个值，从9到10，由于从一个字符变成了两个，所以可能其后面的所有内容都需要往后移一位才可以。 

而使用bson，你可以指定这个列为数字列，那么无论数字从9长到10还是100，我们都只是在存储数字的那一位上进行修改，不会导致数据总长变大。 

当然，在mongoDB中，如果数字从整形增大到长整型，还是会导致数据总长变大的。

#### 增加了额外的数据类型

json是一个很方便的数据交换格式，但是其类型比较有限。 

bson在其基础上增加了“byte array”数据类型。这使得二进制的存储不再需要先base64转换后再存成json，大大减少了计算开销和数据大小。 

当然，在有的时候，bson相对json来说也并没有空间上的优势，比如对{“field”:7}，在json的存储上7只使用了一个字节，而如果用bson，那就是至少4个字节（32位）


目前在10gen的努力下，bson已经有了针对多种语言的编码解码包。并且都是*Apache2 license*下开源的。并且还在随着mongoDB进一步地发展。

### json与bson对比
#### 数据结构

json是像**字符串存储**的，bson是按**结构存储**的（像数组 或者说struct）

#### 存储空间 

bson>json

#### 操作速度 

bson>json。比如，遍历查找：json需要扫字符串，而bson可以直接定位

#### 修改 

json也要大动大移，bson就不需要。

在大多数情况下，JSON和BSON非常相似，但BSON可以提供额外的速度冲击。当然，两者都是应用程序存储和检索数据非常方便的方法。

> 转自[张山的博客专栏](http://blog.csdn.net/xiaojin21cen/article/details/60953980)