---
title: C++ STL
date: 2024-03-07 19:49:29
tags: C++
---
# C++数据类型语法

## unordered_set

#### 引入头文件

```c++
#include <unordered_set>
```


#### unordered_set是什么

unordered_set 容器，可直译为“无序 set 容器”。即 unordered_set 容器和 set 容器很像，唯一的区别就在于 set 容器会自行对存储的数据进行排序，而 unordered_set 容器不会。

#### **unordered_set的几个特性：**

1. 不再以键值对的形式存储数据，而是直接存储数据的值 ；
2. 容器内部存储的各个元素的值都互不相等，且不能被修改；
3. 不会对内部存储的数据进行排序

#### unordered_set的初始化

```c++
unordered_set<int> set1;//创建
unordered_set<int> set2(set1);//copy
unordered_set<int> set3(set1.begin(), set1.end());//使用迭代器构造
unordered_set<int> set4(arr,arr+5);//使用数组作为其初值进行构造
unordered_set<int> set5(move(set2));//移动构造
unordered_set<int> set6 {1,2,10,10};//使用处置列表
```

#### unordered_set常用函数

```c++
set1.empty();//判断是否位空 是 True 否 Flase;
set1.find(2);//查找，//查找2，找到返回迭代器，失败返回end()
set1.count(2);//返回0 1；
//插入元素，返回pair<unordered_set<int>::iterator, bool>
set1.insert(3);
//使用initializer_list插入元素
set1.insert({1,2,3});
//指定插入位置，如果位置正确会减少插入时间，返回指向插入元素的迭代器
set1.insert(set1.end(), 4);
//使用范围迭代器插入
set1.insert(set2.begin(), set2.end());
```

关于insert函数的返回值：
insert()只传入单个参数（待插入元素）

1. 会返回一个 pair 对象
2. 这个 pair 对象包含一个迭代器，以及一个附加的布尔值用来说明插入是否成功
3. 如果元素被插入，返回的迭代器会指向新元素
4. 如果没有被插入，迭代器指向阻止插入的元素
   ```c++
   auto pr = words.insert("ninety"); // Returns a pair - an iterator & a bool value
   ```

**insert()传入两个参数（迭代器+待插入元素）**

1. 插入初始化表中的元素
2. 在这种情况下，什么都没有返回

```C++
words.insert({"ten", "seven", "six"});  // Inserting an initializer list
```

**emplace()函数——插入元素(转移构造)**

```c++
//使用转移构造函数添加新元素3，比insert效率高
set1.emplace(3);

```

```c++
//删除操作，成功返回1，失败返回0
set1.erase(1);
//删除操作，成功返回下一个pair的迭代器
set1.erase(set1.find(1));
//删除set1的所有元素，返回指向end的迭代器
set1.erase(set1.begin(), set1.end());

```
