# By：狸墨  

# QQ群：134722347



# 变量和常量

## 变量

变量命名规范:

1、 必须以字母或下划线开头，不要以数字开头；

2、 后面可以跟任意字母、下划线、数字；

3、 camel命名法：首个单词小写，后面的单词首字母大写；（类名方法名首字母大写）

4、在变量的作用域内不能再定义同名的变量

注意：

　　　　不能以C#中的关键字命名；

　　　　同一个变量名不能重复定义；

静态变量：静态变量只需创建一次，在后面程序中可以多次引用，静态变量的初始值就是该变量的默认值，不需要创建其所属类的对象。

局部变量：在一个独立的程序块中声明的变量，它只在该范围中有效。

## 常量

常量用来存储固定数值，一旦初始化就不会再改变

字符常量：

| 转义序列 | 含义                |
| :------- | :------------------ |
| \\       | \ 字符              |
| \'       | ' 字符              |
| \"       | " 字符              |
| \?       | ? 字符              |
| \a       | Alert 或 bell       |
| \b       | 退格键（Backspace） |
| \f       | 换页符（Form feed） |
| \n       | 换行符（Newline）   |
| \r       | 回车                |
| \t       | 水平制表符 tab      |
| \v       | 垂直制表符 tab      |

定义常量: const <data_type> <constant_name> = value;

# 数据类型

## 堆和栈

内存分为堆空间和栈空间。

栈空间比较小，但是读取速度快

堆空间比较大，但是读取速度慢

栈的特征：

   数据只能从栈的顶端插入和删除

   把数据放入栈顶称为入栈（push）

   从栈顶删除数据称为出栈（pop）

堆里的内存能够以任意顺序存入和移除，堆是由系统弹性配置的内存空间，没有特定大小与存活时间，可以被弹性的运用于对象的访问

数据类型被分为两种：值类型(整数，bool struct char 小数)和引用类型（string 数组 自定义的类，内置的类）。

 1）值类型只需要一段单独的内存，用于存储实际的数据，（单独定义的时候放在栈中）

 2）引用类型需要两段内存

 第一段存储实际的数据，它总是位于堆中

 第二段是一个引用，指向数据在堆中的存放位置

## 值类型

### 简单类型：

| 类型       | 举例                                                       |
| :--------- | :--------------------------------------------------------- |
| 整数类型   | sbyte、byte、short、ushort、int、uint、long、ulong 和 char |
| 浮点型     | float 和 double                                            |
| 十进制类型 | decimal                                                    |
| 布尔类型   | true 或 false 值，指定的值                                 |
| 空类型     | 可为空值的数据类型                                         |

sbyte 有符号整数 存储空间1B,取值范围-128~127

byte 无符号整数，存储空间1B，取值范围0~255

short 有符号短整型,存储空间2B，取值范围-32768~+32767

ushort 无符号短整型，存储空间2B，取值范围0~65535

int 有符号整型,存储空间4B,取值范围-2^31~2^31

uint无符号整型,存储空间4B,取值范围0~2^31

long有符号长整型,存储空间4B,取值范围-2^63~2^63

ulong无符号长整型,存储空间4B,取值范围0~2^63

char字符型,存储空间1B,取值范围为 -128 ~ 127	

float 单精度浮点数,存储空间4B,取值范围为-3.4×10^-38～3.4×10^38

double 双精度浮点数,存储空间8B,取值范围为-1.7×10^-308～1.7×10^308

decimal 关键字指示 128 位数据类型。 与浮点型相比，decimal 类型具有更高的精度和更小的范围，这使它适合于财务和货币计算

### 枚举类型：

枚举类型（enum type）是具有一组命名常量的独特的值类型，如果没有显式声明基础类型，则使用 Int32。默认基数从O开始，也可指定数值。

### 结构类型：

像类一样，结构（struct）是能够包含数据成员和函数成员的数据结构，但是与类不同，结构是值类型，不需要堆分配。结构类型不支持用户指定的继承，并且所有的结构类型都隐式地从类型 object 继承。

结构是使用 struct 关键字定义的，通常用来封装小类型相关变量组，对小型数据结构而言，使用结构而不是用类会大大节省应用程序分配的量。

### 可空类型：

可空类型可以表示其基础值类型正常范围内的值，再加上一个 null 值。为了定义一个可空变量类型，在底层数据类型中添加？作为后缀。

