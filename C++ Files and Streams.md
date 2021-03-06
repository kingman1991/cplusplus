## C++ 文件和流


到目前为止,我们一直在使用 iostream 标准库,它提供了 cin 及 cout方法，分别用于读取标准输入以及写入标准输出。
本教程将教你如何从文件中读取和写入。这需要另一个称为 fstream 的标准 C++ 库,它定义了三个新的数据类型：
<table>
<tr>
<th>数据类型</th><th>描述</th>
</tr>
<tr>
<td>ofstream</td><td>这个数据类型表示输出文件流，用于创建文件以及将信息写入文件。</td>
<tr>
<td>ifstream</td><td>这个数据类型表示输入文件流,用于从文件读取信息。</td>
<tr>
<td>fstream</td><td>这个数据类型通常表示该文件流,兼备有ofstream和ifstream功能，这意味着它可以创建文件,编写文件,以及读文件。</td>
<tr>

<table>



 
使用 C++ 执行文件处理时，头文件 < iostream > 和 < fstream > 必须包含在你的 C++ 源文件里面。

### 打开文件：

需要对一个文件进行读写操作时必须先打开该文件。 ofstream 或 fstream 对象可以用来打开一个文件并且写入； ifstream 对象用于以读入打开一个文件。

下面是 open（） 函数的标准语法,它是 fstream ， ifstream , ofstream 对象的成员。

    void open(const char *filename, ios::openmode mode) ;
在这里,第一个参数指定文件的名称和打开位置,open()成员函数的第二个参数定义了文件应该以哪种模式被打开。
<table>
<tr>
<th>模式标志</th><th>描述</th>
</tr>
<tr>
<td>ios::app</td><td>追加模式。所有输出文件附加到结尾。</td>
<tr>
<td>ios::ate</td><td>为输出打开一个文件并将读/写控制移动到文件的末尾。
</td>
<tr>
<td>ios::in</td><td>打开一个文件去读。</td>
<tr>
<td>ios::out</td><td>打开一个文件去写。</td>
<tr>
<td>ios::trunc</td><td>如果文件已经存在,打开该文件前文件中的内容将被清空。
。</td>
<table>





 
您可以通过逻辑运算将两个或更多的这些值组合到一起。例如, 如果你想以写方式打开一个文件, 并且想在其打开之前清空内容,以防它已经存在的话,使用一下语法规则:

    ofstream outfile;
    outfile.open("file.dat", ios::out | ios::trunc );

同样,你可以以读入和写入目的打开一个文件如下:

    fstream  afile;
    afile.open("file.dat", ios::out | ios::in );

### 关闭文件：
一个 C++ 程序终止时它会自动关闭所有流,释放所有分配的内存并关闭所有打开的文件。但在终止之前，程序员应该关闭所有打开的程序文件始终是一个很好的实习惯。

下面是标准的 close()函数语法,它是一个 fstream，ifstream,以及 ofstream对象的成员。


    void close();

### 写文件：
在使用 C++ 编程时,你通过程序使用流插入操作符 (< <) 将信息写入文件，使用流插入操作符(< <)就像你使用键盘输入将信息输出到屏幕上。唯一的区别是, 你使用一个 ofstream 或 fstream 对象而不是 cout。
###读文件：

您使用留提取符 (>>) 将文件中的信息读入程序就像你使用该运营商从键盘输入信息。唯一的区别是,你使用一个 ifstream 或 fstream 对象而不是 cin 的对象。

### 读取与写入样例：

下面是一段 C++ 程序，以读取和写入方式打开一个文件。将用户输入的信息写入文件后以afile.dat命名文件。程序从文件中读取信息并输出在屏幕上:

    #include <fstream>
    #include <iostream>
    using namespace std;
     
    int main ()
    {
    
       char data[100];
    
       // open a file in write mode.
       ofstream outfile;
       outfile.open("afile.dat");
    
       cout << "Writing to the file" << endl;
       cout << "Enter your name: "; 
       cin.getline(data, 100);
    
       // write inputted data into the file.
       outfile << data << endl;
    
       cout << "Enter your age: "; 
       cin >> data;
       cin.ignore();
       
       // again write inputted data into the file.
       outfile << data << endl;
    
       // close the opened file.
       outfile.close();
    
       // open a file in read mode.
       ifstream infile; 
       infile.open("afile.dat"); 
     
       cout << "Reading from the file" << endl; 
       infile >> data; 
    
       // write the data at the screen.
       cout << data << endl;
       
       // again read the data from the file and display it.
       infile >> data; 
       cout << data << endl; 
    
       // close the opened file.
       infile.close();
    
       return 0;
    }
当上面的代码被编译并执行，将产生如下的样本和输出：

    $./a.out
    Writing to the file
    Enter your name: Zara
    Enter your age: 9
    Reading from the file
    Zara
    9
上面的例子利用cin对象额外的功能,如利用getline()函数来从外部读取线,用ignor()函数忽略先前读取语句留下的额外字符。

### 文件位置指针：


istream 和 ostream 是用来重新定位文件位置的指针成员函数。这些成员函数有 seekg (“seek get”) istream 和 seekp 上ostream (“seek put”)。
seekg 和 seekp 通常的参数是一个长整型。可以指定第二个参数为寻找方向。寻找方向可以 ios: :beg (默认)定位相对于流的开始, io: :scur 定位相对于当前位置的流或ios::end 定位相对于流的结束。
文件位置指针是一个整数值,它指定文件的位置作为一个从文件的开始位置的字节数。


文件位置指针是一个整数值,它指定文件的位置。定位 “get” 文件位置指针的一些示例如下:

    // position to the nth byte of fileObject (assumes ios::beg)
    fileObject.seekg( n );
    
    // position n bytes forward in fileObject
    fileObject.seekg( n, ios::cur );
    
    // position n bytes back from end of fileObject
    fileObject.seekg( n, ios::end );
    
    // position at end of fileObject
    fileObject.seekg( 0, ios::end );
    
