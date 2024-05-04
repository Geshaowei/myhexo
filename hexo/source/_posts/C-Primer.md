---
title: C++Primer
date: 2024-04-26 21:06:39
tags: C++
---
# C++ Primer 第六版学习笔记

记录重点难点，易忘、混淆点。

任务1. c++primer保持一天一个章节，加课后习题
任务2. 刷题一天两道，配合学过的c++primer容器和算法去刷够50道开始看labuladong的算法小抄

总计18章节计划5.10号前搞定任务一。

## Day1-2024/4/26：0-Chapter2-end

## Chapter2

tips：在大型项目中不写 using namespace std 二十using std::cin using std::cout以定向定义某些函数的空间，而不是直接定义所有，防止出现歧义。

## Chapter3

C++内置的整形-unsigned long 、long、unsigned int、int、unsigned short、short、unsigned char、signed char、bool

C++11新增：unsigned long long 和 long long

表示各种整形的系统限制的 climits 文件

表示各种整型的数字字面值（常量）

使用const限定符来创建符号常量。

浮点：float\double\long double

表示各种浮点类型的系统限制的cfloat 文件

各种浮雕类型的数字字面值

自动类型转换 强制类型转换

### 简单变量

short 至少16

int 至少与short 一样长

long至少32位，且至少与int一样长

long long 至少64位，且至少与long一样长

#### 特殊控制符

dec\hex\oct 分别指示cout 十进制、十六进制、八进制显示正数

cout<<hex;\\\此后的打印均改变。

cout<<int_n;

## Chapter4数组

char   chararray[];//  char字符串可直接cout打印，如果未满自动补\0,\0也是string的输出终止条件。

### 注意

'S'是83的另一种写法，但是“S"字符串的写法则代表S和\0组成的字符串，因此用常量不相等，单引号和双引号不能互通。而且”S“ 实际上表示的是字符串所在的内存地址。因此

```cpp
char shirt_size = "S";  //非法的
```

这试图将一个内存地址赋值给shirt_size;

### 指针和自由存储空间

int *pt = new int;//自我理解为类似匿名变量，即没有直接表示该数据的变量名称，但是又确实存在这样一块变量地址，唯一访问方法为指针pt访问。

注意: 正常变量的值都被存在栈的内存区域中，而new 从被成为堆或自由存储区的内存区域分配内存。

```cpp
int *ps = new int;
...
delete ps;//释放内存
delete ps;//不被允许，因为已经释放。
int jugs = 5;
int *pi = &jugs;
delete pi;//不被允许 地址不是new分配的内存。
```

这样会释放ps指向的内存，但是不会删除指针ps本身。

#### 使用new来创建动态数组

如果直接声明创建数组，则在被编译时将分配内存空间。此时为静态联遍 static binding。而使用new时，则在运行阶段创建它。这被成为动态联编。dynamic binding。

1. 不要使用delete 来释放不是new分配的内存
2. 不要是哟个delete释放同一块内存两次。
3. 如果用new[] 分配数组则用delete[] 释放
4. 如果使用new[] 为一个实体分配，则应用delete 来释放
5. 对空指针 nullptr 应用delete 是安全的。

```cpp
double *p3 =new double [3];
p3[0] = 0.2;
p3[1] = 0.3;
p3[2] = 0.5;
//指针可以当作数组来访问每个元素。
p3 = p3+1;//不同的是可以改变指针变量指向的第一个值。
//现在p3[0]  = 0.3;
```

### 指针不同于实体的关键点

实体对象利用 . 来实现数据和函数的调用，而指向实体的指针可以用->直接访问实体的数据和函数。//自我理解，重载运算符，类似 (*p).函数/变量

### string 和 char[]类型的 I/O

char [] -> 可以用 cin.getline(c,n);//c代表char * ,n代表长度。

string str;// getline(cin,str);   //读取整行，正常的cin读取到 空格或者换行符停止。

## Chapter5循环语句

"++ * 的关系"

++运算符级别较高

++*pt是先取值后加加

但是**p*++和*++pt都是先自加再取值

关系运算符的优先级不如算数运算符

x+3<y+3     //相当于 (x+3)<(y+3)

c风格字符串不能用来 ==，因为其表示的是一个地址，只会比较是否地址相同，应该用strcmp(str1,str2);  str1 == str2 时返回 0 否则 > 给 +0

string对象可以用来 == != 因为string类重载了这些运算符。

逗号表达式   ，  逗号的运算等级最低:  int a = 1,2;相当于  int a = 1 ;2 在后面被舍弃。int a = (1,2); 这种情况使用右值， 即 int a =2 ;

## Chapter if条件逻辑语句

&& 和 ||  低于算数运算符，因此一般判断条件不需要加上括号既可以。但是！的优先级优于算数运算符和逻辑运算符，在对表达式取反时要加上括号。

### 字符函数库cctype

继承至ctype.h。 isalpha(ch),如果ch是一个字符 返回一个int类型的非零数。同样如果ch是一个,句号等标点符号，则ispunct(ch)则返回一个非零值。

```cpp

#include<cctype>
char ch;
if('a'<=ch&&ch<='z'||'A'<=ch&&ch<='Z')   =>  if(isalpha(ch))
isdigits()=》是否为一个数字
isspace 是否为一个空格
```

本章节的课后题未作。//记得补上

## Chapter7

函数相关 int add(int * a,int * b);//声明函数，指针形式传递地址，数组同样可以传递指针，也可以传递 int a[].使用方式相同。

函数指针 int (*pf) (int a,int b)；声明一个int返回值，两个int参数的函数指针pf。函数的地址为函数名. pf = funname;   (*pf)(a,b);

typedef int (*pf)(int a,int b);声明一个pf函数指针类型。 pf a; a即为一个pf类型的函数指针。

## Chapter8函数探幽

int & value = a;  value 同 a的值和地址一样。即value是a的别名

### 尽可能使用const

使用const可以避免无意中修改数据的编程错误

使用const使函数能偶处理const和非const实参，否则将只能接受非const数据

使用const引用使函数能够正确生成并使用临时变量。

应尽可能将引用行参声明为const。

### 右值引用

&&声明，即： int && a = 3；

### 引用细节

函数内部临时变量不能作为引用返回，会报错。//5.3第八章没学完。后续补

### 函数重载

同命名方法，但是不同参数列表。在一个命名只有一个函数时，函数调用会强制转换类型，使参数类型强制转换。但是重载实现后，参数不匹配时，程序将拒绝调用函数。

非const可以默认转换const 但是const不能作为参数传递给非const参数。

如果重载const 和 普通类型，编译器会根据参数是否是const进行调用。

C++不允许相同参数不同返回值的重载。必须不同参。

当传递"string"时，这种类型为char *，但是由于为右值，因此参数为const char * 才可以被匹配。如果没有const char * 可以被强制转为string也可以。

实现重载的底层是编译器会对函数进行名称修饰或者名称矫正

long myfunction(int a,double b); 会被转化为内部不同的接口表示 ?myfunction@@YAXH