```
< data_type> ? <variable_name> = null;
```

Lua：G:\MyTeach\project\LuaWorkSpaceOfMid\src

## 引用类型

定义：引用类型不存储它们所代表的实际数据，而是存储对实际数据的引用。引用类型的变量通常称为对象，对象的实例使用new关键字创建，存储在堆中。

### 类类型

类是一种包含数据成员、函数成员和嵌套类型的数据结构。

类的数据成员：常量、域和事件；

函数成员：方法、属性、索引指示器、运算器、构造函数和析构函数。

#### 1.自定义类型

使用Class关键字定义的类型

#### 2.Object类型

可以为 Object 的变量分配任何引用类型（字符串、数组、类或接口）。Object 变量还可以引用任何值类型（数值、Boolean、Char、Date、结构或枚举）的数据。

Object 数据类型可以指向任意数据类型的数据，包括您的应用程序识别的任意对象实例。当您在编译时不知道变量可能指向哪种数据类型时，请使用 Object。

#### 3.String类型字符串

| 序号 | 属性名称 & 描述                                              |
| :--- | :----------------------------------------------------------- |
| 1    | **Chars** 在当前 *String* 对象中获取 *Char* 对象的指定位置。 |
| 2    | **Length** 在当前的 *String* 对象中获取字符数。              |

C#将字符串视为一个基本类型，它可以申请为一个常量，也可以直接给它赋值。由于C#中的字符串是由System.String类派生而来的引用对象，因此可以使用String类的方法来对字符串进行各种操作。

**字符串的复制：**

​	Copy()方法只适用于需要吧某个字符串完整复制到另一个字符串中的情况，相比之下CopyTo（）则比较灵活。

**字符串的比较：**

String类字符串比较大概有4种方法:Compare(),CompareTo(), CompareOrdinal()和Equals(). 

Compare()方法是CompareTo()的静态版本

而Equals()与”==”是等价的,只要使用”==”运算符,就会调用Equals()方法。

CompareOrdinal()对两个字符串进行比较,不考虑本地化语言和文化。

**字符串的查找：**

(1)、String.Contains(Findstr)

(2)、String.IndexOf(Findstr)

(3)、String.LastIndexOf(FindStr)

**字符串的截取：**

(1)、String.SubString(StartIndex)
(2)、String.SubString(StartIndex, Len)
**字符串的分割：**

String.Split(SplitCh)

**字符串的合并:**

(1)、String.Concat(str1, str2, …., strn)

(2)、String.Join(SplitCh, array)

(3)、用 ‘+’ 来实现

**字符串的长度**

String.Length

返回长度值

**字符串的替换：**

String.Replace(SreStr, ChangeStr)

**字符串的插入与填充：**

(1)、String.Insert(index, str)

(2)、String.PadRight(Len, ch)

(3)、String.PadLeft(Len, ch)

**字符串的删除：**

(1)、String.Trim()

(2)、string.Trim(Param char[])

(3)、String.Remove(Start)

(4)、String.Remove(Start, Len)

**字符串大小写转换：**

(1)、String.ToLower()：将字符串转化为小写形式
(2)、String.ToUpper()：将字符串转换成大写形式

#### Lua相关

Lua模式串：与相关的方式配对

.  任意字符 
%a  字母 
%c  控制字符 
%d  数字 
%l  小写字母 
%p  标点字符 
%s  空白符 
%u  大写字母 
%w  字母和数字 
%x  十六进制数字 
%z  代表 0的字符 

# 运算符

算数运算符

| 运算符 | 描述                             | 实例             |
| :----- | :------------------------------- | :--------------- |
| +      | 把两个操作数相加                 | A + B 将得到 30  |
| -      | 从第一个操作数中减去第二个操作数 | A - B 将得到 -10 |
| *      | 把两个操作数相乘                 | A * B 将得到 200 |
| /      | 分子除以分母                     | B / A 将得到 2   |
| %      | 取模运算符，整除后的余数         | B % A 将得到 0   |
| ++     | 自增运算符，整数值增加 1         | A++ 将得到 11    |
| --     | 自减运算符，整数值减少 1         | A-- 将得到 9     |

关系运算符

