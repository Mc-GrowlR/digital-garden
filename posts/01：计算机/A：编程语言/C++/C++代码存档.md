---
title: 
uid: 202205142247
aliases: []
tags: [C++]
from: 
---


# 第二章

## 程序清单2.4 sqrt.cpp



~~~ cpp
// sqrt.cpp--使用sqrt()函数
#include <iostream>
#include <cmath>或者math.h

int main()
{
	using namespace std;

	double area;
	cout << "Enter the floor area, in square feet,of your home:";
	cin >> area;
	double side;
	side = sqrt(area);
	cout << "That's the equivalent of a square " << side
	     << " feet to the side." << endl;
	cout << "How facinating!" << endl;
	return 0;
}
~~~



## 程序清单 2.5  ourfunc.cpp

用户自定义函数，函数原型描述了函数接口，即函数如何与程序的其他部分交互。参数列表指出了何种信息将被传递给函数，函数类型指出了返回值的类型

~~~ cpp
#include <iostream>
void simon(int);//函数原型

int main()
{
	using namespace std;

	simon(3);//第一次调用Simon函数参数为3
	cout << "Pick an integer";
	int count;
	cin >> count;

	simon(count);//第二次调用Simon函数，参数为变量count
	cout << "Done!" << endl;
	return 0;
}
void simon(int n)//函数定义
{
	using namespace std;//在自定义函数中使用usingb指令
	cout << "simon says touch your toes " << n << " times." << endl;
}
~~~

## 程序清单2.6  convert.cpp

~~~ cpp
#include<iostream>//用户自定义有返回值的函数
int stonetolb(int);//函数原型
//转换英石与磅，
int main()
{
	using namespace std;
	int stone;
	cout << "Enter the weight in stone: ";
	cin >> stone;
	int pounds = stonetolb(stone);
	cout << stone << " stone = ";
	cout << pounds << " pounds." << endl;
	return 0;
}
int stonetolb(int sts)//函数定义
{
	return 14 * sts;
}
~~~





# 第三章

## 程序列表3.1 limits.cpp

~~~ cpp
#include<iostream>
#include<climits>//头文件climits包含了关于整形限制的信息。定义了表示各种限制的符号名称

int main()
{
	using namespace std;
	int n_int = INT_MAX;
	short n_short = SHRT_MAX;
	long n_long = LONG_MAX;
	long long n_llong = LLONG_MAX;

	//
	cout << "int is " << sizeof(int) << " bytes." << endl;
	cout << "short is " << sizeof n_short << " bytes." << endl;
	cout << "long is " << sizeof n_long << " bytes." << endl;
	cout << "long long is" << sizeof n_llong << " bytes." << endl;
	cout << endl;

	cout << "Maxium values:" << endl;
	cout << "int: " << n_int << endl;
	cout << "short: " << n_short << endl;
	cout << "long: " << n_long << endl;
	cout << "long long:" << n_llong << endl << endl;

	cout << "Maxium int value = " << INT_MAX << endl;
	cout << "Bits per byte = " << CHAR_BIT << endl;

	return 0;

}
~~~

运行结果：

~~~ cpp
int is 4 bytes.
short is 2 bytes.
long is 4 bytes.
long long is8 bytes.

Maxium values:
int: 2147483647
short: 32767
long: 2147483647
long long:9223372036854775807

Maxium int value = 2147483647
Bits per byte = 8
~~~

## 程序清单3.2 exceed.cpp

~~~ cpp
#include <iostream>
#define ZERO 0
#include<climits>

int main()
{
	using namespace std;
	short sam = SHRT_MAX;
	unsigned short sue = sam;
	
	cout << "Sam has " << sam << " dollars and Sue has " << sue;
	cout << " dollars deposited." << endl << "Add $1 to each account." << endl << "Now ";
	sam = sam + 1;
	sue = sue + 1;
	cout << "Sam has " << sam << " dollars and Sue has " << sue;
	cout << " dollars deposited.\nPoor Sam!" << endl;
	sam = ZERO;
	sue = ZERO;
	cout << "Sam has " << sam << "dollars and Sue has " << sue;
	cout << " dollars deposited." << endl << "Now ";
	sam = sam - 1;
	sue = sue - 1;
	cout << "Sam has " << sam << " dollars and Sue has " << sue;
	cout << " dollars deposited." << endl << "Lucky Sue!" << endl;
	
	return 0;
}
~~~

输出结果

~~~ cpp
Sam has 32767 dollars and Sue has 32767 dollars deposited.
Add $1 to each account.
Now Sam has -32768 dollars and Sue has 32768 dollars deposited.
Poor Sam!
Sam has 0dollars and Sue has 0 dollars deposited.
Now Sam has -1 dollars and Sue has 65535 dollars deposited.
Lucky Sue!
~~~

## 程序清单3.3 hexoct.cpp

整形字面值是显性书写的常量

~~~ cpp
#include<iostream>、

int main()
{
	using namespace std;
	int chest = 42;
	int waist = 0x42;
	int inseam = 042;

	cout << "Monsieur cuts a striking figure!\n";
	cout << "chest = " << chest << " (42 in decimal)\n";
	cout << "waist = " << waist << " (0x42 in hex)\n";
	cout << "inseam = " << inseam << " (042 in octal)\n";
	return 0;
}
~~~
运行结果
~~~
Monsieur cuts a striking figure!
chest = 42 (42 in decimal)
waist = 66 (0x42 in hex)
inseam = 34 (042 in octal)
~~~

## 程序清单3.4 hexoct2.cpp

~~~ cpp
#include<iostream>
using namespace std;
int main() 
{
	int chest = 42;
	int waist = 42;
	int inseam = 42;
	
	cout << "Monsieur cuts a striking figure!" << endl;
	cout << "chest = " << chest << " (decimal for 42)" << endl;
	cout << hex;
	cout << "waist = " << waist << " (hexadecimal for 42)" << endl;
	cout << oct;
	cout << "inseam = " << inseam << " (octal for 42)" << endl;
	return 0;
}
~~~



运行结果

~~~ cpp
Monsieur cuts a striking figure!
chest = 42 (decimal for 42)
waist = 2a (hexadecimal for 42)
inseam = 52 (octal for 42)
~~~

## 程序清单3.5 chartype.cpp

~~~ cpp
#include<iostream>

int main()
{
	using namespace std;
	char ch;
	cout << "Enter a character: " << endl;
	cin >> ch;
	cout << "Hola! ";
	cout << "Thank you for the " << ch << " character." << endl;
	return 0;
}
~~~

运行结果

~~~ cpp
Enter a character:
M//输入
Hola! Thank you for the M character.
~~~

## 程序清单3.6 morechar.cpp

~~~ cpp
#include<iostream>

int main()
{
	using namespace std;
	char ch = 'M';
	int i = ch;//将M的ASCII吗值赋给i
	cout << "The ASCII code for " << ch << " is " << i << endl;
	
	cout << "Add one to the character code:" << endl;
	ch = ch + 1;//改变储存在ch中的ASCII吗值
	i = ch;
	cout << "The ASCII code for " << ch << " is " << i << endl;
	cout << "Displaying char ch using cout.put(ch): ";
	cout.put(ch);//使用对象ｃｏｕｔ来使用函数ｐｕｔ（）
	cout.put('!');
//cout.put()成员函数提供了另一种显示字符的方法，可以代替<<运算符
	cout << endl << "Done" << endl;
	return 0;

}
~~~



运行结果

~~~ 
The ASCII code for M is 77
Add one to the character code:
The ASCII code for N is 78
Displaying char ch using cout.put(ch): N!
Done

~~~



##  程序清单3.7 bondini.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	cout << "\aOperation \"HyperHype\" is now activated!\n";//  \a  表示振铃  可用\007代替\a
	cout << "Enter your agent code:________\b\b\b\b\b\b\b\b";    // \b  表示退格
    //在打印下划线后，程序使用退格字符将光标推到第一个下划线处。
	long code;
	cin >> code;
	cout << "\aYou entered " << code << "...\n";
	cout << "\aCode verified! Proceed with Plan Z3!\n";
	return 0;
}
~~~

运行结果

~~~ cpp
Operation "HyperHype" is now activated!
Enter your agent code:54826343
You entered 54826343...
Code verified! Proceed with Plan Z3!
~~~

##  程序清单3.8  floratnum.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	cout.setf(ios_base::fixed, ios_base::floatfield);
    //ios_base::fixed和ios_base::floatfield是通过包含iostream来提供的常量
    //cout显示6位小数
    //通常cout会删除结尾的零，调用cout.self()将覆盖这种行为，也就是说，可以显示结尾的零
	float tub = 10.0 / 3.0;
	double mint = 10.0 / 3.0;
	const float million = 1.06e6;//E表示法

	cout << "tub = " << tub;
	cout << ", a million tubs = " << million * tub;
	cout << ",\nand ten million tubs = ";
	cout << 10 * million * tub << endl;

	cout << "mint = " << mint << " and a million mints = ";
	cout << million * mint << endl;
	return 0;
}
~~~

## 程序清单3.9 fltadd.cpp

~~~ cpp
//浮点类型默认是double类型
//若将数据储存为florat类型，则使用f或Fh
//若将数据储存为long double类型 则使用l或L后缀
#include<iostream>
int main()
{
	using namespace std;
	float a = 2.34E+22f;
	float b = a + 1.0f;
	cout << "a = " << a << endl;
	cout << "b - a = " << b - a << endl;
	return 0;
}
~~~



运行结果

~~~ 
a = 2.34e+22
b - a = 0
~~~

## 程序清单3.10 arith.cpp

~~~ cpp
#include<iostream>
//实验算术运算木
int main()
{
	using namespace std;
	float hats, heads;
	cout.setf(ios_base::fixed, ios_base::floatfield);//使得输出数显示0
	cout << "Enter another number: ";
	cin >> hats;
	cout << "Enter another number: ";
	cin >> heads;

	cout << "hats = " << hats << "; heads = " << heads << endl;
	cout << "hats + heads =  " << hats + heads << endl;
	cout << "hats - heads = " << hats - heads << endl;
	cout << "hats * heads = " << hats * heads << endl;
	cout << "hats / heads = " << hats / heads << endl;
	return 0;
}
~~~

run

~~~ cpp
Enter another number: 50.25
Enter another number: 11.17
hats = 50.250000; heads = 11.170000
hats + heads =  61.419998//61.42体现了float类型精度的有限
hats - heads = 39.080002
hats * heads = 561.292480
hats / heads = 4.498657
~~~

## 程序清单3.11 divide.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	cout.setf(ios_base::fixed, ios_base::floatfield);
	cout << "Integer division: 9/5 = " << 9 / 5 << endl;
	//两整数相乘，结果为整数
	cout << "Floating-point division: 9.0/5.0 = ";
	cout << 9.0 / 5.0 << endl;
	//如果其中有一个（或两个）操作数是浮点值，则小数部分将保留，结果为浮点数
	cout << "Mixed division: 9.0/5 = " << 9.0 / 5 << endl;
	//浮点常量在默认情况下为double类型
	cout << "double constants: 1e7/9.0 = ";
	cout << 1.e7 / 9.0 << endl;
	cout << "float constants:1e7f/9.0f = ";
	//两个操作数都是float类型，则结果为float类型
	cout << 1.e7f / 9.0f << endl;
	return 0;
}
~~~

run

~~~ cpp
Integer division: 9/5 = 1
Floating-point division: 9.0/5.0 = 1.800000
Mixed division: 9.0/5 = 1.800000
double constants: 1e7/9.0 = 1111111.111111
float constants:1e7f/9.0f = 1111111.125000
~~~

## 程序清单3.12 modulus.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	const int Lbs_per_stn = 14;
	int lbs;

	cout << "Enter your weight in pounds: ";
	cin >> lbs;
	int stone = lbs / Lbs_per_stn;
	int pounds = lbs % Lbs_per_stn;
	cout << lbs << " pounds are " << stone << " stone, " << pounds << " pound(s).\n";
	return 0;
}
~~~

运行结果

~~~
Enter your weight in pounds: 181
181 pounds are 12 stone, 13 pound(s).
~~~

## 程序清单3.13 assign.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	cout.setf(ios_base::fixed, ios_base::floatfield);
	float tree = 3;
	int guess(3.9832);
	int debt = 7.2E12;
	cout << "tree = " << tree << endl;
	cout << "guess = " << guess << endl;
    //将浮点型转换为整数时，C++将采取截取（丢弃小数部分）
	cout << "debt = " << debt << endl;
	return 0;
}
~~~

~~~ 
tree = 3.000000
guess = 3
debt = 1634811904
~~~

## 程序清单 3.4 typecast.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	int auks, bats, coots;
	auks = 19.9 + 11.9;

	bats = (int)19.9 + (int)19.9;//旧的C格式
	coots = int(19.9) + int(19.9);//新的C++格式
	cout << "auks = " << auks << ", bats = " << bats;
	cout << ", coots = " << coots << endl;

	char  ch = 'Z';
	cout << "The code for " << ch << " is ";//打印char
	cout << int(ch) << endl;//打印int
	cout << "Yes, the code is ";
	cout << static_cast<int>(ch) << endl;//使用  static_cast转换ch
	return 0;
}
~~~

运算结果

~~~ 
auks = 31, bats = 30, coots = 30
The code for Z is 90
Yes, the code is 90
~~~

使用强制类型转化。可以使一种格式的数据能够满足不同的期望

强制类型转化不会修改变量本身，而是创建一个新的、指定类型的值。

类型转换的格式：

` (typeName)value`

` typeName(value)`

` static_cast<typeName> (value)`



## 程序练习

### 5.

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	long long world_population;//声明世界人口
	long long us_population;//声明美国人口
	double population_per;//声明人口比例

	cout << "Enter the world's population: ";
	cin >> world_population;
	cout << "Enter the population of US:";
	cin >> us_population;
    //强制类型转换，将两个long long类型转换为double类型。以保证运算结果是浮点数。
	population_per = (double(us_population) / double(world_population)) * 100;
	cout << "The population of the US is " << population_per << "% of the world population";
	return 0;
}
~~~



# 第四章

## 程序清单 4.1 arrayone.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	int yams[3];
	yams[0] = 7;
	yams[1] = 8;
	yams[2] = 6;

	int yamcosts[3] = { 20,30,5 };
	cout << "Total yams = ";
	cout << yams[0] + yams[1] + yams[2] << endl;
	cout<<"The package with "<<yams[1] << " yams costs ";
	cout << yamcosts[1] << " cents per yam.\n";
	int total = yams[0] * yamcosts[0] + yams[1] * yamcosts[1];
	total = total + yams[2] * yamcosts[2];
	cout << "The total yam expense is " << total << " cents.\n";
	
	cout << "\nSize of yams array = " << sizeof yams;
	cout << " bytes.\n";
	cout << "Size of one element = " << sizeof yams[0];
	cout << " bytes.\n";
	return 0;
}
~~~

~~~
Total yams = 21
The package with 8 yams costs 30 cents per yam.
The total yam expense is 410 cents.

Size of yams array = 12 bytes.
Size of one element = 4 bytes.
~~~

## 程序清单4.2	strings.cpp

~~~ cpp
#include<iostream>
#include<cstring>
int main()
{
	using namespace std;
	const int Size = 15;
	char name1[Size];
	char name2[Size] = "C++owboy";
	cout << "Howdy! I'm" << name2;
	cout << "! What's your name?\n";
	cin >> name1;
	cout << "Well, " << name1 << " , your name has ";
	cout << strlen(name1) << " letters and is stored\n";
	cout << "in an arry of " << sizeof(name1) << " bytes.\n";
	name2[3] = '\0';
	cout << "Here are the first 3 characters of my name:";
	cout << name2 << endl;
	return 0;

}
~~~

## 程序清单 4.3 instr.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	const int ArSize = 20;
	char name[ArSize];
	char dessert[ArSize];

	cout << "Enter your name;\n";
	cin >> name;
	cout << "Enter your favorite dessert:\n";
	cin >> dessert;
	cout << "I have some delicious " << dessert;
	cout << " for you, " << name << ".\n";
	return 0;
}
~~~

~~~
Enter your name;
Alistair Dreeb
Enter your favorite dessert:
I have some delicious Dreeb for you, Alistair.
~~~

由此可见，cin在获取字符数组输入时若遇到多个单词只读取一个单词，并将它放在数组中，并自动在结尾添加空字符。

同时，cin也不能预防输入的字符串比目标数组长的情况。

