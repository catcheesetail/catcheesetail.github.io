---
layout:     post
title:      定时器 你真的会使用吗？
subtitle:   iOS定时器详解
date:       2016-12-13
author:     BY
header-img: img/post-bg-ios9-web.jpg
catalog: 	 true
tags:
    - ECMAScript5
---
## Date
##### Date的方法可以获取想要的时间
* var date=new Date();
* var year=date.getFullYear();
* var month=date.getMonth();
* var day=date.getDay();
* var hou=date.getHours();
* var min=date.getMinutes();
* var sec=date.getSeconds();
* var tim=date.getTime();
* var date2=new Date("12/15/2015 13:05:23")

##### Date时间戳，可以测试代码执行速度

```
	//利用时间戳测试代码执行速度
		var begin=Date.now();
		console.time("test")
		 for(var i=0;i<100000;i++){
             	console.log("www");
         	}
         	var end=Date.now();
		console.log(end-begin);
		console.timeEnd("test");
```
##### Date的一个格式化函数

```
//创建一个函数，可以将一个Date对象进行格式化
function formatDate( date ) {
            if(!date){
                date=new  Date();
                  }
            var year=date.getFullYear();
            var month=date.getMonth()+1;
            var day=date.getDate();
            var week=date.getDay();
          var dayArr=["日","一","二","三","四","五","六"]
            return year+"年"+month+"月"+day+"日"+"星期"+dayArr[week];
        }
          alert(formatDate(date));        
```
## Math
* console.log(Math.PI);//圆周率
* console.log(Math.ceil(2.11));//Math.ceil()上舍入
* console.log(Math.floor(2.99));//Math.floor下舍入
* console.log(Math.round(2.89));//Math.round四舍五入
* console.log(Math.random());//Math.random（0-1之间）随机数

```
//例子
 for(var i=0;i<15;i++){
     console.log(Math.random()*9+1);//（1-10）
     console.log(Math.random()*10);//（0-10）
     console.log(Math.random()*6+1);//（1-6）
     console.log(Math.random()*3+4);//（4-7）
     /*n-m:Math.random()*(m-n)+n*/
         }
   console.log(Math.max(1,2,11,89,23));//最大值
   console.log(Math.min(1,2,11,89,23));  //最小值
   console.log(Math.pow(12,2));//12的2次方//x的y次方 Math.pow(x,y)
   console.log(Math.sqrt(9));//开方//开平方
```
## 包装类
* JS中提供了三个包装类：Number  String  Boolean
* 包装类可以将基本数据类型转换为对象，但是在开发中不使用
* 存在的原因：
 	* 当我们去调用基本数据类型的方法时，解析器会临时将基本数据类型包装为对象，去调用方法，调用完毕则销毁
	* 所有String（） Number（） Boolean（）都可以通过基本数据类型数据调用
       - 将基本数据类型转换为对象，叫做装箱
       -  将对象转换为基本数据类型，叫做拆箱     

## 正则表达式
##### 创建方法
* ①var 变量=new RegExp（"正则表达式","匹配模式"）；
*  ②var 变量=/正则表达式/匹配模式

##### 常用正则表达式
①
符号  | 转义后
---   |---
 \|    |或者
 []   |括号中的内容也是或
 [^]  | 除了
[a-z] | 任意小写字母	
[A-a] | 任意大写字母
[A-z] |任意字母
[0-9] |任意数字

②转义字符\

符号 | 转义后
-----|---
 \\. | .
\\\\ |  \\
\w   |  任意单词符      [A-z0-9]
\W   |除了单词符       [^A-z0-9]
\d   |任意数字 	[0-9]
\B   |除了数字	[^0-9]
\s   |空格
\S   |除了空格
\b   |单词边缘   空格 单词前  单词后
\B   |除了单词边缘 
 ③量{}
 

符号 | 转义后
-----|---
{m}	 |刚好出现m次
{m,n}|	m~n次
{m,} |    m次以上
+	 |一次以上	{1,}
?	 |0到1次
*	 |有没有都行
^    |表示开头
$    |表示结尾     
^和$同时使用|表示必须完全匹配正则表达式

##### 正则表达式的方法
**test();**
测试是否匹配规定的正则表达式   
  匹配 则返回true  否则返回false

##### 字符串与正则表达式结合的方法
**①split(reg);**
* 按照正则去分裂，并将分开的元素存在数组中返回
* 自动匹配所有 不需要设置g	

**②search(reg);**
* 按照正则去搜索，并将第一次出现的索引返回
* 只会返回第一次出现的索引，设置g也没用

**③match(reg);**
* 按照正则去匹配，并将匹配上的内容存在数组中返回，默认匹配上一个后面就不匹配了
* 如果要匹配所有的话，需要设置g

**④replace(reg,"新的字符");**
* 按照正则去替换，并且将替换后的结果返回，默认替换第一个
* 如果要替换所有，需要设置g