| 运算符 | 描述                                                         | 实例              |
| :----- | :----------------------------------------------------------- | :---------------- |
| ==     | 检查两个操作数的值是否相等，如果相等则条件为真。             | (A == B) 不为真。 |
| !=     | 检查两个操作数的值是否相等，如果不相等则条件为真。           | (A != B) 为真。   |
| >      | 检查左操作数的值是否大于右操作数的值，如果是则条件为真。     | (A > B) 不为真。  |
| <      | 检查左操作数的值是否小于右操作数的值，如果是则条件为真。     | (A < B) 为真。    |
| >=     | 检查左操作数的值是否大于或等于右操作数的值，如果是则条件为真。 | (A >= B) 不为真。 |
| <=     | 检查左操作数的值是否小于或等于右操作数的值，如果是则条件为真。 | (A <= B) 为真。   |

逻辑运算符

| 运算符 | 描述                                                         | 实例              |
| :----- | :----------------------------------------------------------- | :---------------- |
| &&     | 称为逻辑与运算符。如果两个操作数都非零，则条件为真。         | (A && B) 为假。   |
| \|\|   | 称为逻辑或运算符。如果两个操作数中有任意一个非零，则条件为真。 | (A \|\| B) 为真。 |
| !      | 称为逻辑非运算符。用来逆转操作数的逻辑状态。如果条件为真则逻辑非运算符将使其为假。 |                   |



# 流程控制

## 1.条件分支语句

### 	If语句

​	最常用的选择语句，根据布尔表达式的值来判断是否执行后面的内嵌语句

​	![image-20220102152009823](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220102152009823.png)

### 	 **if...else** 语句

​		![image-20220102152536123](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220102152536123.png)

###  **if...else **if...else  语句

一个 **if** 语句后可跟一个可选的 **else if...else** 语句，这可用于测试多种条件。

当使用 if...else if...else 语句时，以下几点需要注意：

- 一个 if 后可跟零个或一个 else，它必须在任何一个 else if 之后。
- 一个 if 后可跟零个或多个 else if，它们必须在 else 之前。
- 一旦某个 else if 匹配成功，其他的 else if 或 else 将不会被测试。

### 嵌套 if 语句

在一个 **if** 或 **else if** 语句内使用另一个 **if** 或 **else if** 语句

### Switch语句

```
switch(expression){
    case constant-expression  :
       statement(s);
       break; 
    case constant-expression  :
       statement(s);
       break; 
  
    /* 您可以有任意数量的 case 语句 */
    default : /* 可选的 */
       statement(s);
       break; 
}
```

**switch** 语句必须遵循下面的规则：

- **switch** 语句中的 **expression** 必须是一个整型或枚举类型，或者是一个 class 类型，其中 class 有一个单一的转换函数将其转换为整型或枚举类型。

- 在一个 switch 中可以有任意数量的 case 语句。每个 case 后跟一个要比较的值和一个冒号。

- case 的 **constant-expression** 必须与 switch 中的变量具有相同的数据类型，且必须是一个常量。

- 当被测试的变量等于 case 中的常量时，case 后跟的语句将被执行，直到遇到 **break** 语句为止。

- 当遇到 **break** 语句时，switch 终止，控制流将跳转到 switch 语句后的下一行。

- 不是每一个 case 都需要包含 **break**。如果 case 语句为空，则可以不包含 **break**，控制流将会继续后续的 case，直到遇到 break 为止。

- C# 不允许从一个开关部分继续执行到下一个开关部分。如果 case 语句中有处理语句，则必须包含 **break** 或其他跳转语句。

- 一个 **switch** 语句可以有一个可选的 **default** case，出现在 switch 的结尾。default case 可用于在上面所有 case 都不为真时执行一个任务。default case 中的 **break** 语句不是必需的。

- C# 不支持从一个 case 标签显式贯穿到另一个 case 标签。如果要使 C# 支持从一个 case 标签显式贯穿到另一个 case 标签，可以使用 goto 一个 switch-case 或 goto default。

  

  ![image-20220102162123165](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220102162123165.png)

## 2.循环控制语句

### while循环语句

![image-20220102163936562](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220102163936562.png)

```
while(condition)
{
   statement(s);
}
```

**statement(s)** 可以是一个单独的语句，也可以是几个语句组成的代码块。**condition** 可以是任意的表达式，当为任意非零值时都为真。当条件为真时执行循环。

### do..while循环语句

![image-20220102165734047](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220102165734047.png)

