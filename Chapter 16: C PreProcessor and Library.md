# C Preprocessor and Library
---
1. 编译程序之前，先由预处理器检查程序，根据程序中使用的预处理器指令，预处理器用符号缩略语所代表的内容替换程序中的缩略语；
2. 编译器用空格字符代表每一个注释；
3. 宏：
    * 宏定义：`#define replace_name replace_content`
    * 宏常量可以用来指定标准数组大小，const常量不可以（C中）；
    * 宏常量还可以用来初始化const常量；
    * 类函数宏：`#define SQUARE(X) X*X`，避免在宏参数中使用增量或减量运算符；
    * 宏只能定义成一行；
4. `#include`:
    * 尖括号`<>`告诉预处理器在一个或多个标准系统目录中寻找文件；
    * 双引号`""`告诉预处理器先在当前目录下寻找文件，然后在标准目录中寻找文件；
5. `#undef`:取消定义一个给定的`#define`，即使没有定义，也可以取消定义；
6. `#ifdef,#else,#endif`：
    * 如果预处理器已经定义了`#ifdef`后面的标识符，那么执行所有指令并编译Ｃ代码直至下一个`#if`或`#endif`出现为止；
    * 如果有`#else`指令，那么在未定义标识符时会执行`#else`和`#endif`之间的所有代码；
7. `#ifdef,#else,#endif`与Ｃ中的`if else`很像，主要差异为预处理器不能识别代码块中的花括号`{}`，因此使用`#else`（如果需要）和`#endif`（必须存在）来标记指令块；
8. `#ifndef #else #endif`;
9. 避免多次包含同意头文件的方法：
    <pre>
        #ifndef HEADER_H_
            #define HEADER_H_
            statements;
        #endif       
    </pre>    
10. `#if #elif #else #endif`;
11. 预定义宏：
    * `__DATE__`：进行预处理的日期（"Mmm dd yyyy"形式的字符串文字）；
    * `__FILE__`：当前源代码文件名的字符串文字；
    * `__LINE__`： 当前源代码文件中的行号的整数常量；
    * `__TIME__`：源文件编译时间，"hh: mm: ss";
12. `#pragma c9x on`启用Ｃ99的支持；
13. 内联函数：`inline int square(int x){return x*X;}`
    * 把函数变为内联函数将建议编译器尽可能快地调用该函数；
    * 通常把内联函数原型和定义写在一起，代码量不要过大；
    * 内联函数的定义和调用必须在同一文件中；
14. `<math.h>`:
    * `double exp(double x)`：e的x次方；
    * `double pow(double x)`：x的y次幂；
    * `double sqrt(double x)`：x的平方根；
    * `double fabs(double x)`：x的绝对值；
    * `double ceil(double x)` ：不小于x的最小整数值；
    * `double floor(double x)`：不大于x的最大整数值；
15. `qsort()`：
    * `void qsort(void *base,size_t nmemb,size_t size,int (*compar)(const void *,const void *));`
    * Ｃ允许将任何数据类型的指针转换为void类型指针；
    * 第一个参数为指向要排序的数组头部的指针；
    * 第二个参数是需要排序的项目数量；size_t由`sizeof`返回，`<stdio.h>`中定义；
    * 第三个参数为每个数组元素的大小信息；
    * 第四个参数是指向函数的指针，该函数用于确定排序顺序：
        * 如果第一个项目的值大于第二个项目的值，那么比较函数返回正值；
        * 相等返回0;
        * 小于返回负数；
    <pre>
        int mycomp(const void *p1,const void *p2)
        {
            const double *a1 = (const double *)p1;
            const double *a2 = (const double *)p2;
            
            if(*a1 < *a2)
                return -1;
            else if(*a1 == *a2)
                return 0;
            else
                return 1;                                
        }
        double arr[100] = { 1,2,3,4 };
        qsort(arr,sizeof(arr),sizeof(double),mycomp);        
    </pre>            
16. memcpy与memmove:
    * void *memcpy(void * restrict s1,const void *restrict s2,size_t n);
    * void *memmove(void *s1,const void *s2,size_t n);
    * 上述两个函数均从s2指向的位置复制n个字节到s1指向的位置，且均返回s1的值；
    * 使用memcpy()时，必须确保没有重叠区域；
    * 它们不关心数据类型，只是把一些字节从一个位置复制到另一个位置；
    * `memcpy(arr1,arr2,10*sizeof(int));`
    * `memmove(arr1,arr2,10*sizeof(int));`    
17. 可变参数`<stdarg.h>`:
    * 参量列表中至少有一个后跟省略号的参量；
    * va_list类型代表一种数据对象，该数据存放参量列表中省略号部分代表的参量；`va_list ap;`
    * `va_start(ap,fristParameter);`将ap初始化为参数列表；  
    * `typename val1 = va_arg(ap,typename);`取得参数列表中的值， 从第一个开始；
    * `va_arg()`不提供回退功能；
    * 使用`va_end(ap);`完成清理工作；
    * 只有用`va_start()`重新对ap初始化后，才能使用变量ap;
    <pre>
        double sum(int lim,...)
        {
            va_list ap;
            double tot = 0;
            int i;
            va_start(ap,lim);
            for(i = 0; i < lim ; i ++)
            {
                tot += va_arg(ap,double);
            }        
            va_end(ap);
            return tot;
        }    
    </pre>
