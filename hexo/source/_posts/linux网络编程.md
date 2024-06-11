---
title: linux网络编程
date: 2024-05-24 12:23:50
tags:
---
1. 线程的概念
2. 线程的创建
   线程的终止
   栈的清理
   线程的取消选项
3. 线程同步
4. 线程属性
   线程同步的属性
5. 重入

## linux的多线程编程

```
#include<pthread.h> //pthread
#include<stdio.h>
#include<unistd.h> //usleep()
```

多线程和锁的相关，如果直接make 和gcc会出现未定于pthread相关函数 因为没有链接静态库

```shell
gcc thread.c -o thread -lpthread
```

## 线程概念

posix 标准

pthread_t   类型线程

pthread_self()   //返回pthread_t 类型，相当于 getpid()

### 线程的创建

pthread_create()

线程的调度取决于调度的策略

### 线程的终止

3种终止方法：

1. 线程从启动历程返回，返回值就是线程的退出码
2. 线程可以被同一进程种的其他线程取消
3. 线程调用pthread_exit()函数

pthread_join()    ---wait() 等待收尸

### 栈的清理

pthread_cleanup_push();

pthread_cleanup_pop();

### 线程同步

```
pthread_mutex_t;
pthread_mutex_init();
pthread_mutex_destory();
pthread_mutex_lock();
pthreaD_mutex_trylock();
pthread_mutex_unlock();
```

## 线程池的数量：

在StackOverflow上面发现了一个还不错的[回答](https://stackoverflow.com/a/16128493/7121726)，意思是：
线程池中的线程数量最直接的限制因素是中央处理器(CPU)的处理器(processors/cores)的数量 `N`：如果你的CPU是4-cores的，对于CPU密集型的任务(如视频剪辑等消耗CPU计算资源的任务)来说，那线程池中的线程数量最好也设置为4（或者+1防止其他因素造成的线程阻塞）；对于IO密集型的任务，一般要多于CPU的核数，因为线程间竞争的不是CPU的计算资源而是IO，IO的处理一般较慢，多于cores数的线程将为CPU争取更多的任务，不至在线程处理IO的过程造成CPU空闲导致资源浪费，公式：`最佳线程数 = CPU当前可使用的Cores数 * 当前CPU的利用率 * (1 + CPU等待时间 / CPU处理时间)`（还有回答里面提到的Amdahl准则可以了解一下）
