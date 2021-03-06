---
layout:     post
title:      定时器 你真的会使用吗？
subtitle:   iOS定时器详解
date:       2016-12-13
author:     BY
header-img: img/post-bg-ios9-web.jpg
catalog: 	 true
tags:
    - Html
---
## display
##### 内联元素不支持内容区宽高的设置，为了能设置内联元素可见框的大小，可将内联元素转换为块元素显示------display
##### display可设置元素的类型
- 可选值：
  - inline  将当前元素设置为内联元素  不会独占一行
  - block   将当前元素设置为块元素   可设置宽高
  - inline-block 将当前元素设置为行内块元素
    - 行内块元素，既有内联元素的特点，不会独占一行，又有块元素的特点可设置元素的宽高
    - none  元素不会在页面中显示，也不会占据位置

## visibility
##### visibility设置元素是否可见
- 可选值：
  - visible，默认值元素在页面中正常显示
  - hidden，元素不在页面中显示，但是依然占据页面的位置
  - collapse，元素不在页面中显示，但是依然占据页面的位置


## overflow
##### overflow可设置父元素如何处理内容溢出问题
- 可选值：
    - visible默认值，不对溢出内容做任何处理，溢出内容会在父元素以外的地方显示
    - hidden溢出父元素的内容将会被裁剪不会在页面中显示
    - scroll默认添加水平和垂直方向的滚动条通过滚动条查看内容
      - 但是无论内容是否溢出都会产生双方向的滚动条 
    - auto根据需要产生滚动条

## 文档流
- 文档流是网页的最底层，也可以说他是网页的基础部分，我们创建的元素默认都是在文档流中排列
- 元素在文档流中的特点
   - 块元素：
     1. 块元素在文档流中会自上向下垂直排列
     2. 块元素在文档流中默认宽度是父元素的100%
     3. 块元素在文档流中默认高度由内容撑开
   - 内联元素：
     1. 内联元素在文档流中会自左向右水平排列
        - 如果一行不足以容纳所有元素，则会另起一行继续自作向右排列（与书写规范一样）
     2. 内联元素在文档流中宽度和高度默认都是被内容撑开

##### float
- 可通过设置元素的属性float来设置元素的浮动
- 可选值：
  - none 元素没有浮动，还处于文档流中
  - left 元素向左浮动
  - right 元素向右浮动
- 浮动的特点：
  1. 设置浮动后，元素会完全脱离文档流，并且向页面的左上或者右上移动
  2. 设置浮动后，元素下面的元素会向上移动
  3. 元素浮动时，在遇到父元素或兄弟元素的边框时会停止浮动
  4. 如果上面是一个没有浮动的块元素，则浮动元素不会超过那个元素
  5. 如果一行不足以容纳所有的元素，则元素会自动换到下一行

##### 脱离文档流的特点
- 块元素脱离文档流后不再独占一行
- 块元素脱离文档流后，宽度和高度默认都是被内容撑开(块元素在文档流中的特点是宽度默认为父元素的100%)
- 内联元素脱离文档流后，会变成块元素，和块元素的特点一致

##### 高度塌陷
- 父元素在默认情况下，高度时被子元素撑开的，当子元素浮动以后，它就会完全脱离文档流，无法撑起父元素的高度，导致父元素的高度丢失
- 父元素高度塌陷以后，它后面的元素会向上移，从而导致页面布局混乱
- 解决：
   1. 设置父元素的高度足以撑起自己---------不灵活
   2. 开启元素的BFC模式（blocking formatting context）
    - bfc是元素的隐藏属性，默认是关闭的
    - 开启方法：
      1. 设置元素浮动
      2. 设置元素绝对定位
      3. 将元素的display设置为inline-block
      4. 将元素的overflow设置为一个非visible的值
      我们一般通过设置overflow=hidden来开启元素的BFC，从而解决高度塌陷问题
    - 开启BFC后元素拥有以下特点：
      1. 子元素的外边距不会传递给父元素
      2. 开启BFC的元素不会被浮动元素所覆盖
      3. 开启BFC的父元素可以包含子元素
                   
