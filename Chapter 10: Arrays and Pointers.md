# Arrays and Pointers
---
1. 当初始化数组数值数目少于数组元素数目时，剩余数组元素被初始化为0;
2. 当使用空的方括号对数组初始化时，编译器会根据初始化数值数目来确定数组大小，这时可以用sizeof得到数组大小；但尽量不要这样做；
3. 编译器不会检查数组索引是否超出边界；
4. C中const值不是整数常量
5. 数组是顺序存储的；
6. 当且仅当在函数原型或函数定义头的场合中，*array与array[]等价，下面几种原型都是等价的：  
    type_name function(type_name *array,...);  
    type_name function(type_name *,...);  
    type_name function(type_name array[],...);  
    type_name function(type_name [],...);  
7. 间接运算符*与增量运算符++具有相同的优先级，结合时从右至左；
8. C保证为数组分配存储空间时，指向数组之后的第一个位置的指针是合法的，但不保证该地址存储的值；且不能对该地址进行取值运算；
9. const数据的指针只能赋给const指针；
10. (C99标准)变长数组（variable-length array）:可以使用变量定义数组各维，但必须在函数内部或作为函数参量声明，并且声明时不可以初始化；示例如下：  
    type_name function(int rows,int cols,int ar[rows][cols]);
