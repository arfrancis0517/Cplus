# 注释

// 单行注释

/* 多行注释 */  

# 变量

数据类型 变量名称 = 初始值;


# 常量

1. #define 常量名 常量值  （宏常量）定义在文件最开始的时候

2. const 数据类型 常量名 = 常量值 修饰这个变量为常量


count << "" <<   << endl;  //输出

# 关键字

![keyword](https://github.com/arfrancis0517/Cplus/blob/main/C%2B%2B%20Helloworld/keyword.png)

 

# 标识符名规则

标识符不可以是关键字

标识符只能是字母，数字，下划线

第一个字符必须是字母或下划线

字符区分大小写

# 数据类型

数据类型：

    整数型

        int:                         255, 0377, 0xff  Integer 4字节

        short:                        10              Short Integer 2字节 ±2^15

        long:                                         long Integer 4 or 8

        long long:                                     long long Integer 8字节

    实型(浮点型) 表示小数

         float： 4字节，  7位有效数字 一般会在 float num = 3.14f 后面加个f 帮助转换

         double：8字节，  15-16位有效数字

         c++ 里一般显示最多6位有效数字

    字符型

         char 变量 = 'a'； //只能写一个字符  单个字符 一个字节 ASCII 单引号才行
         
         a -- 97       b -- 98     c -- 99  ASCII 可以用 (int)变量 知道
         A -- 65       B -- 66
        
    转义字符(特殊字符)
         
         \a  警报

         \b  退格

         \f  换页

         \n  换行

         \t  水平制表  后面有空格 加上前面的字符一共8个位置 

         \\ 代表\

         "输出字符+转义字符"

    字符串型

         1. 沿用了c语言的字符串: char 变量[] = "字符串值"

         2. c++ 自己的 string 变量 = "字符串值" 但是要加上头文件 #include <string>





          


#include <iostream>
using namespace std;

```C++
int main()

{
   cout << "Size of char : " << sizeof(char) << endl;
   cout << "Size of int : " << sizeof(int) << endl;
   cout << "Size of short int : " << sizeof(short int) << endl;
   cout << "Size of long int : " << sizeof(long int) << endl;
   cout << "Size of float : " << sizeof(float) << endl;
   cout << "Size of double : " << sizeof(double) << endl;
   cout << "Size of wchar_t : " << sizeof(wchar_t) << endl;
   return 0;
}
```
// 本实例使用了 endl ，这将在每一行后插入一个换行符，<< 运算符用于向屏幕传多个值。

// 关键字 sizeof(数据类型/变量) 总结数据大小 
      

