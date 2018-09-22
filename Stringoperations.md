## 字符串操作  
<div align="center">
    <img src="https://raw.githubusercontent.com/dncProject/CS-DotNet/master/string.png" width="400px">
    <br>
</div>
前言：  
> 无论是哪一种编程语言，对字符串的操作绝对是很重要的。从终端输入的字符都是字符串。不管是什么数据格式（JSON、XML）还是数据库文件都会涉及到对字符串的操作。最后都将以字符流或字节流的形式进行读取操作。

目录：
- 字符串的基本操作
- String和StringBuilder
- 字符的ASCII码和Unicode码

![](https://raw.githubusercontent.com/ckjbug/xiaokui/master/split.png)

### 一，字符串的输入与输出（I/O）

在要求输入一个数字情况下，我们一般在控制台输入的是个字符或者字符串，这时就需要我们进行字符到数字的类型转换。

```
//这里用到了字符串的Split方法，将输入的字符用空格分开，用字符串数组接收
string[] str = Console.ReadLine().Split();
//将输入的两个数进行相加
Console.WriteLine(int.Parse(str[0]) + int.Parse(str[1]));

//如果是单个字符，要转换为数字
int n = int.Parse(Console.ReadLine());

//当然也可以用一个List集合来存储 
//ConvertAll():将当前泛型集合中的元素转换为另一种类型并返回列表
List<int> str = new List<string>(Console.ReadLine().Split()).ConvertAll(i => int.Parse(i)); 
Console.WriteLine(str[0] + str[1]);
```
在很多算法或者字符串处理的地方用的非常多，当然一般算法都是用C/C++，支持C#编译的OJ比较少，我一般刷OJ也是用的C#，山东理工的OJ网站：http://acm.sdut.edu.cn/

上面代码中，重点在于字符串的**分割**和**转换**。

#### **转换**：  
类型之间的转换方法主要分为Convert 和 Parse，相信大家最熟悉的是数据类型的隐式和显示（强制类型）转换（低位（精度）===》高位（精度）能实现隐式的转换），反过来就只能用显示方法实现了。还有装箱和拆箱也是在进行数据类型的转换。派生类转换为基类也是隐式转换。

```
double.Parse(s);
int.Parse(s);

string ss = 10.ToString();//最常见

var a = "" + 10;
Console.WriteLine(a.GetType());//输出：System.String

Convert.ToInt32(Console.ReadLine());//还有ToInt64、ToDouble、ToDataTime等

Class A{}    //派生类转换为基类也是隐式转换
Class B:A
Class A a= new B();  
```
#### **分割**：  
不得不说Split()很强大也很重要，
参考网站：https://www.cnblogs.com/atom-wangzh/p/8489135.html

```
//对单个字符进行分割
string str = "adasdssdasddasad";
string[] strArray = str.Split('d');
foreach (string i in strArray)
{
  Console.WriteLine(i.ToString());
}

//对多个字符进行分割
string str1 = "adasdssdasddasad";
string[] sArray1 = str1.Trim('d').Split(new char[2] {'a','s'});//Trim('d')去掉前后为d的字符，Trim()为去掉前后为空的字符
foreach (string i in sArray1)
{
     Console.WriteLine(i.ToString());
}

//也可以用正则表达式来进行字符串的分割，添加引用using System.Text.RegularExpressions;
string str2 = "adsfdsafdssddafsafdsdfda";
string[] sArray2 = Regex.Split(str2,"ds",RegexOptions.IgnoreCase);
foreach (string i in sArray2)
{
     Console.WriteLine(i.ToString());
}
Console.WriteLine("sArray2有多少个元素："+sArray2.Length);
Console.ReadKey();

```

String.Split 方法有6个重载函数：
下边我们通过一些实例来说明下怎么使用(以下string words = "1,2.3,,4";)：
```
1. public string[] Split(params char[] separator)
程序代码
string[] split = words.Split(new Char[] { ',' });//返回:{"1","2.3","","4"}
string[] split = words.Split(new Char[] { ',', '.' });//返回:{"1","2","3","","4"} 
2. public string[] Split(char[] separator, int count)
程序代码
string[] split = words.Split(new Char[] { ',', '.' }, 2);//返回:{"1","2.3,,4"}
string[] split = words.Split(new Char[] { ',', '.' }, 6);//返回:{"1","2","3","","4"} 
3. public string[] Split(char[] separator, StringSplitOptions options)
程序代码
string[] split = words.Split(new Char[] { ',', '.' }, StringSplitOptions.RemoveEmptyEntries);//返回:{"1","2","3","4"} 不保留空元素
string[] split = words.Split(new Char[] { ',', '.' }, StringSplitOptions.None);//返回:{"1","2","3","","4"} 保留空元素 
4. public string[] Split(string[] separator, StringSplitOptions options)
程序代码
string[] split = words.Split(new string[] { ",", "." }, StringSplitOptions.RemoveEmptyEntries);//返回:{"1","2","3","4"} 不保留空元素
string[] split = words.Split(new string[] { ",", "." }, StringSplitOptions.None);//返回:{"1","2","3","","4"} 保留空元素 
5. public string[] Split(char[] separator, int count, StringSplitOptions options)
程序代码
string[] split = words.Split(new Char[] { ',', '.' }, 2, StringSplitOptions.RemoveEmptyEntries);//返回:{"1","2.3,,4"} 不保留空元素
string[] split = words.Split(new Char[] { ',', '.' }, 6, StringSplitOptions.None);//返回:{"1","2","3","","4"} 保留空元素 
6. public string[] Split(string[] separator, int count, StringSplitOptions options)
程序代码
string[] split = words.Split(new string[] { ",", "." }, 2, StringSplitOptions.RemoveEmptyEntries);//返回:{"1","2.3,,4"} 不保留空元素
string[] split = words.Split(new string[] { ",", "." }, 6, StringSplitOptions.None);//返回:{"1","2","3","","4"} 保留空元素

```
-------------

### 二，String和StringBuilder的区别




------------


### 三，字符的 ASCII 码和 Unicode 码




