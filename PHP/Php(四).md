Php(四)---字符串
===
## 1.单引号和双引号的区别
在使用单引号时,字符串中需要转义的特殊字符只有反斜杠和单引号本身,单引号不能识别插入的变量.
```
$a = 22;
echo '$a don\'t ';
echo "$a";
```
	输出结果:$a don't 22
双引号转义序列:

| 转义序列 | 字符 | 转义序列 | 字符 |
|---|---|---|---|
| \n | 换行符 | \\ | 反斜杠 |
| \r | 回车符 | \ $ | 美元符号 |
| \t | 制表符 | \ " | 双引号 |
## 字符串的操作
### 改变字符串的大小写
- Ucfirst 将字符串的首字母转换为大写
- Lcfirst 将字符串的首字母转换为小写
- Ucwords 将字符串中每个单词的首字母转换为大写
- Strtouper 将字符串转换为大写
- Strtolower 将字符串的转换为小写
```
$b = "i love you";
echo ucfirst($b).ucwords($b).strtoupper($b);
```
	输出结果:I love youI Love YouI LOVE YOU
### 查找字符串
**stripos(string $haystack,string $needle [,int $offset])
offset : 可选的offset参数允许指定从haystack中的哪个字符开始查找,返回的位置数字值仍然相对于haystack的起始位置.** 
1.	- stripos: 查找字符串中某字符首次出现的位置(不区分大小写)--如果是负数的偏移量,则从字符串尾部开始计数
	- strpos (区分大小写) --偏移量不能为负数
```
$b = "i love you";
var_dump(stripos($b,"d"));
var_dump(stripos($b,"l"));
```
	输出结果:bool(false)int(2)
2.	- strtipos: 计算指定字符串在目标字符串中最后一次出现的位置(不区分大小写)--如果是负数的偏移量,则从字符串尾部开始计数
	- strrpos (区分大小写) --如果是负数的偏移量,则从字符串尾部开始计数
```
$c = "aaddccdddsadfasdfas";
var_dump(strripos($c,"a"));
```
	输出结果:int(17)
### 替换字符串
*str_ireplace(maixed $search,mixed $replace ,mixed $subject [,int & $count])
count:表示执行替换的次数.*
- str_ireplace() (不区分大小写)
- str_replace() (区分大小写)
```
$b = "i love you";
echo str_ireplace("i","he",$b);
```
	输出结果:he love you
### 截取字符串
substr(string $string,int $start [,int $length])
```
$b = "i love you";
echo substr($b,1);
echo substr($b,2,1);
```
	输出结果:i love you love you lo
### 去除字符串首尾空格和特殊字符
- trim 去除首尾两边的空格或特殊字符
- ltrim 去除左边的空格或特殊字符
- rtrim 去除右边的空格或特殊字符
### 计算字符串的长度
strlen(string $string)
### 转义和还原字符串
- 转义:addslashes(string $string)
- 还原:stripslashes()
```
$e = "i don't like you";
$ee = addslashes($e);
echo $ee;
echo stripslashes($ee);
```
	输出结果:i don\'t like youi don't like you
### 重复一个字符串
str_repeat(string $string,int $multiplier);  multiplier>0 否则反回空字符串
```
echo str_repeat("&",9);
```
	输出结果:&&&&&&&&&
### 随即打乱字符串
str_shuffle(string $string);
```
echo str_shuffle("abcdefg");
```
	输出结果:eacfbgd
### 分割字符串
array explode(string $delimiter,string $string [,int $limit]);
- delimiter:表示边界上的分割字符
```
$page = "page1,page2,page3";
$pages = explode(",",$page);
print_r($pages);
```
	输出结果:Array
	(
    [0] => page1
    [1] => page2
    [2] => page3
	)













