# String Function
---
1. 字符串常量： 位于一对双引号中的任何字符；
2. 如果字符串常量中间没有空格或者间隔的是空格，ANSI C会将其串联起来，例如：
<pre>
char greeting[50] = "Hello,and""how are""you""today!";
和
char greeting[50] = "Hello,and how are you today!";
是相等的。
</pre>
3. 用数组存储字符串时，一定要确保元素数比字符串长度至少多一。用于存储空字符；
4. 用数组和指针存储字符串的不同：数组是常量，而指针是变量，指针可以使用增量运算符；
5. 初始化一个指向字符串常量的指针时，建议使用const修饰符，避免出现不必要的麻烦；
6. C库提供了三个读取字符串的函数：gets、fgets、scanf;
  1. gets():  
    * gets()读取换行符之前的所有字符，并在这些字符后面添加一个空字符，它将读取换行符并将其丢弃,它返回字符串的地址,出错时返回空地址；  
    * gets()的不足之处在于它不检查预留存储区是否够容纳实际输入的数据，多出来的数据简单的溢出到相邻内存区；
    <pre>
    char name[SIZE];
    char * ptr;
    ptr = gets(name);
    </pre>
  2. fgets()：  
    * 为文件I/O设计，第二个参数用以说明最大读取字符数，如果这个值为n，那么它会读取最多n-1个字符或者读完一个换行符为止，最先满足的结束输入；  
    * fgets()会读取到换行符，并把它存到字符串里；
    * 第三个参数说明读取那个文件，键盘使用stdin;
    <pre>
    char name[SIZE];
    char * ptr;
    ptr = fgets(name,SIZE,stdin);
    </pre>
  3. scanf():
    <pre>
    char name[SIZE];
    scanf("%s",name);
    </pre>
7. C库提供了三个用于输出字符串的函数：puts、fputs、printf;
  1. puts():  
    * 只要给出字符串参数的地址；
    * 显示字符串时自动添加换行符；
    * 遇到空字符时，停止输出；
    <pre>
    char str1[] = "string1";
    const char * str2 = "string2";
    puts(str1);
    puts(str2);
    </pre>
  2. fputs():  
    * 第二个参数说明要写的文件；
    * 不会自动添加换行符；
    <pre>
    char str[SIZE] = "string";
    fputs(str,stdout);
    </pre>
  3. printf():  
    * 不会自动添加换行符；
    <pre>
    char str[SIZE] = "string";
    printf("%s\n",str);
    </pre>
8. 字符串函数,`<string.h>`:  
  1. strlen()不计算空字符：
    <pre>
    char str[] = "string";
    int size = strlen(str);
    </pre>
  2. strcat()将第二个字符串的拷贝添加到第一个字符串的结尾，返回第一个字符串的地址：
  <pre>
  char str1[] = "string1";
  char str2[] = "string2";
  strcat(str1,str2);
  </pre>
  3. strncat():  
    * strcat()不检查第一个数组是否能够再容纳第二个字符串；
    * strncat()添加另外一个参数来指明最对允许添加的字符数；
    * `strncat(str1,str2,n)`将str2添加到str1,直到加到n个字符或者遇到空字符为止；
  4. strcmp():  
    * 如果第一个字符串在字母表中的顺序先于第二个字符串，那么strcmp()返回负数，否则返回正数；
    * 相等时返回0;
    * 空字符在ASCII中排第一；
  5. strncmp():  
    * 第三个参数用以指定比较的字符数；
    * `strncmp(str1,str2,n)`;
  6. strcpy():  
    * 复制第二个字符串到第一个字符串；
    * `strcpy(str1,str2)`;
  7. strncpy():  
    * 第三个参数用以指定复制字符的个数；
    * `strncpy(str1,str2,n);`如果源字符串字符数少于n，那么目标字符串中就以空字符填充，否则，空字符就不会被复制；
  8. strchr():  
    * 第一个参数为字符串地址；
    * 第二个参数为字符；
    * 返回字符在字符串中的第一个位置的指针；
    * 失败时，返回空指针；
    * `strchr(str,ch);`
9. sprintf(),`<stdio.h>`：  
  * 第一个参数是目标字符串地址；
  * 剩余参数与printf一样；
  * 写到字符串里；
  * `sprintf(str1,"%s",str2);`
10. C编译器允许main()没有参数或者有两个参数，第一个参数是命令行中的字符串数，第二个参数是一个指向字符串的指针数组：  
  `int main(int argc,char *argv[])`
11. atoi(),`<stdlib.h>`:  
  * 如果字符串是一个整数，`atoi(str)`返回字符串中的整数值；
  * 如果字符串是一个浮点数，`atof(str)`返回字符串中的浮点数；
