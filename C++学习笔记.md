# C++学习笔记

### 1、双冒号、using和namespace

* **namespace**主要用来解决命名冲突的问题
  * 必须在全局作用域下声明
  * 命名空间下可以放函数，变量、结构体和类
  * 命名空间可以嵌套命名空间
  * 命名空间是开放的，可以随时加入新成员（添加时只需要再次声明namespace，然后添加新成员即可
  * 命名空间可以起别名

* **双冒号**::作用域运算符
  * 全局作用域符（::name）：用于类型名称（类、类成员、成员函数、变量等）前，表示作用域为全局命名空间
  * 类作用域符（class::name）：用于表示指定类型的作用域范围是具体某个类的
  * 命名空间作用域符（namespace::name）:用于表示指定类型的作用域范围是具体某个命名空间的

* **using**分为using声明和using编译指令
  * `using std::cout; //声明`
  * `using namespace std; //编译指令`
  * 尽量使用声明而不是编译指令，不同命名空间中可能会有相同的变量名，编译指令执行两个命名空间后，会产生二义性
  * 一般来说，使用using声明比使用using编译指令更安全，这是由于它只导入指定的名称；**using声明使特定的标示符可用，using编译指令使整个名称空间可用。**

### 2、C++相对于C做了哪些增强

​			1、 全局变量的检测增强

​			2、 函数的检测增强

​					参数类型检测、返回值检测、函数调用参数检测增强

​			3、类型转换检测增强

​			4、struct增强

​			5、bool类型增强

​			6、3目运算符增强，c语言中返回的是值，c++中返回的是变量

​			7、const增强，

​					在c中，const修饰的变量是伪常量，编译器会分配内存;c中const默认外部链接

​					在c++中，const不会分配内存，其存储在符号表中，即键值对；c++中const默认内部链接

​			8、const内存分配情况

​					取地址时会分配临时的内存

​					exterm，编译器也会给const分配内存

​					用普通变量初始化const变量时

​					自定义数据类型，加const也会分配内存；

### 3、引用

#### 1、基本语法

`Type &别名 = 原名；`

引用必须初始化/初始化后不可以被修改

#### 2、引用的注意事项

 引用的注意事项
 1.必须引用合法的n内存空间 `int &a=10;  //不合法`
 2.不要返回局部变量的引用

``int& dowork2()` 
 `{   
int a = 10;`
return a;

}`

3.如果函数的返回值是引用，则这个函数k可以作为左值；

#### 3、引用的本质

在c++内部实现一个指针常量

`Type& ref = val;	//Type* const ref =&val;`

#### 4、指针的引用

一级指针引用可以代替二级指针；

#### 5、常量的引用

修饰形参为只读

const int &a=10;会分配内存

### 4、类

1、类和对象的关系

类是对对象的抽象

对象是对类的实现

### 5、内联函数

#### 1、宏定义有哪些缺陷

- 宏定义都是直接嵌入代码中的，所以代码可能更多一点
- 嵌套定义过多会影响程序的可读性，而且容易出错
- 对于带参数的宏而言，由于是直接转换，并不会检查参数是否合法，存在安全隐患，预编译语句仅仅是单独的值替换，缺乏类型检测机制。
- 宏不是函数、宏不是语句、宏并不是类型定义

#### 1、内联函数

- 解决类宏缺陷问题
- 给编译器的一个建议，加上关键字，编译器不一定按照内联处理
- 不加关键字inline,也许编译器会偷摸加上inline

#### 2、内联函数的注意事项

- `inline void func();		//内联函数的声明`
- `inline void func(){	};	// 如果函数实现的时候，没有加inline,那么这个函数依旧不算内联函数`
- `类内部的成员函数，默认前面会加inline;`

### 6、C++语言的封装

1. 将属性和行为作为一个整体来表示生活中具体的事物
2. 有访问权限

- struct和class是一个意思，唯一的不同是默认权限，struct成员的默认权限是public,class的默认权限是private
- public：		类内 类外都可以访问
- protected: 	类内，该类的子类可以访问 在类外不可以访问到
- private			类内可以访问，类外不可以访问（子类不可以访问）  

3. 建议将所有成员变量设为私有，通过set和get方法来修改成员变量

### 7、对象的构造和析构

#### 	1、什么是构造函数和析构函数

代码链接：https://blog.csdn.net/weixin_45233461/article/details/106089555

- 对象的初始化和清理
- 如果程序员没有提供构造函数和析构函数，系统会默认提供，空实现！

  #### 2、构造函数

- 与类名相同
- 没有返回值
- 不写void
- 可以发生重载（可以有参数）
- 构造函数由编译器自动调用，而不是手动，而且只会调用一次

  #### 3、析构函数

- 与类名相同，类名前加“~”
- 也没有返回值
- 不写void,不可以有参数（不能发生重载）

- 自动调用，只会调用一次

  #### 4、构造函数的分类和调用

代码连接：https://blog.csdn.net/weixin_45233461/article/details/106235142

- 按照参数分类
  - 无参构造（默认构造）
  - 有参构造
- 按照类型分类
  - 普通构造函数
  - 拷贝构造函数
- Person(1):匿名对象
  
  - 不能用拷贝构造函数初始化匿名对象
  
  #### 5、拷贝构造函数调用时机

代码连接：https://blog.csdn.net/weixin_45233461/article/details/106236486

1. 用已经创建好的对象初始化新的对象
2. 以值传递的方式给函数参数传值
3. 以值的方式返回局部对象
4. Release模式下会对代码进行优化（VS 中！)

   #### 6、构造函数的调用规则

