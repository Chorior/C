# Function
---
1. 函数：用于完成特定任务的程序代码的自包含单元；
2. 函数优点：
<pre>
  1. 省去重复代码的编写，便于维护；
  2. 更加模块化，便于阅读和理解；
</pre>
3. 参数是实参，参量是形参；
4. return;只能用于void类型函数；
5. 函数声明必须在函数使用之前进行；
6. ANSI C函数原型参数为空时，若如下所示，编译器会认为你没有进行函数声明，所以不会进行参数检查：
<pre>
  type_name functionName();
</pre>
为了表示函数确实不使用参数，必须（C中）写为如下形式：
<pre>
  type_name functionName(void);
</pre>
7. 不确定函数原型，即参数不固定,stdarg.h提供了定义此类函数的标准方法：
<pre>
  type_name functionName(...);
</pre>
8. 递归：调用自身的过程。执行效率没有循环语句高；
9. 递归基本原理：
<pre>
  1. 每一级的函数调用都有自己的变量；
  2. 每一次函数调用都会有一次返回；
  3. 位于递归调用前的语句和各级被调函数具有相同的执行顺序；
  4. 位于递归调用后的语句的执行顺序和各个被调函数的顺序相反；
  5. 函数代码不会得到复制；
  6. 递归函数中必须包含可以终止递归调用的语句；
</pre>
10. 递归处理反序问题时优势很大；
11. 递归的缺点：
<pre>
  1. 会很快耗尽计算机内存资源；
  2. 难于阅读和理解；
</pre>
12. 多源码文件的编译：
<pre>
  1. UNIX: cc file1.c file2.
  2. LINUX: gcc file1.c file2.c
</pre>
13. #include "xxx.h"中的引号代表包含文件在当前目录下查找；
14. 指针：用来存储地址的变量；用&取得变量的地址；
15.  间接运算符*，当其后跟一个指针或地址时，表示存储在被指向地址中的数值；
16. 定义指针的时候，*和指针名的空格是可选的：
<pre>
   type_name *pointer;
   type_name * pointer;
</pre>