```
do
{
   statement(s);

}while( condition );
```

**do...while** 循环是在循环的尾部检查它的条件。

**do...while** 循环与 while 循环类似，但是 do...while 循环会确保至少执行一次循环。

### for/foreach循环语句

![image-20220102170831332](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220102170831332.png)

```
for ( init; condition; increment )
{
   statement(s);
}
```

### 循环控制语句

| 控制语句      | 描述                                                         |
| :------------ | :----------------------------------------------------------- |
| break 语句    | 终止 **loop** 或 **switch** 语句，程序流将继续执行紧接着 loop 或 switch 的下一条语句。 |
| continue 语句 | 引起循环跳过主体的剩余部分，立即重新开始测试条件。           |

break语句

![image-20220102171632180](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220102171632180.png)

continue语句

![image-20220102171815679](C:\Users\Administrator\AppData\Roaming\Typora\typora-user-images\image-20220102171815679.png)

return

主要用在函数返回结果，或者结束一个函数的执行

return只能写在语句块的最后，return执行了之后的所有语句都不会执行

### 排序的应用

1）冒泡排序：通过不断的将相邻的两个数进行大小比较，大的数不断的往后面的位置交换，小的数向数组的顶部位置浮动。

3）选择排序：通过交换排序的方式，将某个范围内的最小数提到该范围内的第一位。

### 质数的判断

​	质数又称素数，是指在大于1的自然数中，除了1和它本身以外不再有其他因数的自然数。质数的个数是无限的;它的约数只有1和它本身;所有大于10的质数中，个位数只有1，3，7，9。

​	合数是指在大于1的整数中，除了能被1和本身整除外，还能被其他非零整数整除的数。所有大于2的偶数都是合数;所有大于5的奇数中，个位为5的都是合数;除O以外，所有个位为O的自然数都是合数;所有个位为4，6，8的自然数都是合数;最小的合数为4，最小的奇合数为9;每一个合数都可以以唯一形式被写成质数的乘积，即分解质因数。



# 方法及重载

## 方法

**定义：**在类的内部定义的，并且可以在类或类的实例上运行的具有某个特定功能的模块。

**C#方法必须包含以下3个部分：**

1.方法的名称

2.方法的返回值类型

3.方法的主体

语法如下：

```
<Access Specifier> <Return Type> <Method Name>(Parameter List)
{
   Method Body
}
```

- **Access Specifier**：访问修饰符，这个决定了变量或方法对于另一个类的可见性。
- **Return type**：返回类型，一个方法可以返回一个值。返回类型是方法返回的值的数据类型。如果方法不返回任何值，则返回类型为 **void**。
- **Method name**：方法名称，是一个唯一的标识符，且是大小写敏感的。它不能与类中声明的其他标识符相同。
- **Parameter list**：参数列表，使用圆括号括起来，该参数是用来传递和接收方法的数据。参数列表是指方法的参数类型、顺序和数量。参数是可选的，也就是说，一个方法可能不包含参数。
- **Method body**：方法主体，包含了完成任务所需的指令集。

### 递归方法

一个方法可以自我调用

### 参数传递

| 方式     | 描述                                                         |
| :------- | :----------------------------------------------------------- |
| 值参数   | 这是参数传递的默认方式。在这种方式下，当调用一个方法时，会为每个值参数创建一个新的存储位置。这种方式复制参数的实际值给函数的形式参数，实参和形参使用的是两个不同内存中的值。在这种情况下，当形参的值发生改变时，不会影响实参的值，从而保证了实参数据的安全。 |
| 引用参数 | 引用参数是一个对变量的内存位置的引用。这种方式复制参数的内存位置的引用给形式参数。这意味着，当形参的值发生改变时，同时也改变实参的值。在 C# 中，使用 **ref** 关键字声明引用参数。 |
| 输出参数 | 输出参数会把方法输出的数据赋给自己，其他方面与引用参数相似。这种方式可以返回多个值。使用 **out** 关键字声明输出参数 |

### 参数数组

Params关键字：允许将相同类型数量可变的多个参数传给一个方法

### 可选参数

使用规则：

1.可选参数不能为参数列表的第一个参数，它必须位于所有必选参数之后

2.可选参数必须指定一个默认值

3.可选参数的默认值必须是一个常量表达式

4.所有可选参数以后的参数都必须是可选参数

## 方法的重载

