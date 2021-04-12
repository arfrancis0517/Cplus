# 注释

// 单行注释

/* 多行注释 */  

# 变量

数据类型 变量名称 = 初始值;


# 常量

1. #define 常量名 常量值  （宏常量）定义在文件最开始的时候

2. const 数据类型 常量名 = 常量值 修饰这个变量为常量


count << "" <<   << endl;  //输出


## 整数常量

整数常量可以是十进制、八进制或十六进制的常量。前缀指定基数：0x 或 0X 表示十六进制，0 表示八进制，不带前缀则默认表示十进制。

212         // 合法的

215u        // 合法的

0xFeeL      // 合法的

078         // 非法的：8 不是八进制的数字

032UU       // 非法的：不能重复后缀

85         // 十进制

0213       // 八进制 

0x4b       // 十六进制 

30         // 整数 

30u        // 无符号整数 

30l        // 长整数 

30ul       // 无符号长整数

## 浮点常量

3.14159       // 合法的 

314159E-5L    // 合法的 

510E          // 非法的：不完整的指数

210f          // 非法的：没有小数或指数

.e55          // 非法的：缺少整数或分数




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

    布尔数据类型 bool 代表 真 或者 假 只占一个字节

         true 1

         false 0

    枚举类型 enum

          enum enum-name {list of name} 变量名

          enum color {red, blue, green} c;

          c = red;

          enum color { red, green=5, blue } c; // 一般 red = 0, 这里green=5， blue = 6
          

```C++

#include <iostream>
using namespace std;


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

### 使用 typedef 为一个已有的类型取一个新的名字

```C++

typedef type newname; 
typedef int feet;
feet distance;

```
      
### static 存储类

static 存储类指示编译器在程序的生命周期内保持局部变量的存在，而不需要在每次它进入和离开作用域时进行创建和销毁。因此，使用 static 修饰局部变量可以在函数调用之间保持局部变量的值。

static 修饰符也可以应用于全局变量。当 static 修饰全局变量时，会使变量的作用域限制在声明它的文件内。

在 C++ 中，当 static 用在类数据成员上时，会导致仅有一个该成员的副本被类的所有对象共享。

```C++

#include <iostream>
 
// 函数声明 
void func(void);
 
static int count = 10; /* 全局变量 */
 
int main()
{
    while(count--)
    {
       func();
    }
    return 0;
}
// 函数定义
void func( void )
{
    static int i = 5; // 局部静态变量
    i++;
    std::cout << "变量 i 为 " << i ;
    std::cout << " , 变量 count 为 " << count << std::endl;
}

```

### extern 存储类

extern 存储类用于提供一个全局变量的引用，全局变量对所有的程序文件都是可见的。当您使用 'extern' 时，对于无法初始化的变量，会把变量名指向一个之前定义过的存储位置。

当您有多个文件且定义了一个可以在其他文件中使用的全局变量或函数时，可以在其他文件中使用 extern 来得到已定义的变量或函数的引用。可以这么理解， extern 是用来在另一个文件中声明一个全局变量或函数。

extern 修饰符通常用于当有两个或多个文件共享相同的全局变量或函数的时候，如下所示：

第一个文件：main.cpp

```C++
#include <iostream>
 
int count ;
extern void write_extern();
 
int main()
{
   count = 5;
   write_extern();
}
```

第二个文件：support.cpp

```C++

#include <iostream>
 
extern int count;
 
void write_extern(void)
{
   std::cout << "Count is " << count << std::endl;
}
```
在这里，第二个文件中的 extern 关键字用于声明已经在第一个文件 main.cpp 中定义的 count。


# 数据的输入

cin >> 


# 运算符

下表显示了 C++ 支持的关系逻辑运算符。

假设变量 A 的值为 1，变量 B 的值为 0，则：

| 运算符 | 描述 | 实例 |
| &&	| 称为逻辑与运算符。如果两个操作数都非零，则条件为真。	|(A && B) 为假。 |
| ||	| 称为逻辑或运算符。如果两个操作数中有任意一个非零，则条件为真。	| (A || B) 为真。 |
| !	| 称为逻辑非运算符。用来逆转操作数的逻辑状态。如果条件为真则逻辑非运算符将使其为假。	|!(A && B) 为真。 |



# 程序流程结构

## 选择结构

## 循环语句

### 循环控制语句

循环控制语句更改执行的正常序列。当执行离开一个范围时，所有在该范围中创建的自动对象都会被销毁。

C++ 提供了下列的控制语句。点击链接查看每个语句的细节。

| 控制语句 | 描述 |
| ---- | ---- |
| [break 语句](http://www.runoob.com/cplusplus/cpp-break-statement.html) | 终止  **loop**  或  **switch**  语句，程序流将继续执行紧接着 loop 或 switch 的下一条语句。 |
| [continue 语句](http://www.runoob.com/cplusplus/cpp-continue-statement.html) | 引起循环跳过主体的剩余部分，立即重新开始测试条件。 |
| [goto 语句](http://www.runoob.com/cplusplus/cpp-goto-statement.html) | 将控制转移到被标记的语句。但是不建议在程序中使用 goto 语句。 |

