# C++ 的基础知识

C++ 在 C 语言 (Structured Programming) 的基础上添加了类，这是面向对象的编程 OOP

类 是 一类事物的基本特征

对象是 针对类的 具体案例

同时C++模版支持 泛型编程 generic programming

独立于特定数据类型


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

/*
使用 #include 和 python 里 import 一样 这是包含文件

预处理 把iostream添加到程序中 

io 是指 输入和输出， 为了使用 cout cin

还有 cmath， 

如果使用 iostream 而不是 iostream.h，必须使用名称空间编译指令来使之有效

using namespace std;


为了使多个来自不同厂家的代码组合起来更加容易

不同的厂家有不同的名称：相同的名字的不同公司的函数 wanda()

可以用 Microflop::wanda() 和 Piscine::wanda() 来区分


*如果没有 using namespace*

cout 要写成 std::cout <<  << std::endl;

iostream.h 和 cout
iostream 和 std::cout

using 是为了简化

*/

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
| ---- | ---- | ---- |
| &&	| 称为逻辑与运算符。如果两个操作数都非零，则条件为真。	|(A && B) 为假。 |
| ||	| 称为逻辑或运算符。如果两个操作数中有任意一个非零，则条件为真。	| (A || B) 为真。 |
| !	| 称为逻辑非运算符。用来逆转操作数的逻辑状态。如果条件为真则逻辑非运算符将使其为假。	|!(A && B) 为真。 |



# 程序流程结构

## 选择结构


```C++
#include <iostream>
using namespace std;
 
int main ()
{
   // 局部变量声明
   int a = 10;
 
   // 使用 if 语句检查布尔条件
   if( a < 20 )
   {
       // 如果条件为真，则输出下面的语句
       cout << "a 小于 20" << endl;
   }
   cout << "a 的值是 " << a << endl;
 
   return 0;
}
```

```C++
#include <iostream>
using namespace std;
 
int main ()
{
   // 局部变量声明
   int a = 100;
 
   // 检查布尔条件
   if( a < 20 )
   {
       // 如果条件为真，则输出下面的语句
       cout << "a 小于 20" << endl;
   }
   else
   {
       // 如果条件为假，则输出下面的语句
       cout << "a 大于 20" << endl;
   }
   cout << "a 的值是 " << a << endl;
 
   return 0;
}

```


```C++
#include <iostream>
using namespace std;
 
int main ()
{
   // 局部变量声明
   char grade = 'D';
 
   switch(grade)
   {
   case 'A' :
      cout << "很棒！" << endl; 
      break;
   case 'B' :
   case 'C' :
      cout << "做得好" << endl;
      break;
   case 'D' :
      cout << "您通过了" << endl;
      break;
   case 'F' :
      cout << "最好再试一下" << endl;
      break;
   default :
      cout << "无效的成绩" << endl;
   }
   cout << "您的成绩是 " << grade << endl;
 
   return 0;
}
```


## 循环语句

```C++
#include <iostream>
using namespace std;
 
int main ()
{
   // 局部变量声明
   int a = 10;

   // while 循环执行
   while( a < 20 )
   {
       cout << "a 的值：" << a << endl;
       a++;
   }
 
   return 0;
}
```


```C++
#include <iostream>
using namespace std;
 
int main ()
{
   // for 循环执行
   for( int a = 10; a < 20; a = a + 1 )
   {
       cout << "a 的值：" << a << endl;
   }
 
   return 0;
}
```


```C++
#include <iostream>
using namespace std;
 
int main ()
{
   // 局部变量声明
   int a = 10;

   // do 循环执行
   do
   {
       cout << "a 的值：" << a << endl;
       a = a + 1;
   }while( a < 20 );
 
   return 0;
}
```

### 循环控制语句

循环控制语句更改执行的正常序列。当执行离开一个范围时，所有在该范围中创建的自动对象都会被销毁。

C++ 提供了下列的控制语句。点击链接查看每个语句的细节。

