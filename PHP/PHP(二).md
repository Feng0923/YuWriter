PHP(二)---流程控制语句
===
 声明:只记录特别的知识点,常见的不在此累赘.
# 跳转语句
## foreach循环

```
$array = [0,1,2];
foreach ($array as $value){
    echo "value is ".$value."<br/>";
}
$array2 = ["a"=>1,"b"=>2,"c"=>3];
foreach ($array2 as $item=>$value){
    echo "键是: ".$item."值是: ".$value."<br/>";
}
```
	输出结果:value is 0
		value is 1
		value is 2
		键是: a值是: 1
		键是: b值是: 2
		键是: c值是: 3
## goto语句
	跳到指定位置执行

```
goto a;
echo "FOO";
a:
echo "BAR<br/>";
for ($i = 0;$i<10;$i++){
    if($i > 2){
        goto b;
    }
    echo $i;
}
b:
echo "跳出循环";
```
	输出结果:BAR
		012跳出循环
# 包含语句
## include语句
包含并运行指定文件.如果没找到就会发出警告.
a.php里写:

```
$color = "Green";
echo "a.php";
```
test.php里写:
	
```
include "a.php";
echo $color;
```
	输出结果:a.php
		Green
## include_one 语句
用于在脚本执行期间同一个文件有可能被包含超过一次的情况时确保只包含一次,以避免函数重定义,变量重新复制等问题.
```
include "a.php";
include "a.php";
```
	输出结果:Green
		Green

```
include "a.php";
include_once "a.php";
```
	输出结果:Green
## require 语句
和include语句几乎完全一样,不同的是当被包含的文件不存在时,发出一个Fatal error错误,程序终止,而include发出警告后,继续执行.


