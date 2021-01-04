title: Emmet笔记
author: LanGaoBai
author_id: defaultAuthorId
language: zh-CN
tags:

  - 前端
  - HTML
categories:
  - HTML
  - 前端
date: 2020-05-04 09:52:00

---



最近又需要经常的使用emmet写html，但是好长时间不写了，突然忘记了很多，虽然简单，但是很多东西长时间不用，又给忘记了；

因此决定要写一下笔记，好记性不如烂笔头，多记录一下，以后方便自己也多查查；



### 嵌套运算符（Nesting Operator）

#### 子代操作符（Child）：>

```html
<!-- 递进的层级关系 -->
div>span>a
<!-- 生成如下html -->
<div><span><a href=""></a></span></div>
```

#### 兄弟操作符（Sibling）：+

```html
<!-- 同层级关系 -->
div>div+p
<!-- 生成如下html -->
<div>
    <div></div>
    <p></p>
</div>
```

#### 返回上级操作符（Climb-up）：^
```html
<!-- 返回上层级 -->
div>div+p^div
<!-- 生成如下html -->
<div>
    <div></div>
    <p></p>
</div>
<div></div>

div>div>div>p^^^div
<!-- 返回上三层 生成如下html -->
<div>
    <div>
        <div>
            <p></p>
        </div>
    </div>
</div>
<div></div>
```

#### 乘法操作符（Multiplication）：*
```html
<!-- 指定标签生成数量 -->
ul>li*5
<!-- 生成如下html -->
<ul>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
    <li></li>
</ul>
```

#### 分组操作符（Grouping）：()
```html
<!-- 组与层类比，需要使用（） -->
(header>h1+div>p)+(main>p)+(footer>ul>li*3)
<!-- 生成如下html -->
<header>
    <h1></h1>
    <div>
        <p></p>
    </div>
</header>
<main>
    <p></p>
</main>
<footer>
    <ul>
        <li></li>
        <li></li>
        <li></li>
    </ul>
</footer>

<!-- 例子 -->
div>(header>ul>li*2>a)+footer>p

<div>
    <header>
        <ul>
            <li><a href=""></a></li>
            <li><a href=""></a></li>
        </ul>
    </header>
    <footer>
        <p></p>
    </footer>
</div>
```

### 属性操作符（Attribute Operators）

#### ID 和 Class（ID and CLASS）


```html
<!-- ID用# Class用. 类似css样式和jQuery选择器 -->
div#header>p.news*3
<!-- 生成如下html -->
<div id="header">
    <p class="news"></p>
    <p class="news"></p>
    <p class="news"></p>
</div>
```

#### 定制属性（Custom attributes）


```html
<!-- 属性使用[] -->
a[target='' title='hello world']*3
<!-- 生成如下html -->
<a href="" target="" title="hello world"></a>
<a href="" target="" title="hello world"></a>
<a href="" target="" title="hello world"></a>
```

#### 数值计算操作符（Item numbering）：$

```html
<!-- $->指定数字 -->
div>ul>li.item-$*3
<!-- 生成如下html -->
<div>
    <ul>
        <li class="item-1"></li>
        <li class="item-2"></li>
        <li class="item-3"></li>
    </ul>
</div>

<!--使用任意个$在数字前加任意个0-->
<!-- ul>li.item$$*5 -->
<ul>
    <li class="item01"></li>
    <li class="item02"></li>
    <li class="item03"></li>
    <li class="item04"></li>
    <li class="item05"></li>
</ul>

<!--如果你想倒着写数值的话呢，可以在 $ 操作符后面再加上 @- -->
<!-- ul>li.item$@-*5 -->
<ul>
    <li class="item5"></li>
    <li class="item4"></li>
    <li class="item3"></li>
    <li class="item2"></li>
    <li class="item1"></li>
</ul>

<!--指定开始的序号，在$后面加@N，N为开始的序号-->
<!-- ul>li.item$@3*5 -->
<ul>
    <li class="item3"></li>
    <li class="item4"></li>
    <li class="item5"></li>
    <li class="item6"></li>
    <li class="item7"></li>
</ul>
```

#### 文本操作符（Text）：{}

```html
<!-- a{Click me} -->

<a href="">Click me</a>

```
