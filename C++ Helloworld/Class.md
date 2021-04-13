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

// 

```