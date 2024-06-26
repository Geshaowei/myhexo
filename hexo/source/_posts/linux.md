---
title: linux
date: 2024-05-20 17:07:29
tags:
---
## mysql 相关

Ubuntu删除 重装 mysql

https://geek-docs.com/mysql/mysql-ask-answer/1625_mysql_ubuntu_mysql_uninstall_reinstall.html

初始密码修改

https://blog.csdn.net/qq_26164609/article/details/106881079

重启服务

```
service mysql restart
```

安装C API MYsql：针对找不到mysql.h头文件

sudo apt-get install libmysqlclient-dev

## 文件相关

### 删除命令

1.强制删除文件夹并提示

```
sudo rm -r 文件名
1
```

例如:

```
sudo rm -r  /usr/local/include/opencv
1
```

2.强制删除文件夹并不提示

```cpp
sudo rm -rf 文件名
1
```

3.删除文件

```cpp
sudo rm -f 文件名
```

### CD操作

```linux
cd ~  回到自己的根目录//通常是home
cd / 回到系统根目录
cd .. 退回上级目录
wsl 中， cd ~ 默认进入 cd / 的 root里面。
```

### 文件操作

复制文件

```
cp 目标文件 /目标地址
```

## Go-Linux安装

[https://studygolang.com/articles/14815?fr=sidebar]()

## MyTinyServer

项目链接[MyTinyServer](https://github.com/qinguoyi/TinyWebServer)

问题注意：mysql.h注意是否配置成功

测试环境：WSL下的Ubuntu2004，mysql 8.0。

```shell
make clean //清除make生成文件
```

## 线程进程相关

ps  当前信息

ps -axf

ps -axm纤细

## 系统操作

```
nprox ：cpu逻辑处理器个数（线程数）
lscpu:查看cpu信息

```
