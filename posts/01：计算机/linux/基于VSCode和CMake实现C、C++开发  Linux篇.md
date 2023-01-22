---
title: 
created: 2022-06-27-14-18
aliases: []
tags: [计算器,Linux,编译]
from: 
editflag: 0
---

# 视频
[基于VSCode和CMake实现C/C++开发 | Linux篇_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1fy4y1b7TC?p=6&vd_source=8e43b8da5e07eef6f57edcd950d3b1d3)

# 笔记
```shell
sudo apt update
```


## 编译过程

1. 预编译过程   //i 文件
   ```
   # -E 选项指示编译器进队输入文件进行预处理
   g++ -E test.cpp -o test.i
   ```
2. 编译-Compiling   //. s 文件
   -S编译选项告诉g++在为C++代码产生了汇编语言文件后停止编译
   ```
   g++ -S test.i -o test.s
   ```
3. 汇编-Assembling
   -C 选线告诉 C++仅把源代码编译为及其语言的目标代码
   缺省时 g++建立的目标代码文件有一个. o 的扩展名
   ```
   g++ -c test.s -o test.o
   ```

4. 链接-Linking    //bin 文件
   -o 编译选项来为将产生的可执行文件用指定的文件名
   ```
   g++ test.o -o test
   ```


在日常使用中，用一步可以包含整个4个步骤。
# 评论
