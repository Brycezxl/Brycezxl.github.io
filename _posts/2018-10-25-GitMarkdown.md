---
title: Markdown语法(Github)
categories:
 - 新手村
tags:
 - 新手村
---

简单记录了github里一些基本的markdown语法， markdown用不好怎么写博客！

<!--more-->

***

## 0. 标题

`##` 大标题

`###` 小标题

`####` 超小标题

超大标题  等于号写于文字下方

` === `

标题  同超大标题

` --- `

***

## 1. 行内代码

' abc '

***
## 2. 引用

### A. 竖线

`>` + 空格 + 某一行

> 效果

### B. 高亮

两个tab

    效果

***

## 3. 排序

### A. 无序列表

书写方式： `(*、-、+)` + 空格 + 内容

### B. 有序列表

`1. 第一行`

`1. 第二行`

`1. 第N行`

***

## 4. 分割线

### A. 分隔符

`---` 或 `***`

### B. Table

First Header `|` Second Header

------------ `|` -------------

Content from cell 1 `|` Content from cell 2

Content in the first column `|` Content in the second column

First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column

***

## 5. 强调

### A. 加粗

`*`字`*`  *或*  `_`字`_`

### B. 斜体

`**`字`**` **或** `__`字`__`

### C. 高亮

倒引号　＋　字　＋　倒引号

`不灵不灵`

### D. Text自带

文本下面一行写：

`{:.success/info/warning/error}`

success.
{:.success}

info.
{:.info}

warning.
{:.warning}

error.
{:.error}

### E. Tag

`tag` `{:. + 同上 }`

***

## 6. 外部引用

### A. 超链接

`[`标题`]``(`路径`)`

### B. 图片

！`[`标题`]``(`路径`)`

### C. 直接显示超链接

`<`内容`>`

***