## 程序清单 4.4 instr2.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	const int ArSize = 20;
	char name[ArSize];
	char dessert[ArSize];

	cout << "Enter your name:\n";
	cin.getline(name, ArSize);
	cout << "Enter your favorite dessert:\n";
	cin.getline(dessert, ArSize);
	cout << "I have some delicious " << dessert;
	cout << " for you, " << name << ".\n";
	return 0;
}
~~~

~~~Enter your name:
Enter your name:
Drik Hammernose
Enter your favorite dessert:
Radish Torte
I have some delicious Radish Torte for you, Drik Hammernose.
~~~

## 程序清单 4.5 instr3.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	const int ArSize = 20;
	char name[ArSize];
	char dessert[ArSize];
	
	cout << "Enter your name:\n";
	cin.get(name, ArSize).get();
	cout << "Enter your favorite dessert:\n";
	cin.get(dessert, ArSize).get();
	cout << "I have some delicious " << dessert;
	cout << " for you, " << name << ".\n";
	return 0;

}
~~~

~~~
Enter your name:
Mai Parfait
Enter your favorite dessert:
Choolate Mousse
I have some delicious Choolate Mousse for you, Mai Parfait.
~~~

## 程序清单 4.6 numstr.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	cout << "What year was your house built?\n";
	int year;
	cin >> year;
	cout << "What is its street address?\n";
	char address[80];
	cin.getline(address, 80);
	cout << "Year built: " << year << endl;
	cout << "Address: " << address << endl;
	cout << "Done!\n";
	return 0;

}
~~~



~~~
What year was your house built?
1966
What is its street address?
Year built: 1966
Address:
Done!
~~~

用户没有输入地址的机会。

当` cin`读取年份，将回车键生成的换行符留在了输入队列中。后面的` cin.getline`看到换行符之后，将会以为是一个空行，并将一个空字符串赋给address数组。

## 程序清单 4.7 strtype.cpp

~~~ cpp
#include<iostream>
#include<string>　　使用string　类
int main()
{
	using namespace std;
	char charr1[20];
	char charr2[20];
	string str1;
	string str2 = "panther";／／Ｃ风格初始化

	cout << "Enter a kind of feline: ";
	cin >> charr1;
	cout << "Enter another kind of feline: ";
	cin >> str1;／／使用ｃｉｎ输入
	cout << "Here are some felines:\n";
	cout << charr1 << " " << charr2 << " " << str1 << " " << str2 << endl;／／可以使用ｃｏｕｔ来显示string对象
	cout << "The third letter in " << charr2 << " is " << charr2[2] << endl;
	cout << "The third letter in " << str2 << " is " << str2[2] << endl;
    ／／可以使用数组表示法来访问储存在string对象中的字符
	return 0;
}
~~~

~~~
Enter a kind of feline: ocelot
Enter another kind of feline: tiger
Here are some felines:
ocelot jaquar tiger panther
The third letter in jaquar is q
The third letter in panther is n
~~~

类设计能使程序自动处理string的大小

## 程序清单 4.8 strtype2.cpp

~~~ cpp
#include<iostream>
#include<string>
int main()
{
	using namespace std;
	string s1 = "penguin";
	string s2, s3;

	cout << "You can assign one string object to another: s2 = s1\n";
	s2 = s1;
	cout << "s1: " << s1 << ", s2: " << s2 << endl;
	cout << "You can assign a C-style string to a string object.\n";
	cout << "s2 = \"nuzzard\"\n";
	s2 = "buzzard";
	cout << "s2: " << s2 << endl;
	cout << "You can concatenate strings: s3 = s1 + s2\n";
	s3 = s1 + s2;
	cout << "s3: " << s3 << endl;
	cout << "You can append strings.\n";
	s1 += s2;
	cout << "s2 += \"for a day\" yields s2 = " << s2 << endl;

	return 0;
}
~~~

~~~ 
You can assign one string object to another: s2 = s1
s1: penguin, s2: penguin
You can assign a C-style string to a string object.
s2 = "nuzzard"
s2: buzzard
You can concatenate strings: s3 = s1 + s2
s3: penguinbuzzard
You can append strings.
s2 += "for a day" yields s2 = buzzard
~~~

4.8说明，可以将一个string对象赋给另一个string对象

可以用运算符 + 将两个string对象合并起来

可以使用运算符 += 将字符串附加到string对象的末尾

## 程序清单 4.9 strtype3.cpp

~~~ cpp
#include<iostream>
#include<string>
#include<cstring>
int main()
{
	using namespace std;
	char charr1[20];
	char charr2[20] = "jaquar";
	string str1;
	string str2 = "panther";

	str1 = str2;
	strcpy(charr1, charr2);

	str1 += "paste";
	strcat(charr1, "juice");

	int len1 = str1.size();
	int len2 = strlen(charr1);

	cout << "The string " << str1 << " contains " << len1 << " characters.\n";
	cout << "The string " << charr1 << " contains " << len2 << " characters.\n";

	return 0;
}
~~~

~~~ 
The string pantherpaste contains 12 characters.
The string jaquarjuice contains 11 characters.
~~~

解决VS2019  C4996错误代码方法：

> 项目→属性→C/C++→SDL检查(点击关闭)

## 程序清单 4.10 strtype.cpp

~~~ cpp
#include<iostream>
#include<string>
#include<cstring>
int main()
{
	using namespace std;
	char charr[20];
	string str;

	cout << "Lengh of string in charr before input: " << strlen(charr) << endl;
	cout << "Lengh of string in str  before input: " << str.size() << endl;
	cout << "Enter a line of text:\n";
	cin.getline(charr, 20);
	cout << "You entered: " << charr << endl;
	cout << "Enter another line of text:\n";
	getline(cin, str);
	cout << "You entered: " << str << endl;
	cout << "Length of string in charr after input:" << strlen(charr) << endl;
	cout << "length of string in str after input: " << str.size() << endl;
	return 0;
}
~~~

~~~ 
Lengh of string in charr before input: 31//随机数
Lengh of string in str  before input: 0
Enter a line of text:
peanut butter
You entered: peanut butter
Enter another line of text:
blueberry jam
You entered: blueberry jam
Length of string in charr after input:13
length of string in str after input: 13
~~~

未初始化的数组的内容是未定义的。

函数` strlen()`从数组的第一个元素开始计算字节数，直到遇到空字符

## 程序清单 4.11 strctur.cpp

~~~ cpp 
#include<iostream>
struct inflatable
{
	char name[20];
	float volume;
	double price;
};
int main()
{
	using namespace std;
	inflatable guest =//结构初始化
	{
		"Glorious Gloria",//字符数组
		1.88,//float类型
		29.99//double类型
	};//使用逗号分隔值列表，可以每值一行，也可以都在一行中
	inflatable pal =
	{
		"Audacious Arthur",
		3.12,
		32.99
	};
    //可将每个结构成员可做是相应类型的变量
	cout << "Expand your guest list with " << guest.name;
	cout << " and " << pal.name << "!\n";
	cout << "You can have both for $";
	cout << guest.price + pal.price << "!\n";
	return 0;
}
~~~

~~~
Expand your guest list with Glorious Gloria and Audacious Arthur!
You can have both for $62.98!
~~~

结构声明的位置很重要。

声明位置：

- 将声明放在` main()`函数中，紧随在开始括号的后面，被称为内部声明。
- 将声明放在` main()`之前，被称为外部声明。

区别： 

- 外部声明可以被其后面的任何函数使用。
- 内部声明只能被该声明所属的函数使用

对于变量，也可以在函数内部和外部定义，外部变量由所有函数共享。（C++不提倡使用外部变量，但提倡使用外部结构声明）



可以使用成员运算符（.）来访问各个成员

结构可以让string类作为成员

**C++11结构初始化：**

支持列表初始化且等号（=）可选

若` {}`内未包含任何东西，各个成员都被设置为零，若是数组，则次成员每个字节都被设置为零（字符数组，C-风格）

## 程序清单 4.12 assgn_st.cp

~~~ cpp 
#include<iostream>
struct inflatable
{
	char name[20];
	float volume;
	double price;
};
int main()
{
	using namespace std;
	inflatable bouquet =
	{
		"sunflowers",
		0.20,
		12.49
	};
	inflatable choice;
	cout << "bouquet: " << bouquet.name << "for %";
	cout << bouquet.price << endl;

	choice = bouquet;//将结构赋给另一同类型的结构
	cout << "choice: " << choice.name << " for $";
	return 0;
}
~~~

~~~
bouquet: sunflowersfor %12.49
choice: sunflowers for $
~~~





可以同时完成定义结构和创建结构变量的工作。
方法：将变量名放在结束括号的后面
例：

~~~ cpp
struct perks
{
    int key_number;
    char car[12];
}mr_smith,ms_jones;
~~~

可以对上述方法创建的变量初始化
例：

~~~ cpp
struct perks
{
    int key_number;
    char car[12];
}mr_glitz =
{
    7,
    "packard"
};
~~~

可以声明没有名称的结构类型
方法：省略名称
例：

~~~ cpp
struct//没有名称
{
    int x;
    int y;
}position;
~~~

由于没有名称，因此以后无法创建这种类型的变量

## 程序清单 4.13 arrstus.cpp

~~~ cpp
#include<iostream>
struct inflatable
{
	char name[20];
	float volume;
	double price;
};
int main()
{
	using namespace std;
	inflatable guests[2] =//数组初始化，guests本身是数组。
	{
		{"Bambi",0.5,21.99},
		{"Godzilla",2000,565.99}
	};
	cout << "The guests " << guests[0].name << " and " << guests[1].name
		<< "\nhave a combined volume of "
		<< guests[0].volume + guests[1].volume << " cubic feet.\n";
	return 0;
}
~~~

~~~
The guests Bambi and Godzilla
have a combined volume of 2000.5 cubic feet.
~~~

可以创建元素为结构的数组。
方法：与创建基本类型数组完全相同

结构数组中的每个元素可以使用成员运算符（.）

**初始化结构数组**
结合使用初始化数组的规则和初始化结构的规则。



![结构数组](结构数组.png)



## 程序清单 4.14 adress.cpp

~~~ cpp
#include<iostream>
int main() 
{
	using namespace std;
	int donuts = 6;
	double cups = 4.5;

	cout << "donuts value = " << donuts;
	cout << " and donuts address = " << &donuts << endl;
	cout << "cups value = " << cups;
	cout << " and cups address = " << &cups << endl;
	return 0;
}
~~~

~~~ cpp
donuts value = 6 and donuts address = 0095FA58
cups value = 4.5 and cups address = 0095FA48//十六进制
~~~

是用十六进制表示法（常用于表示内存）

使用常规变量时，值时指定的量，而地址为派生量。

## 程序清单 4.15 pointer.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	int updates = 6;
	int * p_updates;
	p_updates = &updates;

	cout << "Values: updates = "<<updates;
	cout << ", *p_updates = " << *p_updates << endl;

	cout << "Addresses: &updates = " << &updates;
	cout << ", p_updates = " << p_updates << endl;

	*p_updates = *p_updates + 1;
	cout << "Now updates = " << updates << endl;
	return 0;
}
~~~

~~~
Values: updates = 6, *p_updates = 6
Addresses: &updates = 010FF950, p_updates = 010FF950
Now updates = 7
~~~

指针用于储存值的地址。指针名表示的是地址。

` *`运算符被称为间接值或接触引用，将其运用到指针，可以得到该地址储存的值。(C++根据上下文确定*运算符是乘法还是解除引用)。

指针变量用` *`运算符来获得指针所指向的值。

变量用` &` 运算符来获得地址。

从输出结果可以看出，*p_updates与updates完全等价,两者数据类型相同，表示“值”。p_updates与&updates完全等价，两者数据类型相投，表示“地址”。



## 程序清单 4.16 init_ptr.cpp

~~~ cpp 
#include<iostream>
int main()
{
	using namespace std;
	int higgens = 5;
	int* pt = &higgens;//将pt的值设置为&higgens

	cout << "Value of higgens = " << higgens << "; Address of higgens = " 
        << &higgens << endl;
	cout << "Value of *pt = " << *pt << "; Value of pt = " << pt << endl;
	return 0;
}
~~~



~~~
Value of higgens = 5; Address of higgens = 005BF7B8
Value of *pt = 5; Value of pt = 005BF7B8
~~~

演示了如何将指针初始化为一个地址。在声明语句中初始化指针，注意：在这种情况下被初始化的是指针，而不是它指向的值。

**一定要在对指针应用接触引用运算符（*）之前，将指针初始化为一个确定的、适当的地址**

在声明指针时，` *` 不可或缺却,对于每一个指针变量名都需要一个` *`。
指针两边的空格是可选的，强调了不同的意义，但对于编译器来说在哪里添加空格没有区别。

C-格式：
` int *ptr`强调 ` *ptr`是一个int类型的值。

Ｃ++风格
` int* ptr` 强调` int*` 是一种类型（复合类型）——指向int的指针。

在这里说明的是：指针变量不仅仅是指针，而且是指向**特定类型**的指针。（与数组一样指针都是基于其他类型，指向的类型在指针声明时就已经被说明了）
例：

~~~Ｃ＋＋
double * tax_ptr;//tax_ptr的类型是指向double的指针（或double*）
char * str;//str是指向char的指针类型（或char*）
~~~

 

## 程序清单 4.17 use_new.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	int nights = 1001;
	int* pt = new int;//为int类型分配内存
	*pt = 1001;

	cout << "nights value = ";
	cout << nights << ": location " << &nights << endl;
	cout << " int ";
	cout << "value = " << *pt << ": location = " << pt << endl;
	double* pd = new double;//为double类型分配内存
	*pd = 10000001.0;

	cout << "double ";
	cout << "value = " << &pd << ": location = " << pd << endl;
	cout << "location of pointer pd: " << &pd << endl;
	cout << "size of pt = " << sizeof(pt);
	cout << "; size of *pt = " << sizeof(*pt) << endl;
	cout << "size of pd = " << sizeof pd;
	cout << "; size of *pd = " << sizeof(*pd) << endl;
	return 0;
}
~~~

~~~
nights value = 1001: location 001AFED0
 int value = 1001: location = 005CCA38
double value = 001AFEB8: location = 005CDB18
location of pointer pd: 001AFEB8
size of pt = 4; size of *pt = 4
size of pd = 4; size of *pd = 8
~~~



指针作用： 在运行阶段分配未命名的内存以储值。在这种情况下，只能通过指针来访问内存。

程序员要告诉new，需要为哪种数据类型分配指针；new将找到一个长度正确的内存块，并返回该内存块的地址，并返回内存块的地址。程序员的责任是将该地址赋给一个指针。

为一个数据对象（可以是结构,也可以是基本类型）获得并指定分配内存的通用格式：

> typeName * pointer_name = new typeName

地址本身只指出了对对象储存地址的开始，而没有指出其类型（使用的字节数）

new从被称为堆（heap）或自由储存区（free store）的内存区域分配内存。

## 程序清单 4.18 arraynew.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	double* p3 = new double[3];
	p3[0] = 0.2;
	p3[1] = 0.5;
	p3[2] = 0.8;
	cout << "p3[1] is " << p3[1] << ".\n";
	p3 = p3 + 1;
	cout << "Now p3[0] is " << p3[0] << " and ";
	cout << "p3[1] is " << p3[1] << ".\n";
	p3 = p3 - 1;
	delete[] p3;
	return 0;
}
~~~

~~~
p3[1] is 0.5.
Now p3[0] is 0.5 and p3[1] is 0.8.

~~~

将指针p3当作数组名来使用，p3[0]为第一个元素、、、

## 程序清单4.19 addpntrs.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	double wages[3] = { 10000.0,20000.0,30000.0 };
	short stacks[3] = { 3,2,1 };

	double* pw = wages;
	short* ps = &stacks[0];
	cout << "pw = " << pw << ", *pw = " << *pw << endl;
	pw = pw + 1;
	cout << "add 1 to the pw pointer:\n";
	cout << "pw = " << pw << ", *pw = " << *pw << "\n\n";
	cout << "ps = " << ps << ", *ps = " << *ps << endl;
	ps = ps + 1;
	cout << "add 1 to the ps pointer:\n";
	cout << "ps = " << ps << ", *ps = " << *ps << "\n\n";
	cout << "access two elements with array notation\n";
	cout << "stacks[0] = " << stacks[0] << ",stacks[1] = " << stacks[1] << endl;
	cout << "access two elements with pointer notation\n";
	cout << "*stacks = " << *stacks << ", *(stacks + 1) = " << *(stacks + 1) << endl;

	cout << sizeof(wages) << " = size of wages array\n";
	cout << sizeof(pw) << " = size of pw pointer\n";
	return 0;
}
~~~

