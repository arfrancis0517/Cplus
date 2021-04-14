# 结构

```C++
struct Books
{
   char  title[50];
   char  author[50];
   char  subject[100];
   int   book_id;
}book;  
```

例子

```C++
#include <iostream>
#include <cstring>
 
using namespace std;
 
struct Books
{
   char  title[50];
   char  author[50];
   char  subject[100];
   int   book_id;
};
 
int main( )
{
   struct Books Book1;        // 声明 Book1，类型为 Book
   struct Books Book2;        // 声明 Book2，类型为 Book
 
   // Book1 详述
   strcpy( Book1.title, "Learn C++ Programming");
   strcpy( Book1.author, "Chand Miyan"); 
   strcpy( Book1.subject, "C++ Programming");
   Book1.book_id = 6495407;

   // Book2 详述
   strcpy( Book2.title, "Telecom Billing");
   strcpy( Book2.author, "Yakit Singha");
   strcpy( Book2.subject, "Telecom");
   Book2.book_id = 6495700;
 
   // 输出 Book1 信息
   cout << "Book 1 title : " << Book1.title <<endl;
   cout << "Book 1 author : " << Book1.author <<endl;
   cout << "Book 1 subject : " << Book1.subject <<endl;
   cout << "Book 1 id : " << Book1.book_id <<endl;

   // 输出 Book2 信息
   cout << "Book 2 title : " << Book2.title <<endl;
   cout << "Book 2 author : " << Book2.author <<endl;
   cout << "Book 2 subject : " << Book2.subject <<endl;
   cout << "Book 2 id : " << Book2.book_id <<endl;

   return 0;
}
```

当上面的代码被编译和执行时，它会产生下列结果：

```C++
Book 1 title : Learn C++ Programming
Book 1 author : Chand Miyan
Book 1 subject : C++ Programming
Book 1 id : 6495407
Book 2 title : Telecom Billing
Book 2 author : Yakit Singha
Book 2 subject : Telecom
Book 2 id : 6495700
```

下面是一种更简单的定义结构的方式，您可以为创建的类型取一个"别名"。例如：

```C++
typedef struct
{
   char  title[50];
   char  author[50];
   char  subject[100];
   int   book_id;
}Books;
```

现在，您可以直接使用  _Books_  来定义  _Books_  类型的变量，而不需要使用 struct 关键字。下面是实例：

```C++
Books Book1, Book2;
```


# 面向对象

```C++
class student 
{
   string name;
   int age;
}

// 共有和私有

class student
{
   public:
      string name;

   private:
      int age;
       
} 

// student aa
// aa.name = 

// 成员函数的重载

// 用set()使得在类外重新赋值 具体内容在类外面

class student
{
   public:
      string name;
      int age;

      bool set(int a);
      bool set(string a)
       
} 
```

# 构造函数

```C++
// 无参数

#include <iostream>
using namespace std;

class Time // 先声明构造函数
{
public :
    Time() // 这是构造函数 没有输入值和返回值 名字和类的一样
    {
        hour = 0;  // 在类里定义构造函数
        minute = 0; // 这些都是默认值
        sec = 0;
    }
    void showtime();
private:
    int hour;
    int minute;
    int sec;
};
void Time::showtime() 
{
    cout<<"hour:"<<hour<<"min:"<<minute<<"sec:"<<sec<<endl;
}

 int main()
 {
 Time time; // 赋上默认值
 time.showtime();
 getchar();
 return 0; 
 }

 // or

 #include <iostream>
using namespace std;

class Time
{
public :
    Time();
    void showtime();
private:
    int hour;
    int minute;
    int sec;
};
void Time::showtime()
{
    cout<<"hour:"<<hour<<endl<<"min:"<<minute<<endl<<"sec:"<<sec<<endl;
}
Time::Time() // 在类外定义构造函数
{
    hour = 0;
    minute = 0;
    sec = 0;
}
 int main()
 {
 Time time; //
 time.showtime();
 getchar();
 return 0;
 }




 // 带参数

 #include <iostream>
using namespace std;

class Time
{
public :
    Time(int,int,int); // 带参数的构造函数 可以同名函数 用不同输入类型区别
    void showtime();
private:
    int hour;
    int minute;
    int sec;
};
void Time::showtime()
{
    cout<<"hour:"<<hour<<endl<<"min:"<<minute<<endl<<"sec:"<<sec<<endl;
}
Time::Time(int h,int m,int s) // 带参数的函数定义 这样就不是默认值了 可以动态输入 前一个Time是类 后一个是构造函数
{
    hour = h;
    minute = m;
    sec = s;
}
 int main()
 {
 Time time(1,2,3);
 time.showtime();
 getchar();
 return 0;
 }




 // 构造函数的重载

 #include <iostream>
using namespace std;

class Time
{
public :
    Time();
    Time(int,int,int);
    void showtime();
private:
    int hour;
    int minute;
    int sec;
};
void Time::showtime()
{
    cout<<"hour:"<<hour<<endl<<"min:"<<minute<<endl<<"sec:"<<sec<<endl;
}
Time::Time()
{
    hour = 0;
    minute = 0;
    sec = 0;
}
Time::Time(int h,int m,int s)
{
    hour = h;
    minute = m;
    sec = s;
}
 int main()
 {
 Time time1(1,2,3); // 引用的是 Time::Time(int h,int m,int s)
 time1.showtime();
 Time  time2; // 引用的是 Time::Time()
 time2.showtime();
 getchar();
 return 0;
 }


```

