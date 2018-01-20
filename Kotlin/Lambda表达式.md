Lambda表达式
===
```
1. lambda 表达式总是被大括号括着；
2. 其参数（如果有的话）在 -> 之前声明（参数类型可以省略）；
3. 函数体（如果存在的话）在 -> 后面
```
```
//第一种
    val sum1 = {x: Int,y: Int -> x+y}
    println(sum1)
    println(sum1(1,2))
//第二种 
    val sum2 : (x: Int,y:Int) -> Int = {a,b->a+b}
    println(sum2(2,3))
```
	输出结果:(kotlin.Int, kotlin.Int) -> kotlin.Int
		3
		5
在kotlin里面,一切皆对象,函数也可以是对象.
sum1就是一个函数类型的变量,打印的是sum的是两个int参数,返回一个int的函数
sum2跟sum1是一样的,只不过声明了该变量的类型,而sum1未声明.

补充:高级函数
```
fun 高阶函数名(参数函数名：参数函数类型)：高阶函数返回类型{
    高阶函数体
    ...
}
```

```
//参数为一个参数为int返回值为int的函数,和一个int类型的值
fun doTest(test: (Int)->Int,a: Int){
    println(test(a))
}
```
```
fun main(args: Array<String>) {
    val function = {a: Int -> a+2}//一个参数为int,返回值为int的函数类型变量.
    doTest(function,2)
	doTest({a->a+2},2)
//两种方法一样
}
```
	输出结果:4