~~~
pw = 00AFFDE4, *pw = 10000
add 1 to the pw pointer:
pw = 00AFFDEC, *pw = 20000

ps = 00AFFDD4, *ps = 3
add 1 to the ps pointer:
ps = 00AFFDD6, *ps = 2

access two elements with array notation
stacks[0] = 3,stacks[1] = 2
access two elements with pointer notation
*stacks = 3, *(stacks + 1) = 2
24 = size of wages array
4 = size of pw pointer
~~~

在多数情况下，C++将数组名解释为数组第一个元素的地址，例：

> double* pw = wages;

wages = &wages[0] = address of first element of array

## 程序清单 4.20 ptrstr.cpp

~~~ cpp
#include<iostream>
#include<cstring>
int main()
{
	using namespace std;
	char animal[20] = "bear";//创建char数组
	const char* bird = "wren";//创建指向指向char的指针，
	char* ps;//创建指向char的指针
	
	cout << animal << " and ";//打印animal
	cout << bird << "\n";//打印bird

	cout << "Enter a kind of aniaml: ";
	cin >> animal;
	
	ps = animal;
	cout << ps << "!\n";
	cout << "Before using strcpy():\n";
	cout << animal << " at " << (int*)animal << endl;
	cout << ps << " at " << (int*)ps << endl;
	//创建字符串副本
	ps = new char[strlen(animal) + 1];//分配内存，使用strlen确定字符串长度
	strcpy(ps, animal);//复制字符串，创建副本
	cout << "after using strcpy(): \n";
	cout << animal << " at " << (int*)animal << endl;//强制转换，使cout显示字符串地址
	cout << ps << " at " << (int*)ps << endl;
	delete[]ps;
	return 0;
}
~~~

~~~
bear and wren
Enter a kind of aniaml: fox
fox!
Before using strcpy():
fox at 009FF9E8
fox at 009FF9E8
after using strcpy():
fox at 009FF9E8
fox at 010A8BE8
~~~

在这里我们看到了指针与数组的奇妙关系，以及如何使用指针表示数组

在4.20中演示了如何使用不同形式的字符串。

在cout和多数C++表达式中，char数组名，char指针，以及用引号括起的字符串常量都被解释成字符串第一个字符的地址。

如果给cout提供一个指针，他将打印地址。但如果指针的类型为char*，则cout将显示指向的字符串。

如果要显示的是字符串的地址，则必须将这种指针强制转换为另一种指针类型

如果通过赋值语句将数组的赋给另一个数组，并不会复制字符串，只是复制地址，实质上，这两个指针指向相同的内存单元和字符串。



创建字符串副本：

- 分配内存以储存字符串。|
  方法：声明一个新数组，或使用new，使用new可以根据字符串长度来指定所需的空间
- 复制字符串到新空间中
  方法：strcpy（）或strncpy（）



## 程序清单4.21 newstrct.cpp

~~~ cpp
#include<iostream>
struct inflatable
{
	char name[20];
	float volume;
	double price;
};
int main()
{
	using namespace std;
	inflatable* ps = ps = new inflatable;
	cout << "Enter name of inflatable item: ";
	cin.get(ps->name, 20);
	cout << "Enter volume in cublic feet: ";
	cin >> (*ps).volume;
	cout << "Enter price: $";
	cin >> ps->price;
	cout << "Name: " << (*ps).name << endl;
	cout << "Volume: " << ps->volume << " cublic feet\n";
	cout << "Price: $" << ps->price << endl;
	delete ps;
	return 0;
}
~~~


~~~
Enter name of inflatable item: Fabulous Frodo
Enter volume in cublic feet: 1.4
Enter price: $27.99
Name: Fabulous Frodo
Volume: 1.4 cublic feet
Price: $27.99
~~~

使用new创建动态结构，在运行时创建数组优于在编译时创建数组，结构亦然

将new用于结构：

- 创建结构
- 访问成员

访问成员方法：

1. 使用箭头运算符

创建动态数组，不能将成员运算符用于结构名，应使用箭头成员运算符。
使用两种运算符的场景：

![image-20210724083156361](C:/Users/GrowlR/AppData/Roaming/Typora/typora-user-images/image-20210724083156361.png)

 

2. 利用优先规则。
   例：（*ps）.price

## 程序清单 4.22 delete.cpp

~~~ cpp
#include<iostream>
#include<cstring>
using namespace std;
char* getname(void);
int main()
{
	char* name;
	
	name = getname();
	cout << name << " at " << (int*)name << "\n";
	delete[]name;

	name = getname();
	cout << name << " at " << (int*)name << "\n";
	delete[]name;
	return 0;
}
char* getname()
{
	char temp[80];
	cout << "Enter last name: ";
	cin >> temp;
	char* pn = new char[strlen(temp) + 1];
	strcpy(pn, temp);

	return pn;
}
~~~

~~~
Enter last name: Fredeldumpkin
Fredeldumpkin at 0091CC10
Enter last name: Pook
Pook at 0091E0A8
~~~

虽然可以把new和delete分开，但这并不是一个好办法

## 程序清单 4.23 mixtypes.cpp

~~~ cpp
#include<iostream>
struct antarctica_years_end
{
	int year;

};
int main()
{
	antarctica_years_end s01, s02, s03;
	s01.year = 1998;
	antarctica_years_end* pa = &s02;
	pa->year = 1999;
	antarctica_years_end trio[3];
	trio[0].year = 2003;
	std::cout << trio->year << std::endl;
	const antarctica_years_end* arp[3] = { &s01,&s02,&s03 };
	std::cout << arp[1]->year << std::endl;
	const antarctica_years_end** ppa = arp;
	auto ppd = arp;
	std::cout << (*ppa)->year << std::endl;
	std::cout << (*(ppd + 1))->year<<std::endl;
	return 0;
}
~~~

~~~
2003
1999
1998
1999
~~~



## 程序清单 4.24 choices.cpp

~~~ cpp
#include<iostream>
#include<vector>
#include<array>
int main()
{
	using namespace std;
	double a1[4] = { 1.2,2.4,3.6,4.8 };
	vector<double>a2(4);
	a2[0] = 1.0 / 3.0;
	a2[1] = 1.0 / 5.0;
	a2[2] = 1.0 / 7.0;
	a2[3] = 1.0 / 9.0;
	array<double, 4>a3 = { 3.14,2.72,1.62,1.41 };
	array<double, 4>a4;
	a4 = a3;
	cout << "a1[2]: " << a1[2] << " at " << &a1[2] << endl;
	cout << "a2[2]: " << a2[2] << " at " << &a2[2] << endl;
	cout << "a3[2]: " << a3[2] << " at " << &a3[2] << endl;
	cout << "a4[2]: " << a4[2] << " at " << &a4[2] << endl;
	a1[-2] = 20.2;
	cout << "a1[-2]: " << a1[-2] << " at " << &a1[-2] << endl;//等效于*(a1-2)=20.2,而这是不安全的
	cout << "a3[2]: " << a3[2] << " at " << &a3[2] << endl;
	cout << "a4[2]: " << a4[2] << " at " << &a4[2] << endl;
	return 0;
}
~~~

~~~
a1[2]: 3.6 at 010FF93C
a2[2]: 0.142857 at 0144C360
a3[2]: 1.62 at 010FF8FC
a4[2]: 1.62 at 010FF8D4
a1[-2]: 20.2 at 010FF91C
a3[2]: 1.62 at 010FF8FC
a4[2]: 1.62 at 010FF8D4
~~~

vector和 array都可用标准数组表示法来访问各个元素。

array对象储存在相同的内存区域（栈）中，vector对象储存在（自由存储区或堆）中

可以将一个array对象赋给另一个array对象，，而对于数组，必须逐元素复制数据。

# 第五章

## 程序清单5.1 forloop.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	int i;
	for (i = 0; i < 5; i++)
	{
		cout << "C++ know loops.\n";
	};
	cout << "C++ knows when to stop.\n";
	return 0;
}
~~~

~~~
C++ know loops.
C++ know loops.
C++ know loops.
C++ know loops.
C++ know loops.
C++ knows when to stop.
~~~

## 程序清单 5.2num_test.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	cout << "Enter the starting countdown value: ";
	int limit;
	cin >> limit;
	int i;
	for (i = limit; i; i--)
		cout << "i = " << i << endl;
	cout << "Done now that i = " << i << endl;
	return 0;
}
~~~

~~~
Enter the starting countdown value: 5
i = 5
i = 4
i = 3
i = 2
i = 1
Done now that i = 0
~~~

循环在i变为0后结束

## 程序清单 5.3 express.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	int x;

	cout << "The expression x = 100 has the value ";
	cout << (x = 100) << endl;
	cout << "Now x = " << x << endl;
	cout << "The expression x < 3 has the value ";
	cout << (x < 3) << endl;
	cout << "The expression x > 3 has the value ";
	cout.setf(ios::boolalpha);
	cout << "The expression x < 3 has the value ";
	cout << (x < 3) << endl;
	cout << "The expression x > 3 has the value ";
	cout << (x > 3) << endl;
	return 0;
}
~~~

~~~
The expression x = 100 has the value 100
Now x = 100
The expression x < 3 has the value 0
The expression x > 3 has the value The expression x < 3 has the value false
The expression x > 3 has the value true
~~~

通常，cout在显示bool值之前将他们转换为int

## 程序清单 5.4 formore.cpp

~~~ cpp
#include<iostream>
const int ArSize = 16;
int main()
{
	long long factorials[ArSize];
	factorials[1] = factorials[0] = 1LL;
	for (int i = 2; i < ArSize; i++)
		factorials[i] = i * factorials[i - 1];
	for (int i = 2; i < ArSize; i++)
		std::cout << i << "! = " << factorials[i] << std::endl;
	return 0;
}
~~~

~~~
2! = 2
3! = 6
4! = 24
5! = 120
6! = 720
7! = 5040
8! = 40320
9! = 362880
10! = 3628800
11! = 39916800
12! = 479001600
13! = 6227020800
14! = 87178291200
15! = 1307674368000
~~~

利用数组来储存阶乘值。

## 程序清单5.5 bigstep.cpp

~~~ cpp
#include<iostream>
int main()
{
	using std::cout;//using声明
	using std::cin;//不是using 编译指令
	using std::endl;
	cout << "Enter an integer: ";
	int by;
	cin >> by;
	cout << "counting by " << "s:\n";
	for (int i = 0; i < 100; i = i + by)
		cout << i << endl;
	return 0;

}
~~~

~~~
Enter an integer: 17
counting by s:
0
17
34
51
68
85
~~~

## 程序清单 5.6 forstr1.cpp

~~~ cpp
#include<iostream>
#include<string>
int main()
{
	using namespace std;
	cout << "Enter a word: ";
	string word;
	cin >> word;

	for (int i = word.size() - 1; i >= 0; i--)
		cout << word[i];
	cout << "\nBye.\n";
	return 0;
}
~~~

~~~
Enter a word: animal
lamina
Bye.
~~~

## 程序清单 5.7 plus_one.cpp

~~~ cpp
#include<iostream>
int main()
{
	using std::cout;
	int a = 20;
	int b = 20;
	cout << "a = " << a << ":b = " << b << "\n";
	cout << "a++ = " << a++ << ": ++b = " << ++b << "\n";
	cout << "a = " << a << ": b = " << b << "\n";
	return 0;
}
~~~



~~~
a = 20:b = 20
a++ = 20: ++b = 21
a = 21: b = 21
~~~

## 程序清单 5.8 

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	cout << "The Amazing Accounto will sum and average ";
	cout << "five numbers for you.\n";
	cout << "Please enter five values:\n";
	double number;
	double sum = 0.0;
	for (int i = 1; i <= 5; i++)
	{
		cout << "Value " << i << ": ";
		cin >> number;
		sum+=number;
	}
	cout << "Five exquisite choices indeed! ";
	cout << "They sum to " << sum << endl;
	cout << "and average to " << sum / 5 << endl;
	cout << "The Amazing Accounto bids youadieu!\n";
	return 0;
}
~~~

~~~
The Amazing Accounto will sum and average five numbers for you.
Please enter five values:
Value 1: 1942
Value 2: 1948
Value 3: 1957
Value 4: 1974
Value 5: 1980
Five exquisite choices indeed! They sum to 9801
and average to 1960.2
The Amazing Accounto bids youadieu!
~~~

## 程序清单 5.9 forstr2.cpp

~~~ cpp
#include<iostream>
#include<string>
int main()
{
	using namespace std;
	cout << "Enter a word: ";
	string word;
	cin >> word;
	char temp;
	int i, j;
	for (j = 0, i = word.size() - 1; j < i; --i, ++j)
	{
		temp = word[i];
		word[i] = word[j];
		word[j] = temp;
	};
	cout << word << "\nDone\n";
	return 0;
}
~~~

~~~
Enter a word: streesed
deseerts
Done
~~~

~~~ cpp
#include<iostream>
#include<cstring>
int main()
{
	using namespace std;
	char word[5] = "?ate";
	for (char ch = 'a'; strcmp(word,"mate"); ch++)
	{
		cout << word << endl;
		word[0] = ch;
	}
	cout << "After loop ends, word is " << word << endl;
	return 0;
}
~~~

~~~
?ate
aate
bate
cate
date
eate
fate
gate
hate
iate
jate
kate
late
After loop ends, word is mate
~~~

## 程序清单 5.12 compstr2.cpp

~~~ cpp
#include<iostream>
#include<string>
int main()
{
	using namespace std;
	string word = "?ate";
	for (char ch = 'a'; word != "mate"; ch++)
	{
		cout << word << endl;
		word[0] = ch;
	}
	cout << "after loop ends, word is " << word << endl;
	return 0;
}
~~~

~~~ ?ate
?ate
aate
bate
cate
date
eate
fate
gate
hate
iate
jate
kate
late
after loop ends, word is mate
~~~

## 程序清单 5.13 while.cpp

~~~ cpp
#include<iostream>
const int ArSize = 20;
int main()
{
	using namespace std;
	char name[ArSize];
	cout << "Your first name, please: ";
	cin >> name;
	cout << "Here is your name, verticalized and ASCIIized:\n";
	int i = 0;
	while (name[i] != '\0')//遇到空字符时停止
	{
		cout << name[i] << ": " << int(name[i]) << endl;
		i++;
	}
	return 0;
}
~~~

~~~
Your first name, please: Muffy
Here is your name, verticalized and ASCIIized:
M: 77
u: 117
f: 102
f: 102
y: 121
~~~

循环遍历字符串，并显示其中的字符及其ASCII码。

可以测试数组中特定的字符是不是空值字符。

## 程序清单5.14 waiting.cpp

~~~ cpp
#include<iostream>
#include<ctime>
int main()
{
	using namespace std;
	cout << "Enter the delay time, in seconds: ";
	float secs;
	cin >> secs;
	clock_t delay = secs * CLOCKS_PER_SEC;
	cout << "starting\a\n";
	clock_t start = clock();
	while (clock() - start < delay)
		; 
	cout << "done \a\n";
	return 0;
}
~~~

## 程序清单 5.15 dowhile.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	int n;
	cout << "Enter number in the range 1-10 to find ";
	cout << "my favorite number\n";
	do
	{
		cin >> n;
	} while (n != 7);
	cout << "Yes, 7 is my favotite.\n";
	return 0;
}
~~~

~~~
Enter number in the range 1-10 to find my favorite number
9
4
7
Yes, 7 is my favotite.
~~~

## 程序清单 5.16 textin1.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	char ch;
	int count = 0;
	cout << "Enter characters; enter #to quit:\n";
	cin >> ch;//输入一个字符
	while (ch != '#')//入口条件循环
	{
		cout << ch;
		++count;
		cin >> ch;//cin将忽略空格和换行符
	}
	cout << endl << count << " characters read\n";
	return 0;
}
~~~

~~~
Enter characters; enter #to quit:
see ken run#really fast
seekenrun
9 characters read
~~~



在循环之前读取第一个输入字符。

使用cin输入空格和换行符不包括在计数内

## 程序清单5.17 textin2.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	char ch;
	int count = 0;

	cout << "Enter characters; enter # to quit:\n";
	cin.get(ch);
	while (ch != '#')
	{
		cout << ch;
		++count;
		cin.get(ch);
	}
	cout << endl << count << " characters read\n";
	return 0;
}
~~~

~~~
Enter characters; enter # to quit:
Did you use a #2 pencil?
Did you use a
14 characters read
~~~



## 程序清单 5.18 textin3.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	char ch;
	int count = 0;
	cin.get(ch);
	while (cin.fail()==false)
	{
		cout << ch;
		++count;
		cin.get(ch);
	}
	cout << endl << count << " characters read\n";
	return 0;
}