系统默认给一个类提供三个函数 默认函数、拷贝函数、析构函数

1. 当我们提供了有参构造函数，那么系统就不会再给我们提供默认构造函数了，但是系统会提供默认拷贝构造函数，进行简单的值拷贝
2. 当提供了拷贝构造函数，系统将不会提供其他构造函数

   #### 7、深拷贝和浅拷贝

代码链接：https://blog.csdn.net/weixin_45233461/article/details/106257127

**浅拷贝**

系统提供的默认拷贝构造，会进行简单的值拷贝

如果属性里面有指向堆区空间的数据，那么简单的值拷贝会导致重复的释放内存的异常

**深拷贝**

解决上述问题，需要我们自己提供拷贝构造函数，进行深拷贝

#### 	8、初始化列表语法

代码链接：https://blog.csdn.net/weixin_45233461/article/details/106268605

在构造函数后面+ ：属性（参数、值），属性（参数、值）......

#### 	9、类对象作为成员变量

代码链接：https://blog.csdn.net/weixin_45233461/article/details/106362440

1. 当类对象作为类的成员函数时，构造顺序是先构造类对象的构造，然后构造自己
2. 析构的顺序相反

   #### 10、new运算符和delete运算符

代码链接：https://blog.csdn.net/weixin_45233461/article/details/106365616

1. Person *p=new Person;会返回一个Person指针
2. 默认调用构造函数，开辟空间，返回的不是void *,不需要强制转换
3. delete释放
4. new出的对象用void *接收，会出现释放不了对象
5. new出来的是数组，如何释放，使用delete []
6. new出来的是数组，肯定会调用默认构造

### 8、类

#### 8.1、静态成员变量和静态成员函数

代码链接：https://blog.csdn.net/weixin_45233461/article/details/106382012

- 静态成员变量

  - 静态成员变量编译阶段分配内存

  - 所有对象共享数据

  - 可以通过对象访问，通过类名访问

  - 有权限控制

  - 类内声明，类外初始化

- 静态成员函数

  - 可以访问静态成员变量，不能访问普通成员变量
  - 普通的成员函数都可以访问
  - 静态成员函数有权限
  - 可以通过对象访问，也可以通过类名访问

#### 8.2 单例模式

代码链接：https://blog.csdn.net/weixin_45233461/article/details/106391351

单例模式案例2：https://blog.csdn.net/weixin_45233461/article/details/106397128

1. 目的：为了让类中只有一个实例，实例也不需要自己释放
2. 将默认构造和拷贝构造私有化
3. 内部维护一个对象指针
4. 私有化唯一指针
5. 对外提供getinstance 方法来访问这个指针
6. 保证了类中只能实例化一个唯一的对象

#### 8.3 C++模型初探，成员变量和成员函数分开储存

代码链接：https://blog.csdn.net/weixin_45233461/article/details/106398109

1. 成员变量和成员属性是分开储存的
2. 空类的大小为1
3. 只有非静态成员才属于对象身上
4. 注意字节对齐

#### 8.4 this指针的 使用

代码链接：https://blog.csdn.net/weixin_45233461/article/details/106408506

1. this指针永远指向当前对象
2. 解决命名的冲突
3. 如果返回实体，返回*this 指向本体
4. 非静态的成员函数才有静态指针

#### 8.5 空指针访问成员函数

代码链接：https://blog.csdn.net/weixin_45233461/article/details/106408461

