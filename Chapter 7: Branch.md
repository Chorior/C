# Branch
1. getchar()函数返回来自输入设备的下一个字符；putchar(char)打印它的参数;它们只对字符有效；包含头文件stdio.h;
2. 用ctype.h中的函数判断字符类型，如isalnum()判断是否是字母或者数字；
3. 编译器忽略缩排；
4. C三个逻辑运算符： &&、||、!，如果包含iso.646.h，可以分别用and,or,not代替；
5. !的优先级与增量运算符相同，仅次于圆括号，&&与||优先级低于关系运算符，高于赋值运算符，&&的优先级比||高；
6. 唯一的三元运算符，条件运算符？：，expreeion1 ? expression2 : expression3;
7. continue使剩余的迭代部分被忽略，开始下一次迭代；
8. break使当前循环终止；
9. 多重选择：
```
        swith(integer expression)
        {
            case constant0: statements;break;
            case constant1: statements;break;
            case constant2: statements;break;
            ...
            default: statements;
         }
```
10.  如果一个case处理完毕之后没有break，那么会执行下一个case;
11. break用于循环和swith；而continue只用于循环；