~~~

~~~
The green bird sings in the winter.
The green bird sings in the winter.
Yes, but the crow flies in the dawn.
Yes, but the crow flies in the dawn.
^Z

73 characters read
~~~

按下Ctrl+Z 和回车键来模拟EOF条件

检测到EOF后，cin将两位（eofbit和failbit）都设置为1（true）.可以通过成员函数eof来查看eofbit是否被设置；如果检测到EOF，则cin.eof()将返回bool值true，否则返回false，同样，如果eofbit或failbit被设置为1，则fail()成员函数返回true，否则返回false。这两周方法是事后报告吗，而不是预先报告，因此应将cin.eof()或cin.fail()测试放在读取后cin.fail()可用于更多实现。

cin.clear()方法可以清楚EOF标记

## 程序清单5.19textin.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	int ch;
	int count = 0;
	while ((ch = cin.get()) != EOF)
	{
		cout.put(char(ch));
		++count;
	}
	cout << endl << count << " characters read\n";
	return 0;
}
~~~

输出

~~~
The sullen mackerel sulks in the shadowy shallows.
The sullen mackerel sulks in the shadowy shallows.
Yes, but the blue bird of happiness harbors secrets.
Yes, but the blue bird of happiness harbors secrets.
^Z

104 characters read
~~~



表5.3：cin.get(ch)与ch=cin.get()的

| 属性                       | cin.get(ch)                           | ch=cin.get()       |
| -------------------------- | ------------------------------------- | ------------------ |
| 传递输入字符的方式         | 付给参数ch                            | 将函数返回值赋给ch |
| 用于字符输入时函数的返回值 | istream对象（执行bool转换之后为true） | int类型的字符编码  |
| 到达EOF时函数的返回值      | istream对象（执行bool转换后为false）  | EOF                |

## 程序清单5.20 nested.cpp

~~~ cpp
#include<iostream>
const int Cities = 5;
const int Years = 4;
int main()
{
	using namespace std;
	const char* cities[Cities] =
	{
		"Gribble City",
		"Gribbletown",
		"New Gribble",
		"San Gribble",
		"Gribble Vista"
	};

	int maxtemps[Years][Cities] =
	{
		{96,100,87,101,105},
		{96,98,91,107,104},
		{97,101,93,108,107},
		{98,103,95,109,108}
	};

	cout << "Maximum temperatures for 2008 - 2011\n\n";
	for (int city = 0; city < Cities; ++city)
	{
		cout << cities[city] << ":\t";
		for (int year = 0; year < Years; ++year)
		{
			cout << maxtemps[year][city] << "\t";
		}
		cout << endl;
	}
	return 0;
}
~~~

~~~
Maximum temperatures for 2008 - 2011

Gribble City:   96      96      97      98
Gribbletown:    100     98      101     103
New Gribble:    87      91      93      95
San Gribble:    101     107     108     109
Gribble Vista:  105     104     107     108

~~~

在输出中使用制表符比使用空格可使数据排列更有规律

从储存空间的角度，使用指针数组更为经济。如果要修改的话，二维数组更好。

# 第六章

设计智能程序的一个关键是使程序具有决策能力

## 6.1 if.cpp

~~~ cpp
#include<iostream>
int main()
{
	using std::cin;
	using std::cout;
	char ch;
	int spaces = 0;
	int total = 0;
	cin.get(ch);
	while (ch != '.')
	{
		if (ch == ' ')
		{
			++spaces;
		}
		++total;
		cin.get(ch);
	}
	cout << spaces << " spaces, " << total;

	cout << " characters total in sentence\n";
	return 0;
}
~~~

~~~
The balloonist was an airhead
with lofty goals.
6 spaces, 46 characters total in sentence
~~~

## 程序清单6.2 ifelse.cpp

~~~ cpp
#include<iostream>
int main()
{
	char ch;
	std::cout << "Type, and I shall repeat.\n";
	std::cin.get(ch);
	while (ch != '.')
	{
		if (ch == '\n')
		{
			std::cout << ch;
		}
		else
		{
			std::cout << ++ch;
		}
		std::cin.get(ch);
	}
	std::cout << "\nPlease excuse the slight confusion.\n";
	return 0;
}
~~~



## 程序清单 6.3 ifelseif.cpp

~~~ cpp
#include<iostream>
const int Fave = 27;
int main() {
	using namespace std;
	int n;
	cout << "Enter a number in the range 1-100 to find ";
	cout << "my favorite number: ";
	do
	{
		cin >> n;
		if (n<Fave)
		{
			cout << "Too low -- guess again: ";
		}
		else if(n>Fave)
		{
			cout << "Too high -- guess again: ";
		}
		else
		{
			cout << Fave << " is right!\n";
		}
	} while (n != Fave);
	return 0;
}
~~~

~~~
Enter a number in the range 1-100 to find my favorite number: 50
Too high -- guess again: 25
Too low -- guess again: 37
Too high -- guess again: 31
Too high -- guess again: 28
Too high -- guess again: 27
27 is right!
~~~

## 程序清单6.4.cpp

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	cout << "This program may reformat your hard disk\n"
		"and destroy all your data.\n"
		"Do you wish to continue?<y/n>";
	char ch;
	cin >> ch;
	if (ch == 'y'||ch=='Y')
	{
		cout << "You were warned!\a\a\n";
	}
	else if (ch == 'n'||ch == 'N')
	{
		cout << "A wise choice .. bye\n";
	}
	else
	{
		cout << "That wasn't a y or n! Apparently you "
			"can't follow\ninstructions, so "
			"I'll trash your disk anyway/\a\a\a\n";
	}
	return 0;
}
~~~

~~~
This program may reformat your hard disk
and destroy all your data.
Do you wish to continue?<y/n>N
A wise choice .. bye
~~~



## 程序清单6.5or.cpp

~~~ cpp
#include<iostream>
const int ArSize = 6;
int main()
{
	using namespace std;
	float naaq[ArSize];
	cout << "Enter the NAAQs (New Age Awareness Quotients) "
		<< "of\nyour neighbors. Program"
		<< "when you make\n" << ArSize << " entries "
		<< "or enter a negative value.\n";

	int i = 0;
	float temp;
	cout << "First value: ";
	cin >> temp;
	cout << "First value: ";
	cin >> temp;
	while (i<ArSize && temp>=0)
	{

		naaq[i] = temp;
		++i;
		if (i<ArSize)
		{
			cout << "Next value: ";
			cin >> temp;
		}
	}
	if (i==0)
	{
		cout << "No data--bye\n";
	}
	else
	{
		cout << "Enter your NAAQ: ";
		float you;
		cin >> you;
		int count = 0;
		for (int j = 0; j < i; j++)
		{
			if (naaq[j] > you)
			{
				++count;
			}
		}
		cout << count;
		cout << " of your neighbors have greater awareness of\n"
			<< "the New Age then you do.\n";
	}
	return 0;
}
~~~

~~~
~~~

## 程序清单6.6

~~~ cpp
#include<iostream>
const char* qualify[4] =
{
	"10,000-meter race.\n",
	"mud tug-of-war.\n",
	"masters canoe jousting.\n",
	"pie-throwing festival.\n"
};
int main()
{
	using namespace std;
	int age;
	cout << "Enter your age in years: ";
	cin >> age;
	int index;

	if (age>17&&age<35)
	{
		index = 0;
	}
	else if(age >= 35 && age<50)
	{
		index = 1;
	}
	else if(age>=50&&age<65)
	{
		index = 2;
	}
	else
	{
		index = 3;
	}
	cout << "You qialify for the " << qualify[index];
	return 0;
}
~~~

## 6.7

~~~ cpp
#include<iostream>
#include<climits>
bool is_int(double);
int main()
{
	using namespace std;
	double num;

	cout << "Yo, dube! Enter an integer value: ";
	cin >> num;
	while (!is_int(num))
	{
		cout << "Out of range -- please try again: ";
		cin >> num;
	}
	int val = int(num);
	cout << "You're entered the integer " << val << "\nBye\n";
	return 0;
}
bool is_int(double x)
{
	if (x <= INT_MAX && x >= INT_MIN)
	{
		return true;
	}
	else
	{
		return false;
	}
}
~~~

## 6.9

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	int a, b;
	cout << "Enter two integers: ";
	cin >> a >> b;
	cout << "The larger of " << a << " and " << b;
	int c = a > b ? a : b;
	cout << " is " << c << endl;
	return 0;
}
~~~

## 6.10

~~~ cpp
#include<iostream>
using namespace std;
void showmenu();
void report();
void comfort();
int main()
{
	showmenu();
	int choice;
	cin >> choice;
	while (choice!=5)
	{
		switch (choice)
		{
		case 1:cout << "\a\n";
			break;
		case 2:report();
			break;
		case 3:cout << "The boss was in all day.\n";
			break;
		case 4:comfort();
			break;
		default:cout << "That's not a choice.\n";
			break;
		}
		showmenu();
		cin >> choice;
	}
	cout << "Bye!\n";
	return 0;
}
void showmenu()
{
	cout << "Please enter 1, 2, 3, 4 or 5:\n"
		"1) alarm           2) report\n"
		"3) alibi           4) comfort\n"
		"5) quit\n";
};
void report()
{
	cout << "It's been an excellent week for business.\n"
		"Sales are up 120%. Expense are down 35%.\n";
}
void comfort()
{
	cout << "Your employees think you are finest CEO\n"
		"in the industry.The board of directors think\n"
		"you are the finest CEO in the industry.\n";
}

~~~

## 6.11

~~~ cpp

~~~

## 6..12

~~~ cpp
#include<iostream>
const int ArSize = 80;
int main()
{
	using namespace std;
	char line[ArSize];
	int spaces = 0;
	
	cout << "Enter a line of text: \n";
	cin.get(line, ArSize);
	cout << "Complete line:\n" << line << endl;
	cout << "Line through first period:\n";
	for (int i = 0;line[i] !='0'; i++)
	{
		cout << line[i];
		if (line[i] == '.')
		break;
		if (line[i]!=' ')
		{
			continue;
		}
		spaces++;
	}
	cout << "\n" << spaces << " spaces\n";
	cout << "Done.\n";
	return 0;
}
~~~



## 6.13

~~~ cpp
#include<iostream>
const int ArSize = 80;
int main()
{
	using namespace std;
	char line[ArSize];
	int spaces = 0;
	
	cout << "Enter a line of text: \n";
	cin.get(line, ArSize);
	cout << "Complete line:\n" << line << endl;
	cout << "Line through first period:\n";
	for (int i = 0;line[i] !='0'; i++)
	{
		cout << line[i];
		if (line[i] == '.')
		break;
		if (line[i]!=' ')
		{
			continue;
		}
		spaces++;
	}
	cout << "\n" << spaces << " spaces\n";
	cout << "Done.\n";
	return 0;
}
~~~

## 6.13 

~~~ cpp
#include<iostream>
const int Max = 5;
int main()
{
	using namespace std;
	double fish[Max];
	cout << "Please enter the weights of your fish.\n";
	cout << "You may enter up to " << Max
		<< " fish <q to terminate>.\n";
	cout << "fish #1: ";
	int i = 0;
	while (i<Max && cin >> fish[i]) {//cin>>fish[i]是cin方法函数调用，该函数返回cin，若处在测试条件中则会被转换成bool类型。如果输入成功，则转换后的值为true，否则为false
		if (++i < Max)
			cout << "fish #" << i + 1 << ": ";
	}
	double total = 0.0;
	for (int j = 0; j < i; j++)
	{
		total += fish[j];
	}
	if (i == 0)
	{
		cout << "No fish\n";
	}
	else
	{
		cout << total / i << " = average weight of "
			<< i << " fish\n";
	}
	cout << "Done.\n";
	return 0;
}
~~~

## 6.14

~~~ cpp
#include<iostream>
const int Max = 5;
int main()
{
	using namespace std;
	int golf[Max];
	cout << "Please enter your golf scores.\n";
	int i;
	for ( i = 0; i < Max; i++)
	{
		cout << "round #" << i + 1 << ": ";
		while (!(cin>>golf[i]))
		{
			cin.clear();//用clear重置输入，如果省略这条语句，程序将拒绝急继续输入。
			while (cin.get()!='\n')
			{
				continue;
			}
			cout << "Please enter a number: ";
		}
	}
	double total = 0.0;
	for (i = 0; i < Max; i++)
	{
		total += golf[i];
	}
	cout << total / Max << " = average score "
		<< Max << " rounds\n";
	return 0;
}
~~~

## 6.15

这个例子介绍了简单文件输入\输出

**使用文本输出的主要步骤：**

1. 包含头文件fstream
2. 创建一个ofstream
3. 将该ofstream对象同一个文件关联起来
4. 就像使用cout那样使用ofstream对象

~~~ cpp
#include<iostream>
#include<fstream>
int main()
{
	using namespace std;
	
	char automobile[50];
	int year;
	double a_price;
	double d_price;

	ofstream outFile; //创建名为outFile的ofstream对象
	outFile.open("carinfo.txt");

	cout << "Enter the make and model of automobile: ";
	cin.getline(automobile, 50);
	cout << "Enter the model year: ";
	cin >> year;
	cout << "Enter the original asking price: ";
	cin >> a_price;
	d_price = 0.913 * a_price;

	cout << fixed;//以普通方式输出，非科学计数法
	cout.precision(2);//在输出的时候设定输出值以新的浮点数精度值显示，即小数点后保留2位
	cout.setf(ios_base::showpoint);//显示小数点和额外的零，即使不需要.
	cout << "Make and model: " << automobile << endl;
	cout << "Year: " << year << endl;
	cout << "Was asking $" << a_price << endl;
	cout << "Now asking $" << d_price << endl;

	outFile << fixed;//以普通方式输出，非科学计数法
	outFile.precision(2);//在输出的时候设定输出值以新的浮点数精度值显示，即小数点后保留2位
	outFile.setf(ios_base::showpoint);//显示小数点和额外的零，即使不需要.
	outFile << "Make and model: " << automobile << endl;
	outFile << "Year: " << year << endl;
	outFile << "Was asking $" << a_price << endl;
	outFile << "Now asking $" << d_price << endl;

	outFile.close();//程序使用完文件之后将其关闭，方法close（）不需要使用文件名作为参数
	return 0;
}
~~~

## 6.16

控制台输入

- 必须包含头文件iostream
- 头文件iostream定义了一个用处理输入的istream类
- 头文件iostream声明了一个名为cin的istream变量（对象）
- 必须指明名称空间std；
- 可以结合使用cin和运算符>>来读取各种类型的数据
- 可以使用cin和get()方法来读取一个字符，使用cin和getline()来读取一行字符
- 可以结合使用cin和eof()、fail()方法来判断输入是否成功。
- 对象cin本身被用作测试条件时，如果最后一个读取操作成功，他将被转换为布尔值true，否则被转换为false。

文件输出

- 必须包含头文件fstream。
- 头文件fstream定义了一个用于处理输入的ifstream类。
- 需要声明一个或多个ifstream变量（对象）并命名(须遵循命名规则)
- 必须指明名称空间std；
- 需要将ifstream对象与文件关联起来。为此，方法之一是使用open()方法。
- 使用完文件后，应使用close()方法将其关闭。
- 可结合使用ifstream对象和get()方法来读取一个字符，使用ifstream对象和geiline()来读取一行字符。
- 可以结合使用ifstream和eof()、fail()等方法来判断输入是否成功。
- ifstream被当做判断条件时与对象cin一样。



**声明一个ifstream对象并将其同文件关联起来后，便可以像使用cin那样使用它，所有可用于cin的操作和方法都可用于ifstream对象。**

~~~ cpp
#include<iostream>
#include<fstream>
#include<cstdlib>
const int SIZE = 60;
int main()
{
	using namespace std;
	char filename[SIZE];
	ifstream inFile;
	cout << "Enter name of data file: ";
	cin.getline(filename, SIZE);
	inFile.open(filename);
    //检测文件是否能打开
	if (!inFile.is_open())
	{
		cout << "Could not open the file " << filename << endl;
		cout << "Program terminating.\n";
		exit(EXIT_FAILURE);
	}
	double value;
	double sum = 0.0;
	int count = 0;

	inFile >> value;
    //使用good()方法，该方法在没有发生任何错误时返回true
	while (inFile.good())
	{
		++count;
		sum += value;
		inFile >> value;
	}
    //检测循环终止的原因
	if (inFile.eof())
		cout << "End of file reached.\n";
	else if (inFile.fail())
		cout << "Input terminated by data mismatch.\n";
	else
	{
		cout << "Input terminated for unknown reason.\n";
	}
	if (count == 0)
	{
		cout << "No data processed.\n";
	}
	else
	{
		cout << "Items read: " << count << endl;
		cout << "Sum: " << sum << endl;
		cout << "Average: " << sum / count << endl;
	}
	inFile.close();
	return 0;
}

