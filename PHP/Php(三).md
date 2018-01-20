Php(三)
===

# 函数的使用
函数的返回值可以是任意的类型,也可以不返回值.
## 参数传递方式

```
function test1($a){
        $a = $a+1;
    return $a;
}
$a = 1;
echo test1($a);
echo $a;
```
	输出结果:21
	就是说没有改变a的值

```
function test1(&$a){
        $a = $a+1;
    return $a;
}
$a = 1;
echo test1($a);
echo $a;
```
	输出结果:22
	这里传的是地址,所以a的值改变了,跟C++有点像.

注意 传的要是变量,传常量,会报错:
```
function test1(&$a){
        $a = $a+1;
    return $a;
}
$a = 1;
echo test1(2);
```
报错:PHP Fatal error
还可以设置默认参数:

```
function test2($name="I",$fruit="apple"){
    echo $name." like ".$fruit;
}
test2("you");
```
	输出结果:you like apple
	为防止意外情况:一般将默认参数放在非默认参数的右侧.
	意外情况指的是:

```
function test2($name="I",$fruit){
    echo $name." like ".$fruit;
}
test2("you");
```
	这样是会报错的.因为第二个参数没有传值.
可变参数:

```
function test(...$num){
    foreach ($num as $value){
        echo $value." ";
    }
}
test(1,2,3,4);
```
	输出结果:1 2 3 4 
在php7中函数增加了返回值的类型声明

```
function sum($a,$b): int {
    return a+b;
}
var_dump(sum(1,2));
```
可变函数: 形如

```
function foo(){
    echo "this is foo";
}
$f = "foo";
$f(); //调用了foo();
```
匿名函数(闭包函数):

```
$greet = function ($name){
    echo "hello ".$name;
};
$greet("PHP");
```
	输出结果:hello PHP
	闭包函数可以作为变量的值来使用.
闭包函数可以从父作用域中继承变量,这时需要使用关键字use

```
$message = "Hello World";
$example = function () use ($message){
    echo $message;
};
echo $example();
```
	输出结果:Hello World




