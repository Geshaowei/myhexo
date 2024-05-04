---
title: lua
date: 2024-04-23 14:14:55
tags: 游戏开发lua脚本
---
# Lua学习之路

## 基础语法

### 数据类型

tab = {"value1","value2"}  --{}表类型从下标1开始

数字类型只有一个number

允许匿名函数 function() 

string 的连接用  ..

string类型遇到 + - 等会自动转化 number

nil 空 判断中可作false

boolean   false true

### 变量

变量转换

 ->string    = string.format

number  = tonumber  --(类似"123")这种，包含不合规字符会nil

可变参数 ...

```lua
function average(...)
   result = 0
   local arg={...}
   for i,v in ipairs(arg) do
      result = result + v
   end
   print("总共传入 " .. select("#",...) .. " 个数") --select("#"...)查询可变参数数量
   return result/select("#",...)
end

print("平均值为",average(10,5,3,4,5,6))
```

### 循环

### 数据结构

#### 特殊