~~~





精简语句：

~~~ cpp
inFile >> value;//获得第一个值
//使用good()方法，该方法在没有发生任何错误时返回true
while (inFile.good())
{
	//此处为循环体
	inFile >> value;
}
~~~

为

~~~ cpp
while(inFile >> value)
{
    //此处为循环体
}
~~~

# 第七章

要使用C++函数，必须完成：

- 提供函数定义
- 提供函数原型
- 调用函数

## 7.1

~~~ cpp
#include<iostream>

void simple();

int main()
{
	using namespace std;
	cout << "main() will call the simple() function:\n";
	simple();
	cout << "main() is finished with the simple() function.\n";
	return 0;
}
void simple()
{
	using namespace std;
	cout << "I'm but a simple function.\n";
}
~~~

## 7.2

~~~ cpp
#include<iostream>
void cheers(int);
double cube(double x);
int main()
{
	using namespace std;
	cheers(5);
	cout << "Give me a number: ";
	double side;
	cin >> side;
	double volume = cube(side);
	cout << "A " << side << "-foot cube has a volume of ";
	cout << volume << " cubic feet.\n";
	cheers(cube(2));
	return 0;
}
void cheers(int n)
{
	using namespace std;
	for (int i = 0; i < n; i++)
	{
		cout << "Cheers! ";
	}
	cout << endl;
}
double cube(double x)
{
	return x * x * x;
}

~~~

只有在函数使用了名称空间std中的成员时，才在该函数中使用了编译指令using

原型描述了编译器的接口

在C++中，原型是必不可少的

原型的功能：
原型保证以下几点：

- 编译器正确处理函数返回值
- 编译器检查使用的参数数目是否正确
- 编译器检查使用的参数类型是否正确；如果不正确，则转换为正确的类型。（如果可能的话）

## 7.3

~~~ cpp
#include<iostream>
using namespace std;
void n_chars(char, int);
int main()
{
	int times;
	char ch;

	cout << "Enter a chararcter: ";
	cin >> ch;
	while (ch!='q')
	{
		cout << "Enter an integer: ";
		cin >> times;
		n_chars(ch, times);
		cout << "\nEnter another character or press the"
			" q-key to quit: ";
		cin >> ch;
	}
	cout << "The value of times is " << times << ".\n";
	cout << "Bye\n";
	return 0;
}
void n_chars(char c, int n)
{
	while (n-- > 0)
	{
		cout << c;
	}
}
~~~

cin.get()函数读取所有的输入字符，包括空格和换行符。

cin>>ch方法可以轻松跳过这些换行符

## 7.4

~~~ cpp
#include<iostream>
long double probability(unsigned numbers, unsigned picks);
int main()
{
	using namespace std;
	double total, choices;
	cout << "Enter the total number of choices o the game card and\n"
		"the number of picks allowed:\n";
	while ((cin>>total>>choices)&&choices<=total)
	{
		cout << "You have one chance in ";
		cout << probability(total, choices);
		cout << " of winning.\n";
		cout << "Next two numers (q to quit): ";
	}
	cout << "bye\n";
	return 0;
}
long double probability(unsigned numbers, unsigned picks)
{
	long double result = 1.0;
	long double n;
	unsigned p;

	for (n = numbers, p = picks; p > 0; n--, p--)
	{
		result = result * n/p;
		return result;
	}
}
~~~

## 7.5

~~~ cpp
#include<iostream>
const int ArSize = 8;
int sum_arr(int arr[], int n);
int main()
{
	using namespace std;
	int cookies[ArSize] = { 1,2,4,8,16,32,64,128 };

	int sum = sum_arr(cookies, ArSize);
	cout << "Toatal cookies eaten: " << sum << "\n";
	return 0;
}

int sum_arr(int arr[], int n)
{
	int total = 0;

	for (int i = 0; i < n; i++)
	{
		total = total + arr[i];
	}
	return total;
}

~~~

在大多数情况下，C++和C语言一样，也将数组名视为指针。

C++将数组名解释为其第一个元素的地址。

例外：

- 数组声明使用数组来标记存储位置；
- 其次，对数组名使用sizeof将得到整个数组的长度（一字节为单位）
- 将地址运算符&用于数组名时，将返回整个数组的地址

因此函数传递的是地址。

其中：可以将

~~~ cpp
int sum_arr(int arr[], int n)
~~~

换成

~~~ cpp
int sum_arr(int * arr, int n)
~~~

而这两个函数头都是正确的，当且仅当用于函数头，或函数原型中，` int * arr`和` int arr[]`的和含义是相同的

数组表示法（int arr[])提示用户，arr不仅指向int，还指向int数组的第一个int。

**两个恒等式：**

~~~ cpp
arr[i] == *(arr + i)
&arr[i] == arr + I
~~~

**将指针（包括数组名）加 1 ，实际上是加上了一个与指针指向的类型的长度（以字节为单位）相等的值。对于遍历数组而言，使用指针加法和数组下标实际上是等效的。**

7.5将数组的位置（地址）、包含的元素种类（类型）以及元素种类（n变量）提交给函数。有了这些信息后，函数便可以使用原来的数组。传递常规变量时，函数将使用该变量的拷贝；但传递数组时，函数将使用原来的数组。

将数组地址作为参数可以节省整个数组所需的时间和内存。

使用原始数据增加了破坏数据的风险。但是用const限定符可以解决。

## 7.6

~~~ cpp
#include<iostream>
const int ArSize = 8;
int sum_arr(int arr[], int n);

int main()
{
	int cookies[ArSize] = { 1,2,4,8,16,32,64,128 };
	std::cout << cookies << " = array address, ";
	
	std::cout << sizeof(cookies) << " = sizeof cookies\n";
	int sum = sum_arr(cookies, ArSize);
	std::cout << "Total cookies eaten: " << sum << std::endl;
	sum = sum_arr(cookies, 3);
	std::cout << "First three eaters ate " << sum << " cookies.\n";
	sum = sum_arr(cookies + 4, 4);
	std::cout << "Last four eaters ate " << sum << " cookies.\n";
	return 0;
}
int sum_arr(int arr[], int n)
{
	int total = 0;
	std::cout << arr << " = arr";
	std::cout << sizeof(arr) << " = sizeof arr\n";
	for (int i = 0; i < n; i++)
		total = total + arr[i];
	return 0;

}
~~~



## 7.7 

~~~ cpp
#include<iostream>
const int Max = 5;

int fill_array(double ar[], int limit);
void show_array(const double ar[], int n);
void revalue(double r, double ar[], int n);

int main()
{
	using namespace std;
	double properties[Max];

	int size = fill_array(properties, Max);
	show_array(properties, Max);
	if (size > 0)
	{
		cout << "Enter revaluation factor: ";
		double factor;
		while (!(cin>>factor))
		{
			cin.clear();
			while (cin.get()!='\n')
			{
				continue;
			}
			cout << "Bad input; Please enter a number: ";
		}
		revalue(factor, properties, size);
		show_array(properties, size);
	}
	cout << "Done,\n";
	cin.get();
	cin.get();
	return 0;
}
int fill_array(double ar[], int limit)
{
	using namespace std;
	double temp;
	int i;
	for (i = 0; i < limit; i++)
	{
		cout << "Enter value #" << (i + 1) << ":";
		cin >> temp;
		if (!cin)
		{
			cin.clear();
			while (cin.get()!= 'n')
			{
				continue;
			}
			cout << "Bad input; input process terminated.\n";
			break;
		}
		else if (temp < 0)
		{
			break;
		}
		ar[i] = temp;
	}
	return 0;
}
void show_array(const double ar[], int n)
{
	using namespace std;
	for (int i = 0; i < n; i++)
	{
		cout << "Property #" << (i + 1) << ": $";
		cout << ar[i] << endl;
	}
}
void revalue(double r, double ar[], int n)
{
	for (int i = 0; i < n; i++)
	{
		ar[i] *= r;
	}
}
~~~



## 7.8

使用数组区间的函数



~~~ cpp
#include<iostream>
const int ArSize = 8;
int sum_arr(const int* begin, const int* end);
int main()
{
	using namespace std;
	int cookies[ArSize] = { 1,2,4,8,16,32,64,128 };
	
	int sum = sum_arr(cookies, cookies + ArSize);
    //指针cookies + ArSize指向最后一个元素后面的一个位置
	cout << "Total cookies eaten: " << sum << endl;
	sum = sum_arr(cookies,cookies + 3);
	cout << "First three eaters ate " << sum<<" cookies.\n";
	sum = sum_arr(cookies + 4, cookies + 8);
	cout << "Last four eaters ate " << sum << " cookies.\n";
	return 0;
}
int sum_arr(const int* begin, const int* end)
{
	const int* pt;
	int total = 0;

	for (pt = begin; pt != end; pt++)
	{
		total = total + *pt;
	}
	return 0;
}
~~~

数组名被视为其地址

## 7.9

~~~ cpp
#include<iostream>
unsigned int c_int_str(const char* str, char ch);
int main()
{
	using namespace std;
	char mmm[15] = "minimum";

	//char* wail = "ululate";
	//const char* wail = "ululate";
	//char* wail = (char*)"ululate";
	//char wail[15] = "ululate";
	char* wail = const_cast<char*>("ululate");
	//char* wail_window = wail;
	unsigned int ms = c_int_str(mmm, 'm');
	unsigned int us = c_int_str(wail, 'u');
	cout << ms << " m chararcters in " << mmm << endl;
	cout << us << " u characters in " << wail << endl;
	return 0;
	
}
unsigned int c_int_str(const char* str, char ch)
{
	unsigned int count = 0;

	while (*str)
	{
		if (*str == ch)
			count++;
		str++;
	}
	return count;
}
~~~



处理字符串中字符的标准样式：

~~~ cpp
while(*str)
{
    statements
    str++;
}
~~~

str最初指向字符串的第一个字符，因此` *str`表示的是第一个字符。

## 7.10

~~~ cpp
#include<iostream>
char* buildstr(char c, int n);
int main()
{
	using namespace std;
	int times;
	char ch;
	cout << "Enter a character: ";
	cin >> ch;
	cout << "Enter an integer: ";
	cin >> times;
	char* ps = buildstr(ch, times);
	cout << ps << endl;
	delete[]ps;
	ps = buildstr('+', 20);
	cout << ps << "-DONE-" << ps << endl;
	delete[]ps;
	return 0;
}
char* buildstr(char c, int n)
{
	char* pstr = new char[n + 1];//多余的一空间储存控制字符
	pstr[n] = '\0';
	while (n-- >0)//从后往前填充数组。  
	{
		pstr[n] = c;
	}
	return pstr;
}
~~~

函数无法返回一个字符串，但可以反回字符串的地址，这样做的效率更高。      

## 7.11

~~~ cpp

#include<iostream>
struct travel_time
{
	int hours;
	int mins;
};
const int Mins_per_hr = 60;

travel_time sum(travel_time t1, travel_time t2);
void show_time(travel_time t);
int main()
{
	using namespace std;
	travel_time day1 = { 5,45 };
	travel_time day2 = { 4,55 };

	travel_time trip = sum(day1, day2);
	cout << "Two-day total: ";
	show_time(trip);

	travel_time day3 = { 4,32 };
	cout << "Three-day total: ";
	show_time(sum(trip, day3));

	return 0;
}
travel_time sum(travel_time t1, travel_time t2)
{
	travel_time total;

	total.mins = (t1.mins + t2.mins) % Mins_per_hr;
	total.hours = t1.hours + t2.hours + (t1.mins + t2.mins) / Mins_per_hr;

	return total;
}
void show_time(travel_time t)
{
	using namespace std;
	cout << t.hours << " hours, "
		<< t.mins << "minutes\n";
}
~~~

## 7.12

~~~ cpp
#include<iostream>
#include<cmath>

struct polar
{
	double distance;
	double angle;
};
struct rect
{
	double x;
	double y;
};
polar rect_to_polar(rect xypos);
void
show_polar(polar dapos);

int main()
{
	using namespace std;
	rect rplace;
	polar pplace;

	cout << "Enter the x and y values: ";
	while (cin>>rplace.x>>rplace.y)//cin将被转换为bool
	{
		pplace = rect_to_polar(rplace);
		show_polar(pplace);
		cout << "Next two number(q to quit): ";
	}
	cout << "Done.\n";
	return 0;
}
polar rect_to_polar(rect xypos)
{
	using namespace std;
	polar answer;

	answer.distance =
		sqrt(xypos.x * xypos.x + xypos.y * xypos.y);
	answer.angle = atan2(xypos.y, xypos.x);
	return answer;
}
void show_polar(polar dapos)
{
	using namespace std;
	const double Rad_to_deg = 57.29577951;

	cout << "distance = " << dapos.distance;
	cout << ",angle = " << dapos.angle * Rad_to_deg;
	cout << " degrees\n";
}
~~~

## 7.13

~~~ cpp
#include<iostream>
#include<cmath>

struct polar
{
	double distance;
	double angle;
};
struct rect
{
	double x;
	double y;
};
void rect_to_polar(const rect* pxy, polar* pda);
void show_polar(const polar* pda);
int main()
{
	using namespace std;
	rect rplace;
	polar pplace;

	cout << "Enter hte x and y value: ";
	while (cin>>rplace.x>>rplace.y)
	{
		rect_to_polar(&rplace, &pplace);
		show_polar(&pplace);
		cout << "Next two number ( q to quit)";
	}
	cout << "Done.\n";
	return 0;
}
void show_polar(const polar* pda)
{
	using namespace std;
	const double Rad_to_deg = 57.29577951;
	cout << "distance = " << pda->distance;
	cout << ", angle = " << pda->angle * Rad_0to_deg;
	cout << " degress\n";
}
void rect_to_polar(const rect* pxy, polar* pda)
{
	using namespace std;
	pda->distance =
		sqrt(pxy->x * pxy->x + pxy->y * pxy->y);
	pda->angle = atan2(pxy->y, pxy->x);
}
~~~



7.13使用的是指针，让函数能够对原始结构进行操作；

## 7.14

~~~ cpp 
#include<iostream>
#include<string>
using namespace std;
const int SIZE = 5;
void display(const string sa[], int n);
int main()
{
	string list[SIZE];
	cout << "Enter your " << SIZE << " favorite astronomical sights:\n";
	for (int i = 0; i < SIZE; i++)
	{
		cout << i + 1 << ": ";
		getline(cin,list[i]);
	}
	cout << "Your list:\n";
	display(list,SIZE);

	return 0;
}
void display(const string sa[], int n)
{
	for (int i = 0; i < n; i++)
		cout << i + 1 << ": " << sa[i] << endl;
}
~~~

如果需要string数组，只需要试用通常的数组声明格式即可。

## 7.15

~~~ cpp
#include<iostream>
#include<array>
#include<string>
const int Seasons = 4;
const std::array<std::string, Seasons>Snames =
{
	"Spring","Summer","Fall","Winter"
};
void fill(std::array<double, Seasons> *pa);
void show(std::array<double, Seasons> da);

int main()
{
	std::array<double, Seasons>expenses;
	fill(&expenses);
	show(expenses);
	return 0;
}
void fill(std::array<double, Seasons>* pa)
{
	using namespace std;
	for (int i = 0; i < Seasons; i++)
	{
		cout << "Enter " << Snames[i] << " expenses: ";
		cin >> (*pa)[i];
	}
}
void show(std::array<double, Seasons>da)
{
	using namespace std;
	double total = 0.0;
	cout << "\nEXPENSES\n";
	for (int i = 0; i < Seasons; i++)
	{
		cout << Snames[i] << ": $" << da[i] << endl;
		total += da[i];
	}
	cout << "Total Expenses: $" << total << endl;
}
~~~

## 7.16

~~~ cpp
#include<iostream>
void countdown(int n);

int main()
{
	countdown(4);
	return 0;
}
void countdown(int n)
{
	using namespace std;
	cout << "Counting down ... " << n << endl;
	if (n>0)
	{
		countdown(n - 1);
	}
	cout << n << ": Kaboom!\n";
}
~~~

函数递归调用

## 7.17



在需要将一项工作不断分为两箱较小的、类似的工作时，递归非常有用。

递归又称分而治之策略（divide-and0conquer strategy)

