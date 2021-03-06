# C++ 模板 #

模板是泛型编程的基础。泛型编程就是以独立于任何特定类型的方式编写代码。

模板是创建泛型类或函数的蓝图或公式。
使用模板的概念开发的库容器，像迭代器和算法都是泛型编程的例子。

每个容器都有一个单一定义，例如 **vector**，但我们也可以定义许多不同类型的 vector，如 **vector****<int****>** 或 **vector<string>****<string****>** 。 

你也可以使用模板定义函数和类，让我们看看是怎么做的：

## 函数模板： ##

模板函数定义的一般形式如下所示：

    template <class type> ret-type func-name(parameter list)
    {
       // body of function
    }

这里的 **type** 是函数使用的数据类型的占位符名称。 这个名称可以在函数定义内使用。

下面是一个返回两个值中的最大值的函数模板例子：

    #include <iostream>
    #include <string>
    
    using namespace std;
    
    template <typename T>
    inline T const& Max (T const& a, T const& b) 
    { 
    return a < b ? b:a; 
    } 
    int main ()
    {
     
    int i = 39;
    int j = 20;
    cout << "Max(i, j): " << Max(i, j) << endl; 
    
    double f1 = 13.5; 
    double f2 = 20.7; 
    cout << "Max(f1, f2): " << Max(f1, f2) << endl; 
    
    string s1 = "Hello"; 
    string s2 = "World"; 
    cout << "Max(s1, s2): " << Max(s1, s2) << endl; 
    
       return 0;
    }


如果我们编译并运行上述代码，将会产生以下结果：
    
    Max(i, j): 39
    Max(f1, f2): 20.7
    Max(s1, s2): World

## 类模板： ##

就像我们可以定义函数模板一样，我们也可以定义类模板。

模板类定义的一般形式如下所示：
    
    template <class type> class class-name {
    .
    .
    .
    }


这里的 **type** 是一个类型的占位符名称，当类实例化的时候，此类型会被指定。
你可以用一个逗号隔开的列表定义多个泛型数据类型。

以下是一个定义 Stack<> 类并实现泛型方法来压入和弹出堆栈元素的例子：

    #include <iostream>
    #include <vector>
    #include <cstdlib>
    #include <string>
    #include <stdexcept>
    
    using namespace std;
    
    template <class T>
    class Stack { 
      private: 
    vector<T> elems; // elements 
    
      public: 
    void push(T const&);  // push element 
    void pop();   // pop element 
    T top() const;// return top element 
    bool empty() const{   // return true if empty.
    return elems.empty(); 
    } 
    }; 
    
    template <class T>
    void Stack<T>::push (T const& elem) 
    { 
    // append copy of passed element 
    elems.push_back(elem);
    } 
    
    template <class T>
    void Stack<T>::pop () 
    { 
    if (elems.empty()) { 
    throw out_of_range("Stack<>::pop(): empty stack"); 
    }
    	// remove last element 
    elems.pop_back(); 
    } 
    
    template <class T>
    T Stack<T>::top () const 
    { 
    if (elems.empty()) { 
    throw out_of_range("Stack<>::top(): empty stack"); 
    }
    	// return copy of last element 
    return elems.back();  
    } 
    
    int main() 
    { 
    try { 
    Stack<int> intStack;  // stack of ints 
    Stack<string> stringStack;// stack of strings 
    
    // manipulate int stack 
    intStack.push(7); 
    cout << intStack.top() <<endl; 
    
    // manipulate string stack 
    stringStack.push("hello"); 
    cout << stringStack.top() << std::endl; 
    stringStack.pop(); 
    stringStack.pop(); 
    } 
    catch (exception const& ex) { 
    cerr << "Exception: " << ex.what() <<endl; 
    return -1;
    } 
    }

如果我们编译并运行上述代码，将会产生以下结果：

    7
    hello
    Exception: Stack<>::pop(): empty stack