# set ()

```C++
#include <iostream>
#include <set>

 using namespace std;
 
int main()
{
     set<int> s;
     s.insert(1);
     s.insert(2);
     s.insert(3);
     s.insert(1);
     cout<<"set 的 size 值为 ："<<s.size()<<endl;
     cout<<"set 的 maxsize的值为 ："<<s.max_size()<<endl;
     cout<<"set 中的第一个元素是 ："<<*s.begin()<<endl;
     cout<<"set 中的最后一个元素是:"<<*s.end()<<endl;
     s.clear();
     if(s.empty())
     {
         cout<<"set 为空 ！！！"<<endl;
     }
     cout<<"set 的 size 值为 ："<<s.size()<<endl;
     cout<<"set 的 maxsize的值为 ："<<s.max_size()<<endl;
     return 0;
}

```


# 析构函数 销毁数据

```C++

student *p = new student (20, '张三')；

delete p;

// 这样才能生效 释放内存

student :: ˜studnet ()

```
# 常成员函数 const

```C++
#pragma once

#include 
class CTestBasic
{
public:
	//常成员：默认初始化
	CTestBasic() :conNum(0) {
		value = -1;
		pValue = new int;
	}
	//常成员：重载初始化
	CTestBasic(int num ) :conNum(num) {} //常成员函数：又成为只读函数，不能改变成员变量的值
	int getsNum() const;
	int getcNum() const;
	int get_scNum() const;
	int getPointerValue() const;

	~CTestBasic();
private:
	//const成员变量不能在类定义处初始化，[ 只能通过构造函数初始化列表进行 ]，并且必须有构造函数
	const int conNum;

	//static成员变量不能在构造函数初始化列表中初始化，因为它不属于某个对象.
	static int sNum; 
    const static  int scNum = 100;
	int value;
	int* pValue;
};

#include "CTestBasic.h"

//静态成员类外初始化
int CTestBasic::sNum = 1;

//函数定义也必须包含const 关键字
int CTestBasic::getsNum() const
{
	return sNum;
}

int CTestBasic::getcNum() const
{
	return conNum;
}

int CTestBasic::get_scNum() const
{
	return scNum;
}

int CTestBasic::getPointerValue() const
{
	*pValue = 200;
	//pValue++; Error: pValue的值不能改变
	return *pValue;
}

CTestBasic::~CTestBasic()
{
}
```

# 静态成员 static

描述全局情况，和某个对象属性无关，叫做静态成员数据

读取静态成员数据的方法叫做静态成员函数

# 正规写类的定义

public：

方法

private:
 
数据

# 类的派生继承

```C++

class undergraduate : public student // 本科生类定义，冒号代表从 student类 公有 派生出来的
{

public:
    string course; // 这行新增定义了一个公开字符串属性course，比如 数学

}


class postgraduate : public student // 研究生定义
// public 表示 公有继承 只继承student公有的部分， 同时也做研究生的公有部分
// 无法继承 私有 部分
{

public:
    string research; // 比如 芯片设计

}

postgraduate bb; // 没有构造函数 有默认值

bb.set(25); // postgraduate 类没有set方法，调用父类student中的方法，对age赋值

```
派生 可以 自动继承 父类的属性和方法

## 类在不同情况下的继承

protect 保护 和 public private 同级

将父类 的private 替换成 protect

对 父类 没什么影响

```C++

class postgraduate : public student{public, protect}； // 研究生 也可以继承 私有 部分了

postgraduate {public，protect}；

postgraduate bb; // 没有构造函数 有默认值

bb.set(25); // postgraduate 类没有set方法，调用父类student中的方法，对age赋值

class postgraduate : private student {public A, private B} // 只继承 A 且为 私有

class postgraduate : protect student {public A, protect B} // 继承 A B 且都为 保护

```
private 里内容无论如何都不能继承

## 子类构造函数



