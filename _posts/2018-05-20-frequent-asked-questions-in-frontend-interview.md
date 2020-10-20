---
layout: post
title: Frequent asked questions in front end interview
date: 2018-05-20 19:20:23 +0900
category: general
---
# 前端面试题总结

* [HTML相关](#HTML相关)
    * [html5知识点](#html5知识点)
	* [html5优缺点](#html5优缺点)
	* [DOM事件](#DOM事件)
	* [如何理解web语义化](#如何理解web语义化)
	* [什么是跨域以及应对措施](#什么是跨域以及应对措施)
	* [cookie/sessionStorage/localStorage的区别](#cookie/sessionStorage/localStorage的区别)
	* [强缓存和协商缓存](#强缓存和协商缓存)
	* [浏览器的重排和重绘](#浏览器的重排和重绘)

* [JS相关](#JS相关)
	* [理解静态/动态/强/弱类型语言](#理解静态动态强弱类型语言)
	* [let/const/var定义变量的区别](#不同方式定义变量的区别)
	* [undefined和null有什么区别？怎样判断](#undefined和null的区别以及判断方式)
	* [怎样理解原型和原型链](#怎样理解原型和原型链)
	* [原型链继承的原理](#原型链继承的原理)
	* [使用new创建对象的过程](#使用new创建对象的过程)
	* [怎样理解js中的this](#怎样理解js中的this)
	* [js中改变this的几种方法/区别？](#js中改变this的几种方法以及区别？)
	* [判断某对象是否为array的方法](#判断某对象是否为array的方法)
	* [生成指定区间的随机数组](#生成指定区间的随机数组)
	* [实现数组去重的几种方法](#实现数组去重的几种方法)
	* [js交换两个节点如何实现](#js交换两个节点如何实现)
	* [js命名空间,怎样保证多个js文件中同名方法不冲突](#js命名空间,怎样保证多个js文件中同名方法不冲突)
	* [正则表达式的贪婪匹配和非贪婪匹配](#正则表达式的贪婪匹配和非贪婪匹配)
	* [怎样实现函数节流和函数防抖](#怎样实现函数节流和函数防抖)
	* [浏览器内核简介](#浏览器内核简介)

* [CSS相关](#CSS相关)
    * [盒子模型](#盒子模型)
    * [CSS设置元素不可见的方法](#CSS设置元素不可见的方法)
    * [margin重叠问题](#margin重叠问题)
    * [position的不同值的区别](#position的不同值的区别)
    * [样式优先级](#样式优先级)
    * [怎样实现垂直居中](#怎样实现垂直居中)

* [网络相关](#网络相关)
    * [网络基础知识](#网络基础知识)
    * [HTTP状态码](#HTTP状态码)
    
* [更多](#更多)
    * [一篇很有价值的面试题总结](#一篇很有价值的面试题总结)

## HTML相关
### html5知识点
[MDN的一篇介绍总结的很好](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5)
### html5优缺点
- 优点：
    * 有了更多的语义化标签，如`header、footer、nav、section、article`等
    * 用于绘画的canvas元素，有了对于2D/3D图形的支持
    * 对于音频、视频元素的支持
    * 可用于移动开发以及游戏开发等
    * 对于本地存储的支持（sessionStorage、localStorage）
- 缺点
    * 因新标签的引入，各浏览器之间将缺少一种统一的数据描述格式，造成用户体验不佳
    * 技术门槛高，需要对后台开发知识有一定了解
### DOM事件
参考链接：[DOM事件深入浅出(一)](http://www.cnblogs.com/luozhihao/p/5934935.html)
### 如何理解web语义化
[参考链接](https://zhuanlan.zhihu.com/p/25493886)
### 什么是跨域以及应对措施
### cookie/sessionStorage/localStorage的区别
sessionStorage和localStorage大体相似，都是用于在网页端在浏览器中存储数据的。唯一区别在于有效期不同。
* 不同点：
    * localStorage有效期：在同一浏览器内，生命周期从创建操作直到删除操作，同源的前提下，不同tab页面或窗口可共享。
    * sessionStorage有效期：在同一浏览器内，当前页面开启到关闭,刷新页面，session不过期。但在不同tab页面或窗口不共享。
* 相同点：
    * 常用API：[storage].setItem(key, value), [storage].getItem(key), [storage].removeItem(key), [storage].clear()。 
    * key和value都是string类型的，若传入其他类型的值会被自动转为string类型。
    * 两种存储方式在http网页和https网页间都不共享。
而cookie则是可以随请求发送到服务器的存储载体。（[详细介绍](https://segmentfault.com/a/1190000004556040#comment-area)）
### 强缓存和协商缓存
[参考链接](http://www.cnblogs.com/wonyun/p/5524617.html)
### 浏览器的重排和重绘
参考链接：[浏览器的重绘与重排](http://blog.jobbole.com/46722/)

## JS相关
### 理解静态动态强弱类型语言
[参考文章](https://segmentfault.com/a/1190000012372372)
* 静态类型：编译时就知道变量类型 
* 动态类型：运行时才知道一个变量类型
* 强类型：不允许隐式转换
* 弱类型：允许隐式转换
### 不同方式定义变量的区别
* 使用`let`声明的变量，其作用域为该语句所在的代码块内，不存在变量提升(同一作用域内重复声明会报错)
* 使用`const`声明的是常量，在后面出现的代码中不能再修改该常量的值(实质是变量指向的内存地址不能修改，对于对象而言，内存地址保存的是指针，当使用const声明对象时，对象数据结构可以被再次修改;只声明不赋值会报错)
* 使用`var`声明的变量，其作用域为该语句所在的函数内，且存在变量提升现象(值为undefined)
### undefined和null的区别以及判断方式
* `null`：Null类型，代表“空值”，代表一个空对象指针，使用typeof运算得到 “object”，所以你可以认为它是一个特殊的对象值。
* `undefined`： Undefined类型，当一个声明了一个变量未初始化时，得到的就是undefined。
* 判断null： !exp && typeof(exp)!="undefined" && exp!=0 (exp === null也可以)
* 判断undefined：typeof(some) == undefined

[相关链接](http://www.ruanyifeng.com/blog/2014/03/undefined-vs-null.html)
### 怎样理解原型和原型链
我认为讲得很好的一篇文章：[JavaScript深入之从原型到原型链](https://github.com/mqyqingfeng/Blog/issues/2)
### 原型链继承的原理
js通过构造函数实现继承，但在构造函数里定义的所有属性和方法都会被实例化，这样一来所有实例无法共享属性和方法，也造成了资源浪费，所以才有了了原型链。原型链上的所有属性和方法被所有实例所共有。

更详细的解释参考阮一峰老师的个人博客：[Javascript继承机制的设计思想](http://www.ruanyifeng.com/blog/2011/06/designing_ideas_of_inheritance_mechanism_in_javascript.html)

### 使用new创建对象的过程
(详见JS红宝书145页)
1. 创建一个新对象
2. 将构造函数的作用域赋给新对象（因此this指针就指向了步骤1中创建的新对象）
3. 执行构造函数中的代码（为这个新对象添加属性）
4. 返回新对象

### 怎样理解js中的this
请参考阮一峰老师的文章：[Javascript的this用法](http://www.ruanyifeng.com/blog/2010/04/using_this_keyword_in_javascript.html)
以及[JavaScript的this原理](http://www.ruanyifeng.com/blog/2018/06/javascript-this.html)
### js中改变this的几种方法以及区别？
bind/call/apply [这篇文章](https://zhuanlan.zhihu.com/p/27571439)写的清晰明了

### 判断某对象是否为array的方法
详细分析看[这里](#http://web.mit.edu/jwalden/www/isArray.html)
```js
//基于instanceof :
    a instanceof Array;
//基于constructor:
    a.constructor === Array;
//基于Object.prototype.isPrototypeOf:
    Array.prototype.isPrototypeOf(a);
//基于getPrototypeOf :
    Object.getPrototypeOf(a) === Array.prototype;
//基于Object.prototype.toString :
    Object.prototype.toString.apply(a) === '[object Array]';
```
### 生成指定区间的随机数组
```js
function createRandomArray(n, m, l){
    var array=[];
    for(let i=0; i<l;i++){
        // 由[n, m]区间内的整数组成的长度为l的数组
        array.push(Math.round(Math.random()*(m-n))+n);
        // 由[n, m)区间内的整数组成的长度为l的数组
        // Math.floor(Math.random()*(m-n))+n;
        // 由(n, m]区间内的整数组成的长度为l的数组
        // Math.ceil(Math.random()*(m-n))+n;
    }
    return array; 
}
```
### 实现数组去重的几种方法
```js
//1.
function unique(arr){
    var n={}, r=[];
    for(var i=0;i<arr.length; i++){
	if(!n[arr[i]]){
	    n[arr[i]]=true;
	    r.push(arr[i]);
	}
    }
    return r;
}

//2.
arr.indexof(arr[i])==-1
//或者
arr.indexof(arr[i])==arr.lastIndexof(arr[i]) //就push到入新数组

//3. ES6中的方法：
unique = arr => {
    const map = new Map()；
    return arr.filter((a) =>
	!map.has(a) && map.set(a, 1)
	)
}
// or
unique = arr => Array.from(new Set(arr));
```
### js交换两个节点如何实现
```js
function swapDiv(elm) {
    var previous = findPrevious(elm);
    if (previous) {
        elm.parentNode.insertBefore(elm, previous);
    }
}
```
### js命名空间,怎样保证多个js文件中同名方法不冲突
使用模块，其原理是使用了js中的闭包特性: 就是可以把局部变量驻留在内存中，可以避免使用全局变量（[详解](https://www.liaoxuefeng.com/wiki/001434446689867b27157e896e74d51a89c25cc8b43bdb3000/001434502419592fd80bbb0613a42118ccab9435af408fd000)）
[相关链接](https://mp.weixin.qq.com/s?__biz=MjM5MTA1MjAxMQ==&mid=2651224992&idx=1&sn=6741686437e3c34f18b5557de5f6a6dc&chksm=bd49a2248a3e2b329626e5057c6068fe5ee0411a2fc944d1568dc307b5e02e905342db454919&scene=21#wechat_redirect)
### 正则表达式的贪婪匹配和非贪婪匹配
如果在数量词 *、+、? 或 {}, 任意一个后面紧跟该符号（?），会使数量词变为非贪婪（ non-greedy） ，即匹配次数最小化。反之，默认情况下，是贪婪的（greedy），即匹配次数最大化。(自[MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp))
比如
```js
var reg = /a+/g;
var reg1=/a+?/g;
var str='hahaa';
var newStr=str.replace(reg, 'o');
var newStr1=str.replace(reg1, 'o');
console.log(newStr);//hoho
console.log(newStr1);//hohoo
```
### 怎样实现函数节流和函数防抖
[参考链接](https://blog.csdn.net/crystal6918/article/details/62236730)

### 浏览器内核简介
相关机构名称 | 浏览器名称 | 内核名称
---- | --- | ---
Microsoft | IE | Trident
Mozilla |  Firefox | Gecko
Apple | Webkit | Safari
Opera SAS | Opera | Presto

## CSS相关

### 盒子模型
[盒子模型](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model)，[盒子宽高值计算](https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-sizing)
### CSS设置元素不可见的方法
[参考链接](https://75team.com/post/five-ways-to-hide-elements-in-css.html)
### margin重叠问题
MDN详解文档[外边距合并](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Box_Model/Mastering_margin_collapsing)
### position的不同值的区别
MDN详解文档[position](https://developer.mozilla.org/zh-CN/docs/Web/CSS/position)
### 样式优先级
MDN详解文档[优先级](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Specificity)写的非常详细，一定要注意其中的细节，很可能被当成考题。
### 怎样实现垂直居中

## 网络相关
[一篇非常优秀的讲解HTTPS的文章](https://mp.weixin.qq.com/s?__biz=MzI3MzgxNDY2MQ==&mid=2247484382&idx=1&sn=8e127b43152dfadc9ac0f81ffe9c4668&chksm=eb1cc634dc6b4f2221294c06a0648af9d6a0209f47ae3f4cf173b0cddbea9fc1c716a02f5c20&scene=0&xtrack=1&key=26d8a6fbb72821d1d02658fd50ce2540d33012f95957f24d8030b944783fc6dfc81fe0eef6bb71fddfc5eafd2d6702ba29ce8dea7b010ab11e3a607bb4d1bf376420a0506fb68abd58056578adaac68e&ascene=1&uin=MTY4NDU4MTc4Mg%3D%3D&devicetype=Windows+10&version=62070158&lang=en&exportkey=AcLnD0cB17hSU6Vc%2BZrIqKE%3D&pass_ticket=0YKgJq364ZUIKgAM22AuNmkrARnPz4C4iq7exP%2B17SvFmf0Qhh4BVlnX9UodJcpx)

### 网络基础知识
[参考链接](https://medium.freecodecamp.org/how-the-web-works-a-primer-for-newcomers-to-web-development-or-anyone-really-b4584e63585c)
### HTTP状态码
[参考链接](#https://funteas.com/topic/5a0038d0f399aad809035856)

## 更多
### 一篇很有价值的面试题总结
[你有必要知道的25个JavaScript面试题](https://github.com/dwqs/blog/issues/17)