~~~ cpp 
#include<iostream>
const int Len = 66;
const int Divs = 6;
void subdivide(char ar[], int low, int high, int level);
int main()
{
	char ruler[Len];
	int i;
	for (i = 1; i < Len - 2; i++)
	{
		ruler[i] = '\0';
	}//ruler from 1 to 63 填充'\0'字符
	ruler[Len - 1] = '\0';//ruler 65 填充 '\0'
	int max = Len - 2; //max = 64
	int min = 0;
	ruler[min] = ruler[max] = '|';//ruler 0 and 64 填充'|'
	std::cout << ruler << std::endl;//打印ruler
	for (i = 1; i <= Divs; i++)
	{
		subdivide(ruler, min, max, i);
		std::cout << ruler << std::endl;
		for (int j = 1; j < Len - 2; j++)
		{
			ruler[j] = ' ';
		}
	}
	return 0;
}
void subdivide(char ar[], int low, int high, int level)
{
	if (level == 0)
	{
		return;
	}
	int mid = (high + low) / 2;
	ar[mid] = '|';
	subdivide(ar, low, mid, level - 1);
	subdivide(ar, mid, high, level - 1);
}
~~~

subdivide()函数利用变量level来控制递归层。

## 7.18

函数也有地址。函数的地址是储存其机器语言代码的内存的开始地址。

允许在不同的时间传递不同函数的地址，这意味着可以再不同的时间使用不同的函数。

要用函数指针：

- 获取函数的地址
  只要使用函数名（后面不跟参数）
- 声明一个函数指针
- 使用函数指针来调用函数

~~~ cpp
#include<iostream>
double betsy(int);
double pam(int);

void estimate(int lines, double (*pf)(int));
int main()
{
	using namespace std;
	int code;
	cout << "How many lines of code do you need? ";
	cin >> code;
	cout << "Here's Betsy's estimate:\n";
	estimate(code, betsy);
	cout << "Here's Pam's estimate:\n";
	estimate(code, pam);
	return 0;
}
double betsy(int lns)
{
	return 0.05 * lns;
}
double pam(int lns)
{
	return 0.03 * lns + 0.0004 * lns * lns;
}
void estimate(int lines, double(*pf)(int))//利用函数指针调用函数
{
	using namespace std;
	cout << lines << " lines will take ";
	cout << (*pf)(lines) << "hour(s)\n";
}
~~~

## 7.19

~~~ cpp
#include<iostream>
const double* f1(const double ar[], int n);
const double* f2(const double[], int);
const double* f3(const double*, int);

int main()
{
	using namespace std;
	double av[3] = { 1112.3,1542.6,2227.9 };

	const double* (*p1)(const double*, int) = f1;
	auto p2 = f2;

	cout << "Using pointers to functionsL\n";
	cout << " Address Value\n";
	cout << (*p1)(av, 3) << ": " << *(*p1)(av, 3) << endl;
	cout << p2(av, 3) << ": " << *p2(av, 3) << endl;
	const double* (*pa[3])(const double*, int) = { f1,f2,f3 };

	auto pb = pa;

	cout << "\nUsing an array of pointer to function:\n";
	cout << " Address Value\n";
	for (int i = 0; i < 3; i++)
	{
		cout << pb[i](av, 3) << ": " << *pb[i](av, 3) << endl;

	}

	cout << "\nUsing pointers to an array of pointers:\n";
	cout << " Address Value\n";

	auto pc = &pa;
	cout << (*pc)[0](av, 3) << ": " << *(*pc)[0](av, 3) << endl;
	const double* (*(*pd)[3])(const double*, int) = &pa;
	const double* pdb = (*pd)[1](av, 3);
	cout << pdb << ": " << *pdb << endl;
	cout << (*(*pd)[2])(av, 3) << ": " << *(*(*pd))(av, 3) << endl;
	return 0;
}
const double* f1(const double* ar, int n)
{
	return ar;
}
const double* f2(const double ar[], int n)
{
	return ar + 1;
}
const double* f3(const double ar[], int n)
{
	return ar + 2;
}
~~~

# 第8章

## 8.1

~~~ cpp
#include<iostream>
inline double square(double x) { return x * x; }

int main()
{
	using namespace std;
	double a, b;
	double c = 13.0;

	a = square(5.0);
	b = square(13.0);

	cout << "a = " << a << ",b = " << b << "\n";
	cout << "c = " << c;
	cout << ", c square = " << square(c++) << "\n";
	cout << "Now c= " << c << "\n";
	return 0;
}

~~~

## 8.2

~~~ cpp
#include<iostream>
int main()
{
	using namespace std;
	int rats = 101;
	int& rodents = rats;
	cout << "rats = " << rats;
	cout << ", rodents = " << rodents << endl;
	rodents++;
	cout << "rats = " << rats;
	cout << ", rodents = " << rodents << endl;
	cout << "rats address = " << &rats;
	cout << ", rodents address = " << &rodents << endl;
	return 0;
}

~~~

## 8.3 

~~~ cpp 
#include<iostream>
int main()
{
	using namespace std;
	int rats = 101;
	int& rodents = rats;
	//输出值
	cout << "rats = " << rats;
	cout << ", rodents = " << rodents << endl;
	//输出地址
	cout << "rats address = " << &rats;
	cout << ", rodents address = " << &rodents << endl;
	//将 rodents 值改变，查看结果
	int bunnies = 50;
	rodents = bunnies;
	cout << "bunnies = " << bunnies;
	cout << ", rats = " << rats;
	cout << ", rodents = " << rodents << endl;
	//输出地址查看结果
	cout << "bunnies address = " << &bunnies;
	cout << ", rodents address = " << &rodents << endl;
	return 0;
}
~~~

## 8.4

~~~ cpp 
#include<iostream>
void swapr(int& a, int& b);
void swapp(int* p, int* q);
void swapv(int a, int b);
int main()
{
	using namespace std;
	int wallet1 = 300;
	int wallet2 = 350;
	cout << "wallet1 = $" << wallet1;
	cout << " wallet2 = $" << wallet2 << endl;

	cout << "Using references to swap comtents:\n";
	swapr(wallet1, wallet2);
	cout << "wallet1 = &" << wallet1;
	cout << " wallet2 = $" << wallet2 << endl;

	cout << "Using pointers to swap contents again:\n";
	swapp(&wallet1, &wallet2);
	cout << "wallet1 = $" << wallet1;
	cout << " wallet2 = $" << wallet2 << endl;

	cout << "Trying to use passing by value:\n";
	swapv(wallet1, wallet2);
	cout << "wallet1 = $" << wallet1;
	cout << " wallet2 = $" << wallet2 << endl;
	return 0;
}
void swapr(int& a, int& b)//引用传递
{
	int temp;

	temp = a;
	a = b;
	b = temp;
}
void swapp(int* p, int* q)//指针方法
{
	int temp;

	temp = *p;
	*p = *q;
	*q = temp;
}
void swapv(int a, int b)//按值传递 
{
	int temp;

	temp = a;
	a = b;
	b = temp;
}
~~~

## 8.5

~~~ cpp
#include<iostream>
double cube(double a);
double refcube(double& ra);
int main()
{
	using namespace std;
	double x = 3.0;

	cout << cube(x);
	cout << " = cube of " << x << endl;
	cout << refcube(x);
	cout << " = cube of " << x << endl;
	return 0;
}
double cube(double a)
{
	a *= a * a;
	return 0;
}
double refcube(double& ra)
{
	ra *= ra * ra;
	return 0;
}
~~~

## 8.6

~~~ cpp
#include<iostream>
#include<string>
struct free_throws
{
	std::string name;
	int made;
	int attempts;
	float percent;
};

void display(const free_throws& ft);
void set_pc(free_throws& ft);
free_throws& accumulate(free_throws& target, const free_throws& source);
int main()
{
	free_throws one = { "Ifelsa Branch",13,14 };//设定的初始值比成员少，余下的成员将被设置为零。
	free_throws two = { "Andor Knott",10,16 };
	free_throws three = { "mINNIE mAX",7,9 };
	free_throws four = { "Whily looper",5,9 };
	free_throws five = { "Long long",6,14 };
	free_throws team = { "Throwgoods",0,0 };

	free_throws dup;

	set_pc(one);
	display(one);
	accumulate(team, one);
	display(team);
	display(accumulate(team, two));
	accumulate(accumulate(team, three), four);
	display(team);
    dup = accumulate(team, two);
	std::cout << "Displaying team:\n";
	display(team);
	std::cout << "Displayint dup after assignment:\n";
	display(dup);
	set_pc(four);
	accumulate(dup, five) = four;//在赋值语句中左边必须是可修改的左值。，也就是说在赋值表达式中，左边的子表达式必须表示一个可修改的内存块。
    /*上述代码与下面的代码等效：
    accumulate(dup,five);
    dup=four;
    其中第二条语句会抵消第一条语句所做的工作，因此在原始赋值语句使用accumulate()的方式并不好*/
	std::cout << "Displaying dup after ill-advised assignment:\n";
	display(dup);
	return 0;
}
void display(const free_throws& ft)//显示结构内容，而不修改它使用引用可节省时间和内存
{
	using std::cout;
	cout << "Name: " << ft.name << '\n';
	cout << " Made: " << ft.made << '\t';
	cout << "Attenmpts: " << ft.attempts << '\t';
	cout << "Percent: " << ft.percent << '\n';
}
void set_pc(free_throws& ft)
{
	if (ft.attempts != 0)
		ft.percent = 100.0f * float(ft.made) / float(ft.attempts);
	else
	{
		ft.percent = 0;
	}
}
free_throws& accumulate(free_throws& target, const free_throws& source)
{
	target.attempts += source.attempts;
	target.made += source.made;
	set_pc(target);
	return target;
}
~~~

如果不希望函数修改传入的结构，可使用` const`：

~~~ cpp
void display(const free_throws& ft)
~~~

**返回引用与传统返回机制的不同之处：**

- 传统返回机制与按值传递函数类似：计算关键字return后面的表达式，并将结果返回给调用函数。从概念上说，这个值被复制到一个临时的位置，而调用程序将使用这个值。
- 返回引用将直接返回变量本身，而不是先将变量复制为一个副本，再将副本复制给左值。

**返回引用时需要注意的问题：**

- 应避免返回函数终止时不再存在的内存单元引用。
  比如返回在声明函数是创建的临时变量的引用。，因为函数完毕后他将不再存在。
- 应避免返回临时变量的指针。

解决方法：

- 返回一个作为参数传递给函数的引用。作为参数的引用将指向调用函数使用的数据  ，因此返回的引用也将指向这些数据。
- 是用new来分配新的储存孔家。，并返回指向该内存空间的指针。

**为何将const用于返回类型**

如省略const，可以编写更简短代码，但含义也更模糊。

使用const可避免在设计中添加模糊的特性（会增加犯错的机会）

## 8.7

~~~ cpp
#include<iostream>
#include<string>
using namespace std;
string version1(const string& s1, const string& s2);
const string& version2(string& s1, const string& s2);
const string& version3(string& s1, const string& s2);
int main()
{
	string input;
	string copy;
	string result;
	cout << "Enter a string: ";
	getline(cin, input);
	copy = input;
	cout << "Your string as entered: " << input << endl;
	result = version1(input, "***");
	cout << "Your string enhanced: " << result << endl;
	cout << "Your original string: " << input << endl;

	result = version2(input, "###");
	cout << "Your string enhanced: " << result << endl;
	cout << "Your original string: " << input << endl;

	cout << "Resetting original string.\n";
	input = copy;
	result = version3(input, "@@@");
	cout << "your string enhanced: " << result << endl;
	cout << "Your original string: " << input << endl;

	return 0;
}
string version1(const string& s1, const string& s2)
{
	string temp;
	temp = s2 + s1 + s2;
	return temp;
}
const string& version2(string& s1, const string& s2)
{
	s1 = s2 + s1 + s2;
	return s1;
}
const string& version3(string& s1, const string& s2)
{
	string temp;
	temp = s2 + s1 + s2;
	return temp;
}
~~~

string类定义了一种char*到string的转换功能，这使得可以使用C-风格字符串来初始化string对象。

假设实参的类型与引用的参数类型不匹配，蛋壳杯转换为引用类型，程序将创建一个正确类型的临时变量，使用转换后的实参值来初始化它，然后传递一个指向该临时变量的引用。

即：如果形参类型为` const string &`，在调用函数时，使用的实参可以使string对象或C-风格字符串，

## 8.8

~~~ cpp
#include<iostream>
#include<fstream>
#include<cstdlib>
using namespace std;

void file_it(ostream& os, double fo, const double fe[], int n);
const int LIMIT = 5;
int main()
{
	ofstream fout;
	const char* fn = "ep-data.txt";
	fout.open(fn);
	if (!fout.is_open())
	{
		cout << "Can't open " << fn<<". Bye\n";
		exit(EXIT_FAILURE);
	}
	double objective;
	cout << "Enter the focla lengths of your "
		"telescope objective in mm: ";
	cin >> objective;
	double eps[LIMIT];
	cout << "Enter the focal lengths, in mm, of " << LIMIT
		<< " eyepieces:\n";
	for (int i = 0; i < LIMIT; i++)
	{
		cout << "Eyepiece #" << i + 1 << ": ";
		cin >> eps[i];
	}
	file_it(fout, objective, eps, LIMIT);
	file_it(cout, objective, eps, LIMIT);
	cout << "Done\n";
	return 0;
}
void file_it(ostream& os, double fo, const double fe[], int n)
{
	ios_base::fmtflags initial;
	initial = os.setf(ios_base::fixed);
	os.precision(0);
	os << "Focal length of objective: " << fo << " mm\n";
	os.setf(ios::showpoint);
	os.precision(1);
	os.width(12);
	os << "f.1. eyepiece";
	os.width(15);
	os << "magnification" << endl;
	for (int i = 0; i < n; i++)
	{
		os.width(12);
		os << fe[i];
		os.width(15);
		os << int(fo / fe[i] + 0.5) << endl;
	}
	os.setf(initial);
}
~~~

方法调用setf(ios_base::fixed)将对象置于使用定点表示法的模式

方法调用setf(ios_base::showpoint)将对象置于显示小数点的模式，即使小数部分为零。

方法precision()指定显示多少位小数（假设对象处于定点模式下）

方法width()设置下一次输出操作使用的字段宽度，这种设置只在下一次有效。默认的字符宽度为零

每个对象都储存了自己的格式化设置。

## 8.9

~~~ cpp
#include<iostream>
const int ArSize = 80;
char* left(const char* str, int n = 1);
int main()
{
	using namespace std;
	char sample[ArSize];
	cout << "Enter a string:\n";
	cin.get(sample, ArSize);
	char* ps = left(sample, 4);
	cout << ps << endl;
	delete[]ps;
	ps = left(sample);
	cout << ps << endl;
	delete[]ps;
	return 0;
}
char* left(const char* str, int n)
{
	if (n < 0)
		n = 0;
	char* p = new char[n + 1];
	int i;
	for (i = 0; i < n && str[i]; i++)
		p[i] = str[i];
	while (i<=n)
	{
		p[i++] = '\0';
	}
	return 0;
}
~~~

## 8.10

~~~ cpp
#include<iostream>
unsigned long left(unsigned long num, unsigned ct);
char* left(const char* str, int n = 1);
int main()
{
	using namespace std;
	char* trip = (char*)"Hawaii!!";
	unsigned long n = 12345678;
	int i;
	char* temp;

	for (int i = 0; i < 10; i++)
	{
		cout << left(n, i) << endl;
		temp = left(trip, i);
		cout << temp << endl;
		delete[]temp;
	}
	return 0;
}
unsigned long left(unsigned long num, unsigned ct)
{
	unsigned digits = 1;
	unsigned long n = num;
	if (ct == 0 || num == 0)
		return 0;
	while (n/=10)
	{
		digits++;
	}
	if (digits>ct)
	{
		ct = digits - ct;
		while (ct--)
		{
			num /= 10;
		}
		return num;
	}
	else
	{
		return 0;
	}
}
char* left(const char* str, int n)
{
	if (n < 0)
		n = 0;
	char* p = new char[n + 1];
	int i;
	for (i = 0; i < n && str[i]; i++)
		p[i] = str[i];
	while (i<=n)
	{
		p[i++] = '\0';
	}
	return p;
}
~~~

函数多态（函数重载）能够使用多个同名的函数。术语“多态”指的是有多种形式，因此函数多态允许函数可以有多种形式。

术语“函数重载”指的是可以有多个同名的函数。两个术语指的是同名的函数。

C++使用上下文来确定要是用的重载函数版本。

函数重载的关键是函数的参数列表——也称函数特征标（function signature）