方法的重载即在同一类的内部可以定义同名方法，但这些同名方法的参数列表必须不同，以便在用户调用方法的时候能够自动识别应调用的方法。

# 表

## 数组

数组是一个存储相同类型元素的固定大小的顺序集合。数组是用来存储数据的集合，通常认为数组是一个同一类型变量的集合。

声明数组变量并不是声明 number0、number1、...、number99 一个个单独的变量，而是声明一个就像 numbers 这样的变量，然后使用 numbers[0]、numbers[1]、...、numbers[99] 来表示一个个单独的变量。数组中某个指定的元素是通过索引来访问的。

所有的数组都是由连续的内存位置组成的。最低的地址对应第一个元素，最高的地址对应最后一个元素。

数组的声明：datatype[] arrayName

### ![12维数组](G:\MyTeach\project\CSharpAndLua\学习文档\12维数组.jpg)多维数组：

![多维数组](G:\MyTeach\project\CSharpAndLua\学习文档\多维数组.jpg)

```
int [ , , ] m;
```

### 交错数组：

```
int [][] scores;
```

### Array类

常用属性：

| 序号 | 属性 & 描述                                                  |
| :--- | :----------------------------------------------------------- |
| 1    | **IsFixedSize** 获取一个值，该值指示数组是否带有固定大小。   |
| 2    | **IsReadOnly** 获取一个值，该值指示数组是否只读。            |
| 3    | **Length** 获取一个 32 位整数，该值表示所有维度的数组中的元素总数。 |
| 4    | **LongLength** 获取一个 64 位整数，该值表示所有维度的数组中的元素总数。 |
| 5    | **Rank** 获取数组的秩（维度）。                              |

常用方法：

| 序号 | 方法 & 描述                                                  |
| :--- | :----------------------------------------------------------- |
| 1    | **Clear** 根据元素的类型，设置数组中某个范围的元素为零、为 false 或者为 null。 |
| 2    | **Copy(Array, Array, Int32)** 从数组的第一个元素开始复制某个范围的元素到另一个数组的第一个元素位置。长度由一个 32 位整数指定。 |
| 3    | **CopyTo(Array, Int32)** 从当前的一维数组中复制所有的元素到一个指定的一维数组的指定索引位置。索引由一个 32 位整数指定。 |
| 4    | **GetLength** 获取一个 32 位整数，该值表示指定维度的数组中的元素总数。 |
| 5    | **GetLongLength** 获取一个 64 位整数，该值表示指定维度的数组中的元素总数。 |
| 6    | **GetLowerBound** 获取数组中指定维度的下界。                 |
| 7    | **GetType** 获取当前实例的类型。从对象（Object）继承。       |
| 8    | **GetUpperBound** 获取数组中指定维度的上界。                 |
| 9    | **GetValue(Int32)** 获取一维数组中指定位置的值。索引由一个 32 位整数指定。 |
| 10   | **IndexOf(Array, Object)** 搜索指定的对象，返回整个一维数组中第一次出现的索引。 |
| 11   | **Reverse(Array)** 逆转整个一维数组中元素的顺序。            |
| 12   | **SetValue(Object, Int32)** 给一维数组中指定位置的元素设置值。索引由一个 32 位整数指定。 |
| 13   | **Sort(Array)** 使用数组的每个元素的 IComparable 实现来排序整个一维数组中的元素。 |
| 14   | **ToString** 返回一个表示当前对象的字符串。从对象（Object）继承。 |



## 列表

它可以使用键和索引来访问列表中的项。

排序列表是数组和哈希表的组合。它包含一个可使用键或索引访问各项的列表。如果您使用索引访问各项，则它是一个动态数组（ArrayList），如果您使用键访问各项，则它是一个哈希表（Hashtable）。集合中的各项总是按键值排序。

### 1.创建列表

列表可以存储任何类型的数据，在创建列表对象的时候首先要指定你要创建的这个列表要存储什么类型的（泛型）

### 2.遍历列表

for循环，遍历所有的索引，通过索引访问列表中的元素

foreach遍历

### 3.列表的常用属性方法

**1.Capacity获取容量大小,Count获取数组元素个数**

- Capacity 是列表之前设定的容量值；

- Count 是实际的元素个数。

  Capacity 总是大于或等于 Count，当 Count 超过 Capacity 后，又自动扩容以装下新的元素。