1. 如果成员函数没有用到this,那么空指针可以直接访问
2. 如果成员函数用到了this指针，就要注意，可以加this判断，如果this为空，return掉！

#### 8.6 常函数和常对象

代码链接：https://blog.csdn.net/weixin_45233461/article/details/106410024

1. 常函数 void func() const{}
2. 常函数 修饰的是this指针，const type * const this
3. 常函数不能修改this指针执行的值
4. 成对象 在对象前加入const修饰 const Person p1;
5. 常对象 不能调用普通成员函数，可以调用常函数
6. 用mutable修饰的关键字是在常函数中可以修改的

#### 8.7 友元函数

1. 全局函数做友元函数
   
   代码链接：https://blog.csdn.net/weixin_45233461/article/details/106516228
   
   1. 将全局函数写到类中做声明，并在最前面加上关键字 friend
   
2. 类作为友元类

   代码链接：https://blog.csdn.net/weixin_45233461/article/details/106516216

   1. friend class 类名	
   2. 友元关系不能被继承
   3. 友元关系是单向的，类A是类B的友元，但类B不一定是类A的友元
   4. 友元关系不具有传递性
   
3. 让成员函数作为友元函数

   代码链接：https://blog.csdn.net/weixin_45233461/article/details/106589894

   1. friend void goodGay::visit();

### 9、运算符重载

1. #### 加号运算符重载

   代码链接：https://blog.csdn.net/weixin_45233461/article/details/106627568

   1. 如果想要自定义类型进行+运算，那么需要重载+运算符
   2. 在成员函数或者全局函数里重写一个+运算符的函数
   3. 函数名为operator+（）{}
   4. 运算符重载也可以提供多个版本

2. #### 左移运算符的重载

   代码链接：https://blog.csdn.net/weixin_45233461/article/details/106627628

   1. 不要随意乱用符号重载
   2. 内部数据类型的运算符是不可以重载的
   3. cout << 直接对person自定义数据类型进行输出
   4. 写到全局函数中 ostream& operator<<(ostream &cout,Person &p1){}
   5. 如果重载时候想访问p1的私有成员，那么全局函数要做Person的友元函数
   
3. #### 前置++、后置++运算符重载

    代码链接：https://blog.csdn.net/weixin_45233461/article/details/106657578

   1. 自己实现int类型 	MyInteger
   2. 内部维护int的数据
   3. MyInteger myint
   4. myint++、++myint的实现
   5. 重载++运算符 operator++():前置    operator++(int):后置
   6. 前置思路：先++,后返回自己   后置思路：先保存住原有值，内部++,返回临时数据
   
4. #### 智能指针的实现

    代码链接：https://blog.csdn.net/weixin_45233461/article/details/106658010

    1. Person类有成员函数showage()
    2. 如果new出来的Person对象，程序员要去主动释放 delete
    3. 有了智能指针，让只能指针托管这个Person对象，就不用操心对象的释放了，让只能指针管理。
    4. 为了让智能指针像普通的Person*指针一样使用，就要重载->和 *；
    
5. 赋值运算符重载

    ​	代码链接：

    1. 系统默认给类提供，赋值运算符的写法 简单的值拷贝
    2. 导致如果类中有指向堆区的指针，就可能出现深浅拷贝的问题
    3. 所以需要重载=运算符
    4. 如果想链式编程 return *this;

6. []运算符重载

    1. 返回数组索引的引用
    2. int& operator[](int index)
    3. return this->pAddress[index]

## 关键字

### 1、const关键字

https://www.runoob.com/w3cnote/cpp-const-keyword.html

### 2、malloc关键字

https://www.runoob.com/cprogramming/c-function-malloc.html

### 3、strlen关键字

https://www.runoob.com/cprogramming/c-function-strlen.html

strlen(name)+1；+1的目的是包含结束符！

### 4、explicit关键字

https://blog.csdn.net/u012278016/article/details/79930952?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522159049699719724835825064%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=159049699719724835825064&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-2-79930952.pc_insert_v7&utm_term=explicit%E5%85%B3%E9%94%AE%E5%AD%97

防止隐式类型转换



## 学习问题总结：

### 1、C++11编译问题：warning: ISO C++11 does not allow conversion from string literal to 'char *'

https://blog.csdn.net/wangzhezhilu001/article/details/104216989?utm_medium=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase&depth_1-utm_source=distribute.pc_relevant_t0.none-task-blog-BlogCommendFromMachineLearnPai2-1.nonecase

### 2、字节对齐

https://blog.csdn.net/cclethe/article/details/79659590



​	

​					