不同函数的特征表是否相投与变量名是否相同无关。参数的数目和类型相同，同辉参数的排列顺序也相同，则他们的特征标相同。

如果特征标不同，则可以定义相同函数名的函数。

编译器再检查函数特征标时，将把类型引用和；类型本身视为同一个特征标。



## 8.11

~~~ cpp
#include<iostream>
template<typename T>//or class T
void Swap(T& a, T& b);

int main()
{
	using namespace std;
	int i = 10;
	int j = 20;
	cout << "i, j = " << i << ", " << j << ".\n";
	cout << "Using compiler-generated int swapper:\n";
	Swap(i, j);
	cout << "Now i, j = " << i << ", " << j << ".\n";

	double x = 24.5;
	double y = 81.7;
	cout << "x, y = " << x << "," << y << ".\n";
	cout << "Using compiler-generated double swapper:\n";
	Swap(x, y);
	cout << "Now x,y = " << x << ", " << y << ".\n";
	return 0;
}
template <typename T>//or class T
void Swap(T& a, T& b)
{
	T temp;
	temp = a;
	a = b;
	b = temp;
}

~~~

函数模板。

模板并不创建任何函数，而只是告诉编译器如何定义函数

例：

~~~ cpp
template <typename T>//or class T
void Swap(T& a, T& b)
{
	T temp;
	temp = a;
	a = b;
	b = temp;
}
~~~

关键字` template`和` typename` 是必须的 ，除非用class代替template，这两种关键字是等价的。

函数模板不能缩短可执行程序。最终的代码不包含任何模板，而只包含了为程序生成的实际函数。

好处：他使生成多个函数定义更简单、更可靠。

使用场景：常将模板放在头文件中，并在需要试用模板的文件中包含头文件。

## 8.12

~~~ cpp
#include<iostream>
template<typename T>
void Swap(T& a, T& b);

template<typename T>
void Swap(T* a, T* b, int n);
void Show(int a[]);
const int Lim = 8;

int main()
{
	using namespace std;
	int i = 10;
	int j = 20;
	cout << "i, j = " << i << ", " << j << ".\n";
	cout << "Using compiler-generated int swapper:\n";
	Swap(i, j);
	cout << "Now i, j = " << i << ", " << j << ".\n";

	int d1[Lim] = { 0,7,0,4,1,7,7,6 };
	int d2[Lim] = { 0,7,2,0,1,9,6,9 };
	cout << "Orignal arrays:\n";
	Show(d1);
	Show(d2);
	Swap(d1, d2, Lim);
	cout << "Swapped arrays:\n";
	Show(d1);
	Show(d2);
	return 0;
}
template <typename T>
void Swap(T& a, T& b)
{
	T temp;
	temp = a;
	a = b;
	b = temp;
}
template <typename T>
void Swap(T a[], T b[], int n)
{
	T temp;
	for (int i = 0; i < n; i++)
	{
		temp = a[i];
		a[i] = b[i];
		b[i] = temp;
	}
}
void Show(int a[])
{
	using namespace std;
	cout << a[0] << a[1] << "/";
	cout << a[2] << a[3] << "/";
	for (int i = 4; i < Lim; i++)
	{
		cout << a[i];
	}
	cout << endl;
}

~~~

并非所有的模板参数都必须是模板参数类型。

## 8.13

~~~ cpp
#include<iostream>
template<typename T>
void Swap(T& a, T& b);

struct job
{
	char name[40];
	double salary;
	int floor;
};

template<>void Swap <job>(job& j1, job& j2);
void Show(job& j);

int main()
{
	using namespace std;
	int i = 10;
	int j = 20;
	cout << "i, j = " << i << ", " << j << ".\n";
	cout << "Using compiler-generated int swapper:\n";
	Swap(i, j);
	cout << "Now i, j = " << i << ", " << j << ".\n";

	job sue = { "Suan Yaffee",73000.60,7 };
	job sideney = { "Sideney Taffee",78060.72 ,9 };
	cout << "Before job swapping:\n";
	Show(sue);
	Show(sideney);
	Swap(sue, sideney);
	cout << "After job swapping:\n";
	Show(sue);
	Show(sideney);

	return 0;
}
template <typename T>
void Swap(T& a, T& b)
{
	T temp;
	temp = a;
	a = b;
	b = temp;
}
template<>void Swap<job>(job& j1, job& j2)
{
	double t1;
	int t2;
	t1 = j1.salary;
	j1.salary = j2.salary;
	j2.salary = t1;
	t2 = j1.floor;
	j1.floor = j2.floor;
	j2.floor = t2;
}
void Show(job& j)
{
	using namespace std;
	cout << j.name << ": $" << j.salary
		<< " on floor " << j.floor << endl;
}

~~~

显式具体化：为了解决函数模板的局限性。

# 第九章

## 9.1 and 9.2 and 9.3

~~~ cpp
#ifndef COORDIN_H_
#define COORDIN_H_

struct polar
{
	double distance;
	double angle;
};
struct rect
{
	double x;
	double y;
};

polar rect_to_polar(rect xypos);
void show_polar(polar dapos);

#endif // !COORDIN_H_

~~~

~~~ cpp
#include<iostream>
#include"coordin.h"
using namespace std;

int main()
{
	rect rplace;
	polar pplace;

	cout << "Enter the x and y values: ";
	while (cin>>rplace.x>>rplace.y)
	{
		pplace = rect_to_polar(rplace);
		show_polar(pplace);
		cout << "Next two number (q to quit): ";
	}
	cout << "Bye!\n";
	return 0;

}
~~~

~~~ cpp
#include<iostream>
#include<cmath>
#include"coordin.h"

polar rect_to_polar(rect xypos)
{
	using namespace std; 
	polar answer;

	answer.distance =
		sqrt(xypos.x * xypos.x + xypos.y * xypos.y);
	answer.angle = atan2(xypos.y, xypos.x);
	return answer;
}
void show_polar(polar dapos)
{
	using namespace std;
	const double Rad_to_deg = 57.29577951;

	cout << "distance = " << dapos.distance;
	cout << ". angle = " << dapos.angle * Rad_to_deg;
	cout << " degrees\n";
}
~~~

原来的函数（7.12）可以分成三个部分：

- 头文件：包含结构声明和使用这些结构的函数的原型。
- 源代码文件：包含与结构有关的函数的代码。
- 源代码文件：包含调用与结构有关的函数的代码。

一般情况下不要将函数定义或变量声明放到头文件中。

头文件夹一般包含：

- 函数原型
- 使用#define或const定义的符号常量
- 结构声明
- 类声明
- 模板声明
- 内联函数

结构声明不声明变量。

### 头文件管理

在同一个文件中只能将同一个头文件包含一个。

~~~ cpp
#ifndef COORDIN_H
...
#endif
~~~

以上的代码意味着仅当以前没有使用预处理器编译指令#define定义名称COORDIN_H时，才处理#ifndef和#define之间的语句。

通常，使用#define语句来创建符号常量，但只要将#define用于名称，就足以完成该名称的定义。

## 9.4

~~~ cpp
#include<iostream>
void oil(int x);
int main()
{
	using namespace std;
	
	int texas = 31;
	int year = 2011;
	cout << "In main(), texas = " << texas << ", &texas = ";
	cout << &texas << endl;
	cout << "In main(), year = " << year << ", &years = ";
	cout << &year << endl;
	oil(texas);
	cout << "In main(), texas = " << texas << ". &texas = ";
	cout << &texas << endl;
	cout << "In main(),year = " << year << ", year = ";
	cout << &year << endl;
	return 0;
}
void oil(int x)
{
	using namespace std;
	int texas = 5;

	cout << "In oil(), texas = " << texas << ", &texas = ";
	cout << &x << endl;
	{

		int texas = 113;
		cout << "In block, texas = " << texas;
		cout << ", &texas = " << &texas << endl;
		cout << "In block, x = " << x << ", &x = ";
		cout << &x << endl;
	}
	cout << "Post-block texas = " << texas;
	cout << ", &texas = " << &texas << endl;
}
~~~

演示自动存储持续性

默认情况下，在函数中声明的函数参数和变量的存储持续性为自动，作用域为局部，没有链接性

作用域（scope）描述了名称在文件（翻译单元）的多大范围可见

链接性（linkage）描述了名称如何在不同单元间共享。



# 第10章

## 10.1

~~~ cpp
#ifndef STOCK00_H_
#define STOCK00_H_

#include<string>

class Stock
{
public:
	void acquire(const std::string& co, long n, double pr);
	void buy(long num, double price);
	void shell(long num, double price);
	void update(double price);
	void show();

private:
	std::string company;
	long shares;
	double share_val;
	double total_val;
	void set_lot() { total_val = shares * share_val; }
};

#endif
~~~

## 10.2

~~~ cpp
#include <iostream>
#include "stock00.h"

void Stock::acquire(const std::string& co, long n, double pr)
{
	company = co;
	if (n<0)
	{
		std::cout << "Number of shares can't be negative; "
			<< company << " shares set to 0.\n";
		shares = 0;

	}
	else
	{
		shares = n;
	}
	share_val = pr;
	set_lot();
}
void Stock::buy(long num, double price)
{
	if (num<0)
	{
		std::cout << "Number of shares purchased can't be negative. "
			<< "Transaction is aborted.\n";
	}
	else
	{
		shares += num;
		share_val = price;
		set_lot();
	}
	
}
void Stock::shell(long num, double price)
{
	using std::cout;
	if (num<0)
	{
		cout << "Number of shares sold can't be negative. "
			<< "Transcation is aborted.\n";
	}
	else if (num >shares)
	{
		cout << "You can't sell more than you have! "
		<< "Transaction is aborted.\n";
	}
	else
	{
		shares -= num;
		share_val = price;
		set_lot();

	}
}
void Stock::update(double price)
{
	share_val = price;
	set_lot();
}
void Stock::show()
{
	std::cout << "Company: " << company
		<< " shares: " << shares << '\n'
		<< " share Price: $" << share_val
		<< " Total Worth: $" << total_val << '\n';
}
~~~

## 10.3

~~~ cpp
#include<iostream>
#include"stock00.h"

int main()
{
	Stock fluffy_the_cat;
	fluffy_the_cat.acquire("NanoSmart", 20, 12.50);
	fluffy_the_cat.show();
	fluffy_the_cat.buy(15, 18.125);
	fluffy_the_cat.show();
	fluffy_the_cat.shell(400, 20.00);
	fluffy_the_cat.show();
	fluffy_the_cat.buy(300000, 40.125);
	fluffy_the_cat.show();
	fluffy_the_cat.shell(300000, 0.125);
	fluffy_the_cat.show();
	return 0;
}

~~~

## 10.4

~~~ cpp
#ifndef STOCK00_H_
#define STOCK00_H_

#include<string>

class Stock
{
public:

	Stock();
	Stock(const std::string& co, long n = 0, double pr = 0.0);
	~Stock();
	void buy(long num, double price);
	void shell(long num, double price);
	void update(double price);
	void show();

private:
	std::string company;
	long shares;
	double share_val;
	double total_val;
	void set_lot() { total_val = shares * share_val; }
};

#endif
~~~

## 10.5

~~~ cpp
#include <iostream>
#include "stock00.h"
Stock::Stock()
{
	std::cout << "Default constructo called\n";
	company = "mo name";
	shares = 0;
	share_val = 0.0;
	total_val = 0.0;
}

Stock::Stock(const std::string& co, long n, double pr)
{
	std::cout << "Number of shares can't be negative;\n";
	company = co;

	if (n<0)
	{
		std::cout << "Number of shares can't be negative; "
			<< company << " shares set to 0.\n";
		shares = 0;

	}
	else
	{
		shares = n;
	}
	share_val = pr;
	set_lot();
}
Stock::~Stock()
{
	std::cout << "Bye, " << company << "!\n";
}


void Stock::buy(long num, double price)
{
	if (num<0)
	{
		std::cout << "Number of shares purchased can't be negative. "
			<< "Transaction is aborted.\n";
	}
	else
	{
		shares += num;
		share_val = price;
		set_lot();
	}
	
}
void Stock::shell(long num, double price)
{
	using std::cout;
	if (num<0)
	{
		cout << "Number of shares sold can't be negative. "
			<< "Transcation is aborted.\n";
	}
	else if (num >shares)
	{
		cout << "You can't sell more than you have! "
		<< "Transaction is aborted.\n";
	}
	else
	{
		shares -= num;
		share_val = price;
		set_lot();

	}
}
void Stock::update(double price)
{
	share_val = price;
	set_lot();
}
void Stock::show()
{
	using std::cout;
	using std::ios_base;
	//set format to #.##
	ios_base::fmtflags orig =
		cout.setf(ios_base::fixed, ios_base::floatfield);
	//方法set(ios_base::fixed)将对象置于使用定点表示法的模式
	//方法set(ios_base::floatfield)，floatfield中包含定点表示法标记和科学表示法标记

	std::streamsize prec = cout.precision(3);
	
	cout << "Company: " << company
		<< " shares: " << shares << '\n';
	cout << " shares Price: $" << share_val;
	//set format to #.##
	cout.precision(2);
	cout << " Total Worth: $" << total_val << '\n';
	//restore original format
	cout.setf(orig, ios_base::floatfield);
	cout.precision(prec);
}
~~~

## 10.6

~~~ cpp
#include<iostream>
#include"stock00.h"

int main()
{
	{
		using std::cout;
		cout << "Using constructors to create new object\n";
		Stock stock1("NanoSmart", 12, 20.0);
		stock1.show();
		Stock stock2 = Stock("Boffo Object", 2, 2.0);
		stock2.show();

		cout << "Assigning stock1 to stock2:\n";
		stock2 = stock1;//可以将一个对象赋给同类型的另一个对象、
		cout << "Listing stock1 to stock2:\n";
		stock1.show();
		stock2.show();

		cout << "Using a constructor to reset an object\n";
		stock1 = Stock("Nifty Foods", 10, 50.0);
		cout << "Revised stock1:\n";
		stock1.show();
		cout << "Done\n";
	}
    /*添加这一对大括号后，最后两个析构函数调用将在到达返回语句前执行，从而现实相应的消息。*/
    
    
	return 0;
}

~~~









## 暂空

## 10.10 and 10.11 and 10.12

~~~ cpp
// 10.10
#ifndef STACK_H_
#define STACK_H_

typedef unsigned long Item;

class Stack
{
private:
	enum { MAX = 10 };
	Item items[MAX];
	int top;   //栈当前可使用的最大容量
public:
	Stack();
	bool isempty() const;
	bool isfull() const;
	bool push(const Item& item);
	bool pop(Item& item);
};

#endif
~~~

~~~ cpp 
//10.11
#include "stack.h"

/*
	 栈的初始化
	 以 top = 0 表示空栈
*/
Stack::Stack()
{
	top = 0;
}
/*
* 若栈为空栈，则返回 
*/
bool Stack::isempty() const
{
	return top == 0;
}
/**/
bool Stack::isfull() const
{
	return top == MAX;
}
bool Stack::push(const Item& item)
{
	if (top<MAX)
	{
		items[top++] = item;
		return true;
	}
	else
	{
		return false;
	}
}
bool Stack::pop(Item& item)
{
	if (top>0)
	{
		item = items[--top];
	}
	else
	{
		return false;
	}
}
~~~



~~~ cpp
//10.12
#include<iostream>
#include<cctype>
#include"stack.h"

int main()
{
	using namespace std;
	Stack st;
	char ch;
	unsigned long po;
	cout << "Please enter A to add a purchase order,\n"
		<< "P to process a PO, or to quit.\n";
	while (cin >> ch && toupper(ch) !='Q')
	{
		while (cin.get()!= '\n')
		{
			continue;
		}
		if (!isalpha(ch))
		{
			cout << '\a';
			continue;
		}
		switch (ch)
		{
		case 'A':
		case 'a':cout << "Enter a PO number to add: ";
			cin >> po;
			if (st.isfull())
				cout << "stack already full\n";
			else
			{
				st.push(po);
			}
			break;
		case 'P':
		case 'p':if (st.isempty())
		{
			cout << "stack already empty\n";
		}
		else
		{
			st.pop(po);
			cout << "PO #" << po << " popped\n";
		}
		break;
		}
		cout << "Please enter A to add a purchase order,\n"
			<< "P to process a PO, or Q to quit.\n";

	}
	cout << "Bye\n";
	return 0;
}
~~~

# 第三章

## 11.1 and 11.2 and 11.3

~~~ cpp
#ifndef MYTIME0_H_
#define MYTIME0_H_

class Time
{
public:
	Time();
	Time(int h,int m = 0);