**2.Add()方法添加元素**

**3.Insert()方法插入元素**

向指定索引位置插入元素，原来的元素向后移动一位。插入索引不能超出索引范围。

**4.RemoveAt()方法移除指定位置的元素**

**5.IndexOf()方法取得一个元素所在列表中的索引位置
LastIndexOf()上面的方法是从前往后搜索，这个是从后往前搜索，搜索到满足条件的就停止,上面的两个方法，如果没有找到指定元素就返回-1**

**6.Sort()对列表中是元素进行从小到大排序**

## 字典

注意：必须包含名空间System.Collection.Generic
Dictionary里面的每一个元素都是一个键值对(由二个元素组成：键和值)
键必须是唯一的,而值不需要唯一的
键和值都可以是任何类型(比如：string, int, 自定义类型，等等)
通过一个键读取一个值的时间是接近O(1)
如果你尝试读取字典中一个不存在的键，那么你会得到一个KeyNotFoundException。所有在读取一个键之前，你必须先使用ContainKey来核对键是否存在字典中。

## 泛型

使用泛型给代码带来的5点好处：

1、可以做大限度的重用代码、保护类型的安全以及提高性能。

2、可以创建集合类。

3、可以创建自己的泛型接口、泛型方法、泛型类、泛型事件和泛型委托。

4、可以对泛型类进行约束，以访问特定数据类型的方法。

5、关于泛型数据类型中使用的类型的信息，可在运行时通过反射获取。

泛型类的定义：

访问修饰符 class 类名<T>

{泛型类成员定义}

泛型类对象与创建一般类的对象类似，但不能使用占位符T，必须明确指定一种数据类型替换T

如：泛型类名<int> 对象名=new 泛型类名<int>();

泛型类成员的 定义可以使用T类型的参数或变量

如：public void Mysort（T[] a）

**六种类型的约束：**

| 类型          | 描述                                                         |
| ------------- | ------------------------------------------------------------ |
| T：结构       | 类型参数必须是值类型。可以指定除 Nullable 以外的任何值类型。 |
| T：类         | 类型参数必须是引用类型，包括任何类、接口、委托或数组类型。   |
| T：new()      | 类型参数必须具有无参数的公共构造函数。当与其他约束一起使用时，**new()** 约束必须最后指定。 |
| T：<基类名>   | 类型参数必须是指定的基类或派生自指定的基类。                 |
| T：<接口名称> | 类型参数必须是指定的接口或实现指定的接口。可以指定多个接口约束。约束接口也可以是泛型的。 |
| T：U          | 为 T 提供的类型参数必须是为 U 提供的参数或派生自为 U 提供的参数。这称为裸类型约束。 |

## 集合

### 非泛型集合类

#### **1.ArrayList类**

| 属性           | 描述                                                  |
| :------------- | :---------------------------------------------------- |
| Capacity       | 获取或设置 ArrayList 可以包含的元素个数。             |
| Count          | 获取 ArrayList 中实际包含的元素个数。                 |
| IsFixedSize    | 获取一个值，表示 ArrayList 是否具有固定大小。         |
| IsReadOnly     | 获取一个值，表示 ArrayList 是否只读。                 |
| IsSynchronized | 获取一个值，表示访问 ArrayList 是否同步（线程安全）。 |
| Item[Int32]    | 获取或设置指定索引处的元素。                          |
| SyncRoot       | 获取一个对象用于同步访问 ArrayList。                  |

