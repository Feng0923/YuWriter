Php语言基础
===
声明:只记录特别的知识点,常见的不在此累赘.
## 比较运算符

| 运算符 | 名称 | 描述 |
|---|---|---|
| x === y | 恒等于 | 如果x恒等于y,且两者数据类型相同,返回true,否则返回false |
| x <> y | 不等于 | 如果x不等于y,返回true,否则返回false |
| x !== y | 不恒等于 | 如果x不等于y,或者两者类型不同,返回true,否则返回false |
| x <=> y | 组合比较符 | 如果x的值和y的值相等(不是恒等于),就返回0;如果x的值大于y的值返回1;如果x的值小于y的值,就返回-1;(php 7新增运算符) |
eg:
```
<?php
$x = 100;
$y = "100";
var_dump($x == $y); //bool(true)
var_dump($x === $y); //bool(false)
var_dump($x <> $y); //bool(false)
var_dump($x !== $y); //bool(true)
var_dump($x <=> $y); //int(0)
?>
```
## 逻辑运算符

| 运算符 | 名称 | 描述 |
|---|---|---|
| x xor y | 异或 | x和y仅有一个为true,就返回true |

## 字符串的连接
	php中使用英文字符"."将多个字符串连接

```
<?php
$a = "hello";
$b = "world";
$c = $a.$b;
echo $c;
?>
```
	输出结果:helloworld

## 变量的作用域
函数内部无法访问外面的变量

```
<?php
$x = 5;
function test()
{
    $y = 10;
    echo "<p>inside function<p/>";
    echo "x is $x <br>";
    echo "y is $y <br>";
}
test();
echo "<p>outside function<p/>";
echo "x is $x <br>";
echo "y is $y <br>";
```

	输出结果:
```
inside function
x is
y is 10
outside function
x is 5
Notice: Undefined variable: y in D:\Phpstorm\workSpace\Test\test3.php on line 19
y is 
```
要想访问有以下几种方法:
```
$x = 5;
function test()
{
    global $x;
    echo "$x";
}
```
```
$x = 5;
function test()
{
     echo $GLOBALS['x'];
}
```
### static关键字

```
echo "<p>outside function<p/>";
echo "x is $x <br>";
echo "y is $y <br>";
function add()
{
    static $x = 0;
    echo $x;
    $x++;
}
add();
add();
add();
```

	输出结果:012
### $$含义

```
$a = "aa";
$aa = "bb";
echo $$a;
```
	输出结果:bb
### 常量的声明:

```
define("A","A");
const B = "B";
```