	void AddMin(int m);
	void AddHr(int h);
	void Reset(int h = 0, int m = 0);
	Time Sum(const Time& t) const;
	void Show() const;
	~Time();

private:
	int hours;
	int minutes;
};


#endif // !MYTIME0_H_

~~~

~~~ cpp
#include "stack.h"
#include<iostream>
Time::Time()
{
	hours = minutes = 0;
}
Time::Time(int h, int m)
{
	hours = h;
	minutes = m;
}

void Time::AddMin(int m)
{
	minutes += m;
	hours += minutes / 60;
	minutes %= 60;
}

void Time::AddHr(int h)
{
	hours = h;
}

void Time::Reset(int h, int m)
{
	hours = h;
	minutes = m;
}
Time Time::Sum(const Time& t) const
{
	Time sum;
	sum.minutes = minutes + t.minutes;
	sum.hours = hours + t.hours + sum.minutes / 60;
	sum.minutes %= 60;
	return sum;
}
void Time::Show() const
{
	std::cout << hours << " hours, " << minutes << " minutes";
}
Time::~Time()
{
}
~~~

~~~ cpp
#include<iostream>
#include<cctype>
#include"stack.h"

int main()
{
	using namespace std;
	Time planning;
	Time coding(2, 40);
	Time fixing(5, 55);
	Time total;

	cout << "planning time = ";
	planning.Show();
	cout << endl;

	cout << "coding time = ";
	coding.Show();
	cout << endl;

	total = coding.Sum(fixing);
	cout << "coding.Sum(fixing) = ";
	total.Show();
	cout << endl;

	return 0;
}
~~~

## 11.4 and 11.5 and 11.6

~~~ cpp
#ifndef MYTIME0_H_
#define MYTIME0_H_

class Time
{
public:
	Time();
	Time(int h,int m = 0);

	void AddMin(int m);
	void AddHr(int h);
	void Reset(int h = 0, int m = 0);
	//Time Sum(const Time& t) const;
	Time operator+(const Time& t) const;
	void Show() const;
	~Time();

private:
	int hours;
	int minutes;
};


#endif // !MYTIME0_H_

~~~

~~~ cpp
#include "stack.h"
#include<iostream>
Time::Time()
{
	hours = minutes = 0;
}
Time::Time(int h, int m)
{
	hours = h;
	minutes = m;
}

void Time::AddMin(int m)
{
	minutes += m;
	hours += minutes / 60;
	minutes %= 60;
}

void Time::AddHr(int h)
{
	hours = h;
}

void Time::Reset(int h, int m)
{
	hours = h;
	minutes = m;
}
Time Time::operator+(const Time& t) const
{
	Time sum;
	sum.minutes = minutes + t.minutes;
	sum.hours = hours + t.hours + sum.minutes / 60;
	sum.minutes %= 60;
	return sum;
}
void Time::Show() const
{
	std::cout << hours << " hours, " << minutes << " minutes";
}
Time::~Time()
{
}
~~~

~~~ cpp
#include<iostream>
#include<cctype>
#include"stack.h"

int main()
{
	using namespace std;
	Time planning;
	Time coding(2, 40);
	Time fixing(5, 55);
	Time total;

	cout << "planning time = ";
	planning.Show();
	cout << endl;

	cout << "coding time = ";
	coding.Show();
	cout << endl;

	cout << "fixing time = ";
	fixing.Show();
	cout << endl;

	total = coding + fixing;
	cout << "total = coding + fixing";
	//cout << "coding.Sum(fixing) = ";
	total.Show();
	cout << endl;

	Time morefixing(3, 28);
	cout << ",ore fixing time = ";
	morefixing.Show();
	total = morefixing.operator+(total);
	cout << "total = morefixing.operator+(total) = ";
	total.Show();
	cout << endl;


	return 0;
}
~~~

## 11.7 and 11.8 and 11.9

~~~ cpp
#ifndef MYTIME0_H_
#define MYTIME0_H_

class Time
{
public:
	Time();
	Time(int h,int m = 0);

	void AddMin(int m);
	void AddHr(int h);
	void Reset(int h = 0, int m = 0);
	//Time Sum(const Time& t) const;
	Time operator+(const Time& t) const;
	Time operator-(const Time& t) const;
	Time operator*(double mult) const;
	void Show() const;
	~Time();

private:
	int hours;
	int minutes;
};


#endif // !MYTIME0_H_

~~~

~~~ cpp
#include "stack.h"
#include<iostream>
Time::Time()
{
	hours = minutes = 0;
}
Time::Time(int h, int m)
{
	hours = h;
	minutes = m;
}

void Time::AddMin(int m)
{
	minutes += m;
	hours += minutes / 60;
	minutes %= 60;
}

void Time::AddHr(int h)
{
	hours = h;
}

void Time::Reset(int h, int m)
{
	hours = h;
	minutes = m;
}
Time Time::operator+(const Time& t) const
{
	Time sum;
	sum.minutes = minutes + t.minutes;
	sum.hours = hours + t.hours + sum.minutes / 60;
	sum.minutes %= 60;
	return sum;
}
Time Time::operator-(const Time& t) const
{
	Time diff;
	int tot1, tot2;
	tot1 = t.minutes + 60 * t.hours;
	tot2 = minutes + 60 * hours;
	diff.minutes = (tot2 - tot1) % 60;
	diff.hours = (tot2 - tot1) / 60;
	return diff;
}
Time Time::operator*(double mult) const
{
	Time result;
	long totalminutes = hours * mult * 60 + minutes * mult;
	result.hours = totalminutes / 60;
	result.minutes = totalminutes % 60;
	return result;
}
void Time::Show() const
{
	std::cout << hours << " hours, " << minutes << " minutes";
}
Time::~Time()
{
}
~~~

~~~ cpp
#include<iostream>
#include<cctype>
#include"stack.h"

int main()
{
	using namespace std;
	Time weeding(4, 35);
	Time waxing(2, 47);
	Time total;
	Time diff;
	Time adjusted;

	cout << "weeding time = ";
	weeding.Show();
	cout << endl;

	cout << "waxing time =";
	waxing.Show();
	cout << endl;

	cout << "total work time = ";
	total = weeding + waxing;
	total.Show();
	cout << endl;

	diff = weeding - waxing;
	cout << "weeding time - waxing time = ";
	diff.Show();
	cout << endl;

	adjusted = total * 1.5;
	cout << "adjusted work time = ";
	adjusted.Show();
	cout << endl;


	return 0;
}
~~~

## 11.10 and 11.11 and 11.12

~~~ cpp
#ifndef MYTIME0_H_
#define MYTIME0_H_
#include<iostream>
class Time
{
public:
	Time();
	Time(int h,int m = 0);

	void AddMin(int m);
	void AddHr(int h);
	void Reset(int h = 0, int m = 0);
	//Time Sum(const Time& t) const;
	Time operator+(const Time& t) const;
	Time operator-(const Time& t) const;
	Time operator*(double mult) const;
	friend Time operator* (double m, const Time& t)
	{
		return t * m;
	}
	friend std::ostream& operator<<(std::ostream& os, const Time& t);
	void Show() const;
	~Time();

private:
	int hours;
	int minutes;
};


#endif // !MYTIME0_H_

~~~

~~~ cpp
#include "stack.h"
#include<iostream>
Time::Time()
{
	hours = minutes = 0;
}
Time::Time(int h, int m)
{
	hours = h;
	minutes = m;
}

void Time::AddMin(int m)
{
	minutes += m;
	hours += minutes / 60;
	minutes %= 60;
}

void Time::AddHr(int h)
{
	hours = h;
}

void Time::Reset(int h, int m)
{
	hours = h;
	minutes = m;
}
Time Time::operator+(const Time& t) const
{
	Time sum;
	sum.minutes = minutes + t.minutes;
	sum.hours = hours + t.hours + sum.minutes / 60;
	sum.minutes %= 60;
	return sum;
}
Time Time::operator-(const Time& t) const
{
	Time diff;
	int tot1, tot2;
	tot1 = t.minutes + 60 * t.hours;
	tot2 = minutes + 60 * hours;
	diff.minutes = (tot2 - tot1) % 60;
	diff.hours = (tot2 - tot1) / 60;
	return diff;
}
Time Time::operator*(double mult) const
{
	Time result;
	long totalminutes = hours * mult * 60 + minutes * mult;
	result.hours = totalminutes / 60;
	result.minutes = totalminutes % 60;
	return result;
}
std::ostream& operator<<(std::ostream& os, const Time& t)
{
	os << t.hours << " hours, " << t.minutes << "minutes";
	return os;//返回类型是ostream& 这意味着该函数返回ostream对象的引用

}
void Time::Show() const
{
	std::cout << hours << " hours, " << minutes << " minutes";
}
Time::~Time()
{
}
~~~

~~~ cpp
#include<iostream>
#include<cctype>
#include"stack.h"

int main()
{
	using std::cout;
	using std::endl;
	Time aida(3, 35);
	Time tosca(2, 48);
	Time temp;

	cout << "Aida and Tosca:\n";
	cout << aida << "; " << tosca << endl;
	temp = aida + tosca;
	cout << "Aida + Tosca: " << temp << endl;
	temp = aida * 1.17;
	cout << "Aida*1.17: " << temp << endl;
	cout << "10.0 * Tosca: " << 10.0 * tosca << endl;

	return 0;
}
~~~

在为类重载二元运算符时常常需要友元，

友元函数可以访问类的私有成员。

使得非成员函数可以按所需的顺序获得操作数。

传统的二元运算符重载往往会默认规定使用操作数的顺序。友元可以突破这个限制，使得操作突破顺序的限制，在操作数不影响结果的重载中，使用友元函数可以

获得概念层面的实现。



## 11.13

~~~ cpp
#ifndef MYTIME0_H_
#define MYTIME0_H_
#include<iostream>
namespace VECTOR
{
	class Vector
	{
	public:
		enum Mode
		{
			RECT,
			POL
		};
		Vector();
		~Vector();
		Vector(double n1, double n2, Mode form = RECT);
		void reset(double n1, double n2, Mode form = RECT);
		double xval();
		double yval();
		double magval();
		double angval();
		void polar_mode();
		void rect_mode();

		//运算符重载 
		Vector operator+(const Vector& b) const;
		Vector operator-(const Vector& b) const;
		Vector operator-() const;
		Vector operator*(double n) const;

		//友元函数
		friend Vector operator*(double n, const Vector& a);
		friend std::ostream&
			operator<<(std::ostream& os, const Vector& v);
	private:
		double x;
		double y;
		double mag;
		double ang;
		Mode mode;
		void set_mag();
		void set_ang();
		void set_x();
		void set_y();
	};

	Vector::Vector()
	{
	}

	Vector::~Vector()
	{
	}
}//名称空间VECTOR 结束

#endif // !MYTIME0_H_

~~~

## 11.14

~~~ cpp
#include<cmath>
#include"vector.h"
using std::sqrt;
using std::sin;
using std::cos;
using std::atan;
using std::atan2;
using std::cout;

namespace VECTOR
{
	const double Rad_to_deg = 45.0 / atan(1.0);
	//大约57.2957795130823


	void Vector::set_mag()
	{
		mag = sqrt(x * x + y * y);
	}

	void Vector::set_ang()
	{
		if (x == 0.0 && y == 0.0)
			ang = 0.0;
		else
		{
			ang = atan2(y, x);
		}
	}

	void Vector::set_x()
	{
		x = mag * cos(ang);
	}
	void Vector::set_y()
	{
		y = mag * sin(ang);
	}
	Vector::Vector()
	{
		x = y = mag = ang = 0.0;
		mode = RECT;
	}
	Vector::Vector(double n1, double n2, Mode form)
	{
		mode = form;
		if (form == RECT)
		{
			x = n1;
			y = n2;
			set_x();
			set_y();

		}
		else if(form==POL)
		{
			mag = n1;
			ang = n2;
			set_x();
			set_y();

		}
		else
		{
			cout << "Incorrect 3rd argument to Vector() -- ";
			cout << "vector set to 0.0\n";
			x = y = mag = ang = 0.0;
			mode = RECT;

		}
	}

	void Vector::reset(double n1, double n2, Mode form)
	{
		mode = form;
		if (form == RECT)
		{
			x = n1;
			y = n2;
			set_mag();
			set_ang();

		}
		else if (form == POL)
		{
			mag = n1;
			ang = n2 / Rad_to_deg;
			set_x();
			set_y();
		}
		else
		{
			cout << "Incorrect 3rd argument to Vector() -- ";
			cout << "vector set to 0.0\n";
			x = y = mag = ang = 0.0;
			mode = RECT;
		}
	}

	Vector::~Vector()
	{

	}
	void Vector::polar_mode()
	{
		mode = POL;
	}
	void Vector::rect_mode()
	{
		mode = RECT;
	}
	Vector Vector::operator+(const Vector& b) const
	{
		return Vector(x + b.x, y + b.y);
	}
	Vector Vector::operator-(const Vector& b) const
	{
		return Vector(x - b.x, y - b.y);
	}
	Vector Vector::operator-() const
	{
		return Vector(-x, -y);
	}
	Vector Vector::operator*(double n) const
	{
		return  Vector(n * x, n * y);
	}
	Vector operator*(double n,const Vector& a)
	{
		return a * n;
	}
	std::ostream& operator<<(std::ostream & os, const Vector & v)
	{
		if (v.mode==Vector::RECT)
		{
			os << "(x,y) = (" << v.x << ", " << v.y << ")";
		}
		else
		{
			os << "Vector object mode is invalid";
		}
		return os;
	}
}


~~~



## 11.15

~~~ cpp
#include<iostream>
#include<cstdlib>
#include<ctime>
#include"vector.h"
int main()
{
	using namespace std;
	using VECTOR::Vector;
	srand(time(0));
	double direction;
	Vector step;
	Vector result(0.0, 0.0);
	unsigned long steps = 0;
	double target;
	double dstep;
	cout << "Enter target distance (q to quit): ";
	while (cin>>dstep)
	{
		cout << "Enter step length: ";
		if (!(cin>>dstep))
		{
			break;
		}
		while (result.magval()<target)
		{
			direction = rand() % 360;
			step.reset(dstep, direction, Vector::POL);
			result = result + step;
			steps++;
		}
		cout << "After " << steps << " steps, the subject "
			"has the following location:\n";
		cout << result << endl;
		result.polar_mode();
		cout << "Average outward distance per step = "
			<< result.magval() / steps << endl;
		steps = 0;
		result.reset(0.0, 0.0);
		cout << "Enter target distance (q to quit): ";
		cout << "Bye!\n";
		cin.clear();
		while (cin.get() != '\n')
			continue;
		return 0;
	}
}

~~~


# 13

## 13.1 tabtenn0.h
```cpp
#pragma once
#ifndef TABTENN0_H_
#define TABTENN0_H_
#include <string>

using std::string;

class TableTennisPlayer
{
private:
	string firstname;
	string lastname;
	bool hasTable;
public:
	TableTennisPlayer(const string& fn = "one",
		const string& ln = "none", bool ht = false);
	void Name() const;
	bool HasTable() const { return hasTable; };
	void ResetTable(bool v) { hasTable = v; };
};
#endif // !TABTENN0_H_

```

## 13.2tabtenn0. cpp
```cpp
#include"tabtenn0.h"
#include<iostream>

TableTennisPlayer::TableTennisPlayer(const string& fn,
	const string& ln, bool ht):firstname(fn),
		lastname(ln), hasTable(ht) {}

void TableTennisPlayer::Name() const
{
	std::cout << lastname << ", " << firstname;
}
```

# 14
## 14.20tempmemb.cpp
```cpp
#include<iostream>
using std::cout;
using std::endl;
template <typename T>
class beta
{
private:
	template <typename V>
	class hold
	{
	public:
		hold(V v = 0) :val(v) {}
		void show() const { cout << val << endl; }
		V Value() const { return val; }
	private:
		V val;
	};
	hold<T> q;
	hold<int> n;
public:
	beta(T t, int i) :q(t), n(i){}
	template<typename U>
	U blab(U u, T t) { return (n.Value() + q.Value()) * u / t; }
	void Show() const { q.show(); n.show(); }
};

int main() {
	beta<double> guy(3.5, 3);
	cout << "T was set to double\n";
	guy.Show();
	cout << "V was set to T, which is double,then V was set to int\n";
	cout << guy.blab(10, 2.3) << endl;
	cout << "U was ser to int\n";
	cout << guy.blab(10.0, 2.3) << endl;
	cout << "U was set to double\n";
	cout << "Done\n";
	return 0;

}
```