---
title: 
created: 2022-06-14 08:41
uid: 202206140841
aliases: []
tags: [笔记,嵌入式,stm32]
from: 
editflag: 0
---
# 笔记
## 新建工程

给 GPIO 13 口输出数据
寄存器操作：
```C
RCC->APB2ENR=0x00000010;//打开GPIOC的时钟
GPIOC->CRH=0x00300000;
//CNF13为通用推挽输出模式（00）
//MODE13为输出模式，最大速度50MHz（11）
GPIOC->ODR=0x00002000;//给全为0就是亮，全为1就是灭
```


![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220614100306.png)


库函数操作：
```C
RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOC,ENABLE);
	GPIO_InitTypeDef GPIO_InitStructure;
	GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP;
	GPIO_InitStructure.GPIO_Pin = GPIO_Pin_13;
	GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
	GPIO_Init(GPIOC,&GPIO_InitStructure);
```

### 新建工程步骤
建立工程文件夹，Keil中新建工程,选择型号
工程文件夹里建立Start、Library、User等文件夹，复制固件库里面的文件到工程文件夹
工程里对应建立Start、Library、User等同名称的分组，然后将文件夹内的文件添加到工程分组里
工程选项，C/C++， Include Paths内声明所有包含头文件的文件夹工程选项，C/C++，Define内定义USE_STDPERIPH_DRIVER
工程选项，Debug，下拉列表选择对应调试器，Settings，FlashDownload里勾选Reset and Run
### 工程架构
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220614104357.png)

## 点亮 LED 灯
```C
#include "stm32f10x.h"                  // Device header
#include "Delay.h"

int main(void)
{
	RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOA,ENABLE);
	//声明结构体
	GPIO_InitTypeDef GPIO_InitStructure;
	//为结构体赋初值
	//输入输出模式 ，PP是推挽输出
	GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP;
	//i/o口
	GPIO_InitStructure.GPIO_Pin = GPIO_Pin_All;
	//速度
	GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
	//结构体初始化函数
	GPIO_Init(GPIOA,&GPIO_InitStructure);
	//GPIO_SetBits(GPIOC,GPIO_Pin_);
	//GPIO_ResetBits(GPIOA,GPIO_Pin_13);
	
	while(1)
	{
		GPIO_ResetBits(GPIOA,GPIO_Pin_0);
		Delay_ms(500);
		GPIO_SetBits(GPIOA,GPIO_Pin_0);
		Delay_ms(500);
		GPIO_WriteBit(GPIOA,GPIO_Pin_0,Bit_SET);
		Delay_ms(500);
		GPIO_WriteBit(GPIOA,GPIO_Pin_0,Bit_RESET);
		Delay_ms(500);
	}
}//int 类型的int main函数文件最后必须是空行 

```

## 流水灯

```C
#include "stm32f10x.h"                  // Device header
#include "Delay.h"

int main(void)
{
	RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOA,ENABLE);
	//声明结构体
	GPIO_InitTypeDef GPIO_InitStructure;
	//为结构体赋初值
	//输入输出模式 ，PP是推挽输出
	GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP;
	//i/o口
	GPIO_InitStructure.GPIO_Pin = GPIO_Pin_All;
	//速度
	GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
	//结构体初始化函数
	GPIO_Init(GPIOA,&GPIO_InitStructure);
	//GPIO_SetBits(GPIOC,GPIO_Pin_);
	//GPIO_ResetBits(GPIOA,GPIO_Pin_13);
	
	while(1)
	{
		GPIO_Write(GPIOA,~0x0001);//4位16进制数分别代表了从PA0到PA15共16个端口，从低到高-》从右到左，前加按位取反
		Delay_ms(500);
		...
	}
}//int 类型的int main函数文件最后必须是空行 

```

## 蜂鸣器

```c
#include "stm32f10x.h"                  // Device header
#include "Delay.h"

int main(void)
{
	//时钟
	RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOB,ENABLE);
	//声明结构体
	GPIO_InitTypeDef GPIO_InitStructure;
	//为结构体赋初值
	//输入输出模式 ，PP是推挽输出
	GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP;
	//i/o口
	GPIO_InitStructure.GPIO_Pin = GPIO_Pin_12;
	//速度
	GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
	//结构体初始化函数
	GPIO_Init(GPIOB ,&GPIO_InitStructure);
	//GPIO_SetBits(GPIOC,GPIO_Pin_);
	//GPIO_ResetBits(GPIOA,GPIO_Pin_13);
	
	while(1)
	{
		GPIO_ResetBits(GPIOB,GPIO_Pin_12);
		Delay_ms(500);
		GPIO_SetBits(GPIOB,GPIO_Pin_12);
		Delay_ms(500);
	}
}//int 类型的int main函数文件最后必须是空行 

```

## 按键控制



# 遇到的错误

## No target connected

![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220614084244.png)
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220614084250.png)
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220614084311.png)
[Keil 提示 No Target Connected解决方法_yunfile007的博客-CSDN博客_keil no target](https://blog.csdn.net/yunfile007/article/details/109694132?spm=1001.2101.3001.6650.4&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-4-109694132-blog-107564868.pc_relevant_default&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7ECTRLIST%7Edefault-4-109694132-blog-107564868.pc_relevant_default&utm_relevant_index=7)
### 问题已解决
我的串口的杜邦线配置没配对
## 利用库函数首次编译时出错
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220614101206.png)


### 问题已解决
在添加文件时未将文件类型改为 all
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220614101726.png)

导致添加的库文件未包含相应的头文件

![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220614101814.png)
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220614101828.png)
全选之后点击 Add 即可：
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220614101920.png)
文件添加成功。
![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220614102125.png)
编译成功。