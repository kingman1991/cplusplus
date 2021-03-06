## C++ 变量类型##

变量名给我们提供了在程序中我们可以使用的空间信息。每个变量在 C++ 中都有一个特定的类型，它决定变量在内存中的大小和布局；在该内存空间可以存放值的范围；和一组可以应用于该变量的操作。


一个变量的名称可以由字母、数字和下划线字符组成。它必须以字母或下划线开始。大写和小写的字母是不同,因为c++是区分大小写的:

C++ 中有以下基本变量类型，我们在上一节已经介绍过:

<table class="table table-bordered">
<tr>
<th width="30%">Type</th>
<th>Description</th>
</tr>
<tr>
<td>bool</td>
<td>存储的值为 true 或者 false</td>
</tr>
<tr>
<td>char</td>
<td>通常是8位(一位字节)。它是个整数类型。</td>
</tr>
<tr>
<td>int</td>
<td>机器中最常用的整数类型。</td>
</tr>
<tr>
<td>float</td>
<td>单精度浮点类型的值。</td>
</tr>
<tr>
<td>double</td>
<td>双精度浮点类型的值。/td>
</tr>
<tr>
<td>void</td>
<td>代表着缺失类型。</td>
</tr>
<tr>
<td>wchar_t</td>
<td>一个宽字符类型。</td>
</tr>
</table>

C++ 还允许定义各种其他类型的变量，我们将在后续章节将会介绍的，比如 **Enumeration**，指针，数组，引用，数据结构和类。


下一节将介绍如何定义，声明和使用各种类型的变量。

###C++ 中变量的定义###

一个变量定义意味着告诉编译器，存储在哪里以及需要多少的存储空间。变量定义要指定数据类型，同时包含该类型的一个或多个变量的列表：

	type variable_list;

在这里，**type** 必须是一个有效的c++数据类型，包括char，w_char，int，float，double，bool 或者任何用户自定义的对象等。**variable_list** 要包含一个或多个由逗号分隔的标识符。如下是一些有效的声明示例：

	int i, j, k;
	char c, ch;
	float f, salary;
	double d;

**int i,j,k;** 这一行同时声明和定义了变量 i，j 和 k，这条语句指示编译器创建类型为 int，名称为 i，j 和 k 的变量。

变量在声明的同时可以进行初始化(分配一个初始值)。初始化由一个等号后面跟着一个常数表达式如下:

	type variable_name = value;

如下是一些示例：

	extern int d = 3, f = 5;    // declaration of d and f. 
	int d = 3, f = 5;           // definition and initializing d and f. 
	byte z = 22;                // definition and initializes z. 
	char x = 'x';               // the variable x has the value 'x'.

没有初始化的定义：静态类型的变量会隐式地被初始化为 NULL(所有位值为0)，而其他的所有变量的初始值是未知的。

### C++ 中变量声明 ####

变量声明为编译器提供保证，对于给定的类型和名称的变量是唯一的，从而编译器在进一步进行编译变量时不需要变量的完整细节。变量声明只是在编译时有意义的，因为编译器在进行程序的链接时需要变量声明的信息。

当你使用多个文件，并且你自己定义的变量放在其中一个文件里，变量的声明将对程序的链接很有用。您可以使用 **extern** 关键字来声明一个放在任何位置的变量。虽然你在你的c++程序中你可以声明一个变量多次，但它在一个文件中,一个函数或一块代码中只能定义一次。

###示例###

试试下面的例子,一个变量已经在顶部进行了声明,但同时它也在 main 函数中被定义了:

	#include <iostream>
	using namespace std;

	// Variable declaration:
	extern int a, b;
	extern int c;
	extern float f;
  
	int main ()
	{
		// Variable definition:
		int a, b;
		int c;
		float f;
 
		// actual initialization
		a = 10;
		b = 20;
		c = a + b;
 
		cout << c << endl ;

		f = 70.0/3.0;
		cout << f << endl ;
 
		return 0;
	}

上面的代码编译和执行后，它产生以下结果:

	30
	23.3333

相同的概念也可以应用于函数声明，当你对一个函数进行声明时，它的定义可以在其他任何地方。例如:

	// function declaration
	int func();

	int main()
	{
    	// function call
    	int i = func();
	}
	
	// function definition
	int func()
	{
    	return 0;
	}

###左值和右值###

C++ 中有两种表达式：

- 左值：指向内存位置的表达式称为“左值表达式。一个左值可能出现赋值语句的左边或右边。
- 右值：右值是指一个数据值存储在某个内存地址中。一个右值是一个表达式，它不能被赋值，这意味着一个右值可能出现在赋值语句的右边，而不是左边。

变量是左值,因此可能会出现在赋值语句的左边。数字字面值是右值，因此不能被赋值，不能出现赋值语句的在左边。下面是一个有效的语句:

	int g = 20;

但如下却不是一个有效的赋值语句,会产生编译期错误:

 	10 = 20；


