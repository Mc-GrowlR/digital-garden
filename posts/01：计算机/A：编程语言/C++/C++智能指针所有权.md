# 先导概念

**所有权**：对于特定的对象只能有一个智能指针可拥有它，这样只有拥有对象的智能指针的构造函数会删除该对象。应用于`unique_ptr`智能指针。

**转移所有权**：赋值操作会转移所有权。赋值语句同时也意味着所有权转移的过程。赋值是从右往左，所有权转移也是从右往左。左边的接管其指向的特定对象的所有权，而右边的所有权将被剥夺，同时其指针不再指向有效数据。

** `unique_ptr` 智能指针的所有权转移策略**：（赋值语句的语法）
- `unique_ptr` 智能指针是否被编译器允许赋值取决于源`unique_ptr` 的类型。
- 两个 `unique_ptr` 智能指针赋值会引发错误。（**源`unique_ptr` 将存在一段时间**）
	- VS2022 错误：C2280，尝试引用已删除函数
	- ![](https://growlr-center-blog-image.oss-cn-beijing.aliyuncs.com/image/20220721214901.png)
	- 代码
		```cpp
		unique_ptr<string> p3(new string("auto"));
		unique_ptr<string> p4;
		p4 = p3;
		```
- 但是将一个临时 `unique_ptr` 智能指针赋给另一个 `unique_ptr` 智能指针并不会留下危险的悬挂指针。（**源`unique_ptr` 是临时右值**）
	- 例：将函数返回的临时 `unique_ptr` 智能指针赋给用来接收的 `unique_ptr` 智能指针时,编译器不会报告错误。
	- 代码：
		```cpp
		//定义函数：
		unique_ptr<string> ptr_demo(const char* s)
		{
			unique_ptr<string>temp_ptr(new string(s));
			return temp_ptr;
		}  
		//...
		int main()
		{
			unique_ptr<string> pp;
			pp = ptr_demo("ceshi");
		}
		```
	- 解释：此时的pp接管了归ptr_demo函数传来的临时`unique_ptr` 所有的对象，同时，函数返回的临时`unique_ptr` 被销毁。这时，因为临时`unique_ptr` 被销毁，所以也就不会被人通过它来访问无效的数据，因此是安全的。



# 智能指针语法

## 