| 控制语句 | 描述 |
| ---- | ---- |
| [break 语句](http://www.runoob.com/cplusplus/cpp-break-statement.html) | 终止  **loop**  或  **switch**  语句，程序流将继续执行紧接着 loop 或 switch 的下一条语句。 |
| [continue 语句](http://www.runoob.com/cplusplus/cpp-continue-statement.html) | 引起循环跳过主体的剩余部分，立即重新开始测试条件。 |
| [goto 语句](http://www.runoob.com/cplusplus/cpp-goto-statement.html) | 将控制转移到被标记的语句。但是不建议在程序中使用 goto 语句。 |

# 函数

* 返回值类型

返回类型： 一个函数可以返回一个值。 return_type 是函数返回的值的数据类型。有些函数执行所需的操作而不返回值，在这种情况下，return_type 是关键字 void 。

* 函数名

* 参数列表

* 函数语句

* return表达式

```C++
return_type function_name( parameter list )
{
   body of the function

   return
}
```

## 值传递

形参发生变化，实参也不会怎么改变

## 函数的常用类型

1. 无参无返

```C++
void test01()
{
   cout << "This is a test01" << endl;
}
```

2. 有参无返

```C++
void test02(int a)
{
   cout << "This is test02: a =" << a << endl;
}
```

3. 无参有返

```C++
int test03()
{
   something;

   return 1000;
}
```

4. 有参有返

```C++
int test04(int a)
{
   something;

   return a;
}
```

## 函数声明

在函数定义之前，先告诉编译器

```C++
#include <iostream>
using namespace std;
 
// 函数声明
int max(int num1, int num2);
 
int main ()
{
   // 局部变量声明
   int a = 100;
   int b = 200;
   int ret;
 
   // 调用函数来获取最大值
   ret = max(a, b);
 
   cout << "Max value is : " << ret << endl;
 
   return 0;
}
 
// 函数返回两个数中较大的那个数
int max(int num1, int num2) 
{
   // 局部变量声明
   int result;
 
   if (num1 > num2)
      result = num1;
   else
      result = num2;
 
   return result; 
}
```

## 函数分文件编写

1. 创建头文件 .h

2. 创建函数自己的源文件 .cpp

3. 在头文件中写函数声明

4. 在源文件中写函数定义

# 数组

1. 数据类型 数组名[数组长度];

2. 数据类型 数组名[数组长度] = { 1, 2, 3 };

3. 数据类型 数组名[] = { 1, 2, 3 }

数组名[0], 数组名[1], 数组名[3]...

(int)&数组名[] 可以看保存地址

## 二维数组：

1. 数组类型 数组名[行数][列数];

2. 数组类型 数组名[行数][列数] = {{ 1, 2, 3 } , {1, 2, 3 }};

3. 数组类型 数组名[行数][列数] = { 1, 2, 3, 4 ...};

4. 数组类型 数组名[ ][列数] = { 1, 2, 3, 4 ...};

(int)&数组名[][] 可以看保存地址



```C++
#include <iostream>
using namespace std;
 
#include <iomanip>
using std::setw;
 
int main ()
{
   int n[ 10 ]; // n 是一个包含 10 个整数的数组
 
   // 初始化数组元素          
   for ( int i = 0; i < 10; i++ )
   {
      n[ i ] = i + 100; // 设置元素 i 为 i + 100
   }
   cout << "Element" << setw( 13 ) << "Value" << endl;
 
   // 输出数组中每个元素的值                     
   for ( int j = 0; j < 10; j++ )
   {
      cout << setw( 7 )<< j << setw( 13 ) << n[ j ] << endl;
   }
 
   return 0;
}
```

# 数字 计算

```C++
#include <iostream>
#include <cmath>
using namespace std;
 
int main ()
{
   // 数字定义
   short  s = 10;
   int    i = -1000;
   long   l = 100000;
   float  f = 230.47;
   double d = 200.374;

   // 数学运算
   cout << "sin(d) :" << sin(d) << endl;
   cout << "abs(i)  :" << abs(i) << endl;
   cout << "floor(d) :" << floor(d) << endl;
   cout << "sqrt(f) :" << sqrt(f) << endl;
   cout << "pow( d, 2) :" << pow(d, 2) << endl;
 
   return 0;
}


#include <iostream>
#include <ctime> // 随机数
#include <cstdlib>

using namespace std;
 
int main ()
{
   int i,j;
 
   // 设置种子
   srand( (unsigned)time( NULL ) );

   /* 生成 10 个随机数 */
   for( i = 0; i < 10; i++ )
   {
      // 生成实际的随机数
      j= rand();
      cout <<"随机数： " << j << endl;
   }

   return 0;
}
```

# 指针

通过指针间接访问地址编号

int a = 10;

int *p;


```C++
int    *ip;    /* 一个整型的指针 */
double *dp;    /* 一个 double 型的指针 */
float  *fp;    /* 一个浮点型的指针 */
char   *ch     /* 一个字符型的指针 */
```

## C++ 中使用指针

使用指针时会频繁进行以下几个操作：定义一个指针变量、把变量地址赋值给指针、访问指针变量中可用地址的值。这些是通过使用一元运算符  *****  来返回位于操作数所指定地址的变量的值。下面的实例涉及到了这些操作：

```C++
#include <iostream>

using namespace std;

int main ()
{
   int  var = 20;   // 实际变量的声明
   int  *ip;        // 指针变量的声明

   ip = &var;       // 在指针变量中存储 var 的地址

   cout << "Value of var variable: ";
   cout << var << endl;

   // 输出在指针变量中存储的地址
   cout << "Address stored in ip variable: ";
   cout << ip << endl;

   // 访问指针中地址的值
   cout << "Value of *ip variable: ";
   cout << *ip << endl;

   return 0;
}
```
int * p = (int *)0x1100;

# C++ 引用

在这些声明中，&amp; 读作 **引用** 。因此，第一个声明可以读作 "r 是一个初始化为 i 的整型引用"，第二个声明可以读作 "s 是一个初始化为 d 的 double 型引用"。下面的实例使用了 int 和 double 引用：

```C++
#include <iostream>
 
using namespace std;
 
int main ()
{
   // 声明简单的变量
   int    i;
   double d;
 
   // 声明引用变量
   int&    r = i;
   double& s = d;
   
   i = 5;
   cout << "Value of i : " << i << endl;
   cout << "Value of i reference : " << r  << endl;
 
   d = 11.7;
   cout << "Value of d : " << d << endl;
   cout << "Value of d reference : " << s  << endl;
   
   return 0;
}
```

# 时间

C++ 标准库没有提供所谓的日期类型。C++ 继承了 C 语言用于日期和时间操作的结构和函数。为了使用日期和时间相关的函数和结构，需要在 C++ 程序中引用 &lt;ctime&gt; 头文件。

下面的实例获取当前系统的日期和时间，包括本地时间和协调世界时（UTC）。

```C++
#include <iostream>
#include <ctime>

using namespace std;

int main( )
{
   // 基于当前系统的当前日期/时间
   time_t now = time(0);
   
   // 把 now 转换为字符串形式
   char* dt = ctime(&now);

   cout << "本地日期和时间：" << dt << endl;

   // 把 now 转换为 tm 结构
   tm *gmtm = gmtime(&now);
   dt = asctime(gmtm);
   cout << "UTC 日期和时间："<< dt << endl;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```C++
本地日期和时间：Sat Jan  8 20:07:41 2011

UTC 日期和时间：Sun Jan  9 03:07:41 2011
```

## 使用结构 tm 格式化时间

**tm**  结构在 C/C++ 中处理日期和时间相关的操作时，显得尤为重要。tm 结构以 C 结构的形式保存日期和时间。大多数与时间相关的函数都使用了 tm 结构。下面的实例使用了 tm 结构和各种与日期和时间相关的函数。

在练习使用结构之前，需要对 C 结构有基本的了解，并懂得如何使用箭头 -&gt; 运算符来访问结构成员。

```C++
#include <iostream>
#include <ctime>

using namespace std;

int main( )
{
   // 基于当前系统的当前日期/时间
   time_t now = time(0);

   cout << "Number of sec since January 1,1970:" << now << endl;

   tm *ltm = localtime(&now);

   // 输出 tm 结构的各个组成部分
   cout << "Year: "<< 1900 + ltm->tm_year << endl;
   cout << "Month: "<< 1 + ltm->tm_mon<< endl;
   cout << "Day: "<<  ltm->tm_mday << endl;
   cout << "Time: "<< 1 + ltm->tm_hour << ":";
   cout << 1 + ltm->tm_min << ":";
   cout << 1 + ltm->tm_sec << endl;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```C++
Number of sec since January 1, 1970:1294548238
Year: 2011
Month: 1
Day: 8
Time: 22: 44:59
```
