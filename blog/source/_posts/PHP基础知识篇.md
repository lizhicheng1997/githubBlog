---
title: PHP基础知识篇
date: 2020-03-08
tags:
  - PHP
categories:
  - Php
top: 100
copyright: true
---

# 一、变量

## 1. 局部变量与全局变量
{% blockquote %}
1.要在一个函数中访问一个全局变量，需要使用 global 关键字；
2.PHP 将所有全局变量存储在一个名为 $GLOBALS[index] 的数组中。 index 保存变量的名称。这个数组可以在函数内部访问，也可以直接用来更新全局变量；
{% endblockquote %}
<!--more-->
### 示例
```
<?php
$x = 5;
$y = 10;

function test()
{
    global $x, $y;
    $y = $x + $y;
    echo $y;
}

echo $y;        // 10
test();         // 15
echo $y;        // 15
```

## 2. static作用域
{% blockquote %}
当一个函数完成时，它的所有变量通常都会被删除，第一次声明变量时使用 static 关键字，该局部变量便不会被删除；每次调用该函数时，该变量将会保留着函数前一次被调用时的值；（该变量仍然是函数的局部变量）
{% endblockquote %}
<!--more-->
### 示例
```
<?php
$x = 5;
$y = 10;

function test()
{
    static $x = 0;
    echo $x;
    $x++;
    echo PHP_EOL;   // 换行符
}

test();         // 0
test();         // 1
test();         // 2
```

## 3. 参数作用域
{% blockquote %}
参数是通过调用代码将值传递给函数的局部变量（参数是在参数列表中声明的，作为函数声明的一部分）
{% endblockquote %}
<!--more-->

## 4. PHP EOF
{% blockquote %}
1.必须后接分号，否则编译通不过；
2.EOF 可以用任意其它字符代替，只需保证结束标识与开始标识一致；
3.结束标识必须顶格独自占一行(即必须从行首开始，前后不能衔接任何空白和字符)；
4.开始标识可以不带引号或带单双引号，不带引号与带双引号效果一致，解释内嵌的变量和转义符号，带单引号则不解释内嵌的变量和转义符号；
5.当内容需要内嵌引号（单引号或双引号）时，不需要加转义符，本身对单双引号转义，此处相当与q和qq的用法；
6.位于开始标记和结束标记之间的变量可以被正常解析，但是函数则不可以；
{% endblockquote %}
<!--more-->
### 示例
```
<?php
$name="lzc";
$a= <<<EOF
        "abc"$name
        "123"
EOF;

echo $a;
```

# 二、echo 和 print 语句
{% blockquote %}
1.echo - 可以输出一个或多个字符串，print - 只允许输出一个字符串，返回值总为 1；
2.echo 输出的速度比 print 快， echo 没有返回值，print有返回值1；
{% endblockquote %}


# 三、常量
{% blockquote %}
1.常量在定义后，默认是全局变量，可以在整个运行的脚本的任何地方使用；
2.设置常量，使用 define() 函数
{% endblockquote %}

### 示例
```
// 区分大小写的常量名
define("GREETING", "欢迎访问 Runoob.com");

// 不区分大小写的常量名
define("GREETING", "欢迎访问 Runoob.com", true);
```
