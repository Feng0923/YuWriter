Php(五)---数组
===
## 数组的类型{#index}
php中有两种类型的数组,即索引数组和关联数组.索引数组键由数字组成,(默认为索引数组),关联数组由字符串和数字混合组成.
- 关联数组
$array1 = array("a"=>"foo","b"=>"bar");
- 索引数组
$array2 = array(1=>"foo",2=>"bar");
```
$a = array("foo1","foo2","foo3");
$b = array("a","b",6=>"c","d");
var_dump($a);
var_dump($b);
```
	输出结果:array(3) {
 	 [0]=>
  	string(4) "foo1"
 	 [1]=>
 	 string(4) "foo2"
	  [2]=>
 	 string(4) "foo3"
	}
	array(4) {
 	 [0]=>
  	string(1) "a"
  	[1]=>
  	string(1) "b"
 	 [6]=>
 	 string(1) "c"
 	 [7]=>
  	string(1) "d"
	}
## 创建数组
除了上节所示的,还有:
```
$arr["a"] = "red";
$arr["b"] = "orange";
var_dump($arr);
$arr2 = ["dog","cat","wolf"];
var_dump($arr2);
$arr3[] = "a";
$arr3[] = "b";
var_dump($arr3);
```
还可以使用range()来建立一个指定范围单元的数组
array range(mixed $start,mixed $limit [,number $step]);
step:单元之间的步进值;
```
$a = range(0,6,2);
$b = range("a","g");
print_r($a);
print_r($b);
```
	输出结果:Array
	(
    [0] => 0
    [1] => 2
    [2] => 4
    [3] => 6	
	)
	Array
	(
    [0] => a
    [1] => b
    [2] => c
    [3] => d
    [4] => e
    [5] => f
    [6] => g
	)
## 二维数组
```
$person = array("jack"=>array("age"=>20,"weight"=>"50kg"),
                "Tom"=>array("age"=>19,"weight"=>"45kg")
);
print_r($person);
```
## 多维数组
```
$arr = array("安徽"=>array("宿州"=>array("埇桥区","灵璧县"),
                            "合肥"=>array("蜀山区","肥东")),
    "河南"=>array(",,"=>array(",,",",,"),
        ",,"=>array(",,",",,"))
);
print_r($arr);
```
## 检查数组中是否存在某个值
bool in_array(mixed $needle , array $haystack [,bool $strict = FALSE])
说明: 如果没有设置strict,就使用宽松的比较.如果设为true,就还会检查类型是否相同.
注意: in_array()函数只能在当前维度数组中检查是否存在某个元素.
```
$arr = array("安徽"=>array("宿州"=>array("埇桥区","灵璧县"),
                            "合肥"=>array("蜀山区","肥东")),
    "河南"=>array(",,"=>array(",,",",,"),
        ",,"=>array(",,",",,"))
);
var_dump(in_array("合肥",$arr));
$arr2 = ["red","green","blue"];
var_dump(in_array('green',$arr2));
```
	输出结果:bool(false)
		bool(true)
## 数组转换为字符串
string implode(string $glue , array $pieces)
glue:分割符
```
$arr2 = ["red","green","blue"];
$string = implode("-",$arr2);
echo $string;
```
	输出结果:red-green-blue
## 计算数组中的单元数目
int count(mixed $var [,int $mode = COUNT_NORMAL])
```
$person = array("jack"=>array("age"=>20,"weight"=>"50kg"),
                "Tom"=>array("age"=>19,"weight"=>"45kg")
);
echo count($person)." ";
echo count($person,1);
```
	输出结果:2 6
## 数组当前单元和数组指针
```
$food = ["orange","banana","apple"];
echo current($food)." ";//指针指向当前单元
echo next($food)." ";//指针向下移
echo prev($food)." ";//指针向前移
echo end($food)." ";//指针指向最后一位
echo reset($food);//重置指针,指向第一位
```
	输出结果:orange banana orange apple orange


[go](#index)




