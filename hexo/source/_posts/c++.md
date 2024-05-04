---
title: c++
date: 2024-03-11 14:29:16
tags: C++
---
2024年对于C++部分重点梳理记录

开始学习~

## C++

### 常量const和constexpr

```c++
const valuename = initvalue;//声明不可修改常量存储同变量一样，但不可修改。
constexpr valuename() = {return valuename * 2;} //声明不可修改常量函数，类似函数。
```

### 枚举enum

```c++
enum CardinalDirections{
	North = 25,
	South,
	East,
	West
};
//cout<<South输出的值为26;
```

### C++左值/右值引用

```C++
#include<bits/stdc++.h>
int main(){
int a = 1; //a 是作，1是右值
int&& b  = 1 ;// 右值引用
int& c = 1; //左值引用
const int& d = 1 ; //万能引用
//左值，不会因为运算后而消亡，有存储地址。 右值，临时常量。
}

```

### 完美转发

```C++
#include<bits/stdc++.h>

void func(int&& x){
}//无法接受左值

Tamplate <T&& x>
fun1(int& x){
//左值引用
}
fun1(int&& x){
//右值引用
}

void func(T&& x){ //可以接受左右值
fun1(std::forward(x))//完美转发左右值/保持其值类型
}
int main(){

}
```
