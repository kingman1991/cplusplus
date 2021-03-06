##C++ 中的注释##

程序注释是说明性语句，您可以在你编写的 C++ 代码中添加注释，从而帮助任何人阅读源代码。所有编程语言支持某种形式的注释。

C++ 支持单行和多行注释。在注释中可以使用所有的字符，并且它们都将会被 C++ 编译器忽略。

C++ 注释以 /* 开始和以 */结束。例如:

	/* This is a comment */
	
	/* C++ comments can  also
	* span multiple lines
 	*/

注释还可以以 // 开始，一直到行的结束位置。例如:

	#include <iostream>
	using namespace std;

	main()
	{
		cout << "Hello World"; // prints Hello World

		return 0;
	}

上面的代码编译时,将忽略 **//prints Hello World**，最终可执行程序将产生以下结果:

	Hello World

`/*` 和 `*/` 注释，`//` 字符没有特殊的意义。在 `//` 注释的内部，`/*` 和 `*/` 没有特殊的意义。因此，您可以在在一种注释中嵌套另外一种注释。例如:

	/* Comment out printing of Hello World:

	cout << "Hello World"; // prints Hello World

	*/


