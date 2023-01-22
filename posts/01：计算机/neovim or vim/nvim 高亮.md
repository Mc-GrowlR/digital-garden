---
title: 
created: 2022-09-18 23:47
uid: 202209182347
aliases: []
tags: [nvim]
from: 
editflag: 1
---

# 注意
原本我已经安装了一个 cpp 高亮增强插件：`vim-cpp-enhanced-highlight`，用的主题是 `gruvbox`。
`vim-cpp-enhanced-highlight` 插件仓库地址：
[GitHub - octol/vim-cpp-enhanced-highlight: Additional Vim syntax highlighting for C++ (including C++11/14/17)](https://github.com/octol/vim-cpp-enhanced-highlight)
`vim-cpp-enhanced-highlight` 插件配置：
``` vim
"12.⋅===⋅配置vim-cpp-enhanced-highlight⋅Begin
"高亮类，成员函数，标准库和模板
let⋅g:cpp_class_scope_highlight⋅=⋅1
let⋅g:cpp_member_variable_highlight⋅=⋅1
let⋅g:cpp_class_decl_highlight⋅=⋅1
let⋅g:cpp_posix_standard⋅=⋅1
let⋅g:cpp_concepts_highlight⋅=⋅1
let⋅g:cpp_no_function_highlight⋅=⋅1
let⋅g:cpp_experimental_simple_template_highlight⋅=⋅1
```
# 旧高亮
## 带插件
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220918231028.png)
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220918231039.png)
## 不带高亮插件
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220918233110.png)
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220918233121.png)

# 新高亮
## 带插件
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220918232134.png)

![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220918232150.png)
## 不带插件
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220918233235.png)
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220918233244.png)


经过对比，可发现对于用户自建的类和类成员有突出的显示效果，但是 c++自带类却是非高亮的。

总体来说，各有侧重。我更推荐`nvim-treesitter`，因为这对于我自己编写的模板类以及模板函数有更好地帮助。