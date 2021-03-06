# C++ 决策语句
决策结构需要程序员指定一个或多个可以被程序评估或测试的条件，以及一个语句或者是当条件被确定为真时可以用来执行的语句，和当条件被确定为假时，可以选择用来执行的其他语句。  

以下是在大多数编程语言中找到的一个典型的决策结构的通用格式。
  
![](http://www.tutorialspoint.com/cplusplus/images/cpp_decision_making.jpg)
 
C++ 编程语言提供以下类型的决策语句。单击以下链接来查看它们的细节。  

<table border="1">
<tr>
<th>语句</th>
<th>描述</th>
</tr>
<tr>
<td><a href="http://www.tutorialspoint.com/cplusplus/cpp_if_statement.htm">if 语句</a></td>
<td>一个 if 语句由一个布尔表达式及紧随其后的一个或多个语句组成</td>
</tr>
<tr>
<td><a href="http://www.tutorialspoint.com/cplusplus/cpp_if_else_statement.htm">if…else 语句</a></td>
<td>一个 if 语句当执行的布尔表达式为假时，可以在后面伴随着一个可选的 else 语句</td>
</tr>
<tr>
<td><a href="http://www.tutorialspoint.com/cplusplus/cpp_if_else_statement.htm">switch 语句</a></td>
<td>一个 switch 语句允许一个变量针对多个不同的值分别进行验证是否满足条件。</td>
</tr>
<tr>
<td><a href="http://www.tutorialspoint.com/cplusplus/cpp_nested_if.htm">嵌套的 if 语句</a></td>
<td>你可以使一个if或者 else if 语句嵌套在另一个 if 或 else if 语句中。</td>
</tr>
<tr>
<td><a href="http://www.tutorialspoint.com/cplusplus/cpp_nested_switch.htm">嵌套的 switch 语句</a></td>
<td>你可以一个 switch 语句中嵌套使用另一个 switch 语句中。</td>
</tr>
</table>

## ？：运算符:
我们在前一章中有可以用来替换 **if...else** 语句的覆盖<a href="http://www.tutorialspoint.com/cplusplus/cpp_conditional_operator.htm">条件语句？：</a>。它具有以下基本形式： 

    Exp1 ? Exp2 : Exp3;
 
其中 Exp1 , Exp2 和 Exp3 是表达式。注意冒号的使用和它的位置。
  
？ 表达式值的计算方式为：首先计算Exp1的值。如果 Exp1 为真，则计算 Exp2 的值作为整个 ？ 表达式的值，如果 Exp1 为假，则计算 Exp3 的值，并且将其作为这个表达式的值。