| 1    | **public virtual int Add( object value );** 在 ArrayList 的末尾添加一个对象。 |
| ---- | ------------------------------------------------------------ |
| 2    | **public virtual void AddRange( ICollection c );** 在 ArrayList 的末尾添加 ICollection 的元素。 |
| 3    | **public virtual void Clear();** 从 ArrayList 中移除所有的元素。 |
| 4    | **public virtual bool Contains( object item );** 判断某个元素是否在 ArrayList 中。 |
| 5    | **public virtual ArrayList GetRange( int index, int count );** 返回一个 ArrayList，表示源 ArrayList 中元素的子集。 |
| 6    | **public virtual int IndexOf(object);** 返回某个值在 ArrayList 中第一次出现的索引，索引从零开始。 |
| 7    | **public virtual void Insert( int index, object value );** 在 ArrayList 的指定索引处，插入一个元素。 |
| 8    | **public virtual void InsertRange( int index, ICollection c );** 在 ArrayList 的指定索引处，插入某个集合的元素。 |
| 9    | **public virtual void Remove( object obj );** 从 ArrayList 中移除第一次出现的指定对象。 |
| 10   | **public virtual void RemoveAt( int index );** 移除 ArrayList 的指定索引处的元素。 |
| 11   | **public virtual void RemoveRange( int index, int count );** 从 ArrayList 中移除某个范围的元素。 |
| 12   | **public virtual void Reverse();** 逆转 ArrayList 中元素的顺序。 |
| 13   | **public virtual void SetRange( int index, ICollection c );** 复制某个集合的元素到 ArrayList 中某个范围的元素上。 |
| 14   | **public virtual void Sort();** 对 ArrayList 中的元素进行排序。 |
| 15   | **public virtual void TrimToSize();** 设置容量为 ArrayList 中元素的实际个数。 |

#### **2.Queue类**

代表了一个**先进先出**的对象集合

| 属性  | 描述                          |
| :---- | :---------------------------- |
| Count | 获取 Queue 中包含的元素个数。 |

| 序号 | 方法名 & 描述                                                |
| :--- | :----------------------------------------------------------- |
| 1    | **public virtual void Clear();** 从 Queue 中移除所有的元素。 |
| 2    | **public virtual bool Contains( object obj );** 判断某个元素是否在 Queue 中。 |
| 3    | **public virtual object Dequeue();** 移除并返回在 Queue 的开头的对象。 |
| 4    | **public virtual void Enqueue( object obj );** 向 Queue 的末尾添加一个对象。 |
| 5    | **public virtual object[] ToArray();** 复制 Queue 到一个新的数组中。 |
| 6    | **public virtual void TrimToSize();** 设置容量为 Queue 中元素的实际个数。 |

#### **3.Stack类**

代表了一个**先进后出**的对象集合

| 属性  | 描述                          |
| :---- | :---------------------------- |
| Count | 获取 Stack 中包含的元素个数。 |

| 序号 | 方法名 & 描述                                                |
| :--- | :----------------------------------------------------------- |
| 1    | **public virtual void Clear();** 从 Stack 中移除所有的元素。 |
| 2    | **public virtual bool Contains( object obj );** 判断某个元素是否在 Stack 中。 |
| 3    | **public virtual object Peek();** 返回在 Stack 的顶部的对象，但不移除它。 |
| 4    | **public virtual object Pop();** 移除并返回在 Stack 的顶部的对象。 |
| 5    | **public virtual void Push( object obj );** 向 Stack 的顶部添加一个对象。 |
| 6    | **public virtual object[] ToArray();** 复制 Stack 到一个新的数组中。 |

#### **4.Hashtable类**

Hashtable 类代表了一系列基于键的哈希代码组织起来的键/值对。它使用键来访问集合中的元素。

当您使用键访问元素时，则使用哈希表，而且您可以识别一个有用的键值。哈希表中的每一项都有一个键/值对。键用于访问集合中的项目。

| 属性        | 描述                                          |
| :---------- | :-------------------------------------------- |
| Count       | 获取 Hashtable 中包含的键值对个数。           |
| IsFixedSize | 获取一个值，表示 Hashtable 是否具有固定大小。 |
| IsReadOnly  | 获取一个值，表示 Hashtable 是否只读。         |
| Item        | 获取或设置与指定的键相关的值。                |
| Keys        | 获取一个 ICollection，包含 Hashtable 中的键。 |
| Values      | 获取一个 ICollection，包含 Hashtable 中的值。 |

| 序号 | 方法名 & 描述                                                |
| :--- | :----------------------------------------------------------- |
| 1    | **public virtual void Add( object key, object value );** 向 Hashtable 添加一个带有指定的键和值的元素。 |
| 2    | **public virtual void Clear();** 从 Hashtable 中移除所有的元素。 |
| 3    | **public virtual bool ContainsKey( object key );** 判断 Hashtable 是否包含指定的键。 |
| 4    | **public virtual bool ContainsValue( object value );** 判断 Hashtable 是否包含指定的值。 |
| 5    | **public virtual void Remove( object key );** 从 Hashtable 中移除带有指定的键的元素。 |

### 泛型集合类

#### 1.List<T>类

#### 2.dictionary<T>类