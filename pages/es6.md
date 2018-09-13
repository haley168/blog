# ECMAScript 6学习笔记 [返回首页](/)
>来源 [ECMAScript 6 入门--阮一峰](http://es6.ruanyifeng.com/)

# 基本概念
>1.ECMAScript 6.0（以下简称 ES6）是 JavaScript 语言的下一代标准，已经在2015 年 6 月正式发布了。它的目标，是使得 JavaScript 语言可以用来编写复杂的大型应用程序，成为企业级开发语言。

# 新增
## let
>1. ES6新增了let命令，用来声明变量。它的用法类似于var，但是所声明的变量，只在let命令所在的代码块内有效。
>1. 典型的使用场景就是for循环，不用再使用一堆 i j k 了
>1. let不允许在相同作用域内，重复声明同一个变量。

> 在代码块内，使用let命令声明变量之前，该变量都是不可用的。这在语法上，称为“暂时性死区”（temporal dead zone，简称 **TDZ**）
## const
> const声明一个只读的常量。一旦声明，常量的值就不能改变。
const PI = 3.1415;



# 工具
[检测es6支持情况](https://github.com/ruanyf/es-checker)
[Traceur](http://es6.ruanyifeng.com/#docs/intro)