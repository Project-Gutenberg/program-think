---
layout: default
title: 'C++ 的可移植性和跨平台开发[2]&#65306;语法'
date: None
author:
    display_name: 
---

　　目前还有相当一部分开发人员在使用老式编译器干活，这些老式编译器可能对C++98支持不够。因此，当你的代码移植到这些老式的编译器上时，可能会碰到一些稀奇古怪的问题（包括编译出错和运行时错误）。下面这些注意事项有助于你绕过这些问题。  
强调一下，后面提到的好几个条款都是通过回避C++的新语法来保证移植性。如果你用的是新式编译器，那么你可以不理会这些条款。 　　在 C++ 98 标准中，for 循环变量的作用域局限在循环体内。但某些老的编译器（例如Visual C++ 6）认为 for 循环变量的作用域在循环体外。所以如下的代码可能导致移植问题。

{ for(int i\=0; i<XX; i++) { // ... } for(int i\=0; i<XXX; i++) { // ... }
}

　　建议修改为【不同的】循环变量名，如下所示：

{ for(int i\=0; i<XX; i++) { // ... } for(int j\=0; j<XXX; j++) { // ... }
}

  
　　全局类对象的构造函数先于 main() 函数执行，如果某个模块中同时包含若干个全局类对象，则它们的构造函数的调用顺序是【不确定】的。而单键是在第一次调用时被初始化，能避免此问题。另外，单键虽然解决了构造问题，但是析构依然有隐患。更多介绍请看《[C++ 对象是怎么死的？](https://program-think.blogspot.com/2009/02/cxx-object-destroy-overview.html)》系列博文。 　　【不要】在 inline 函数内部使用局部静态变量，【不要】在 inline 函数使用可变参数。 　　因为这些做法有可能导致可移植性的问题。 　　C++ 标准【没有】明确规定函数参数的求值顺序。因此，如下的代码行为是不确定的。

void Foo(int a, int b);
int n \= 1;
foo(++n, ++n);

　　某些【老式】编译器对“模板偏特化”或“模板全特化”支持不够。 　　举例：VC6 不支持“模板偏特化”。 　　为了直观，给出如下例子：

template <typename T\>
class TBase
{
protected: typedef std::vector<T\> Container; Container m\_container;
}; template <typename T\>
class TDerived : public TBase<T\>
{ typedef TBase<T\> BaseClass; public: void Func() { typename BaseClass::Container foo; // 可移植 Container foo; // 【不】可移植 this\->m\_container.clear(); // 可移植 m\_container.clear(); // 【不】可移植 }
};

　　（先声明一下，俺这里说的 RTTI 主要是指 typeid 操作符和 type\_info 类型） 　　首先，由于某些老式编译器可能不支持 typeid 操作符和 type\_info 类型，会导致移植性的问题，这是慎用 RTTI 的一个原因。（如果你用的是新式编译器，不用考虑这个因素） 　　其次，由于标准对于 type\_info 类型的约束比较简单。这导致了不同的编译器对 type\_info 的实现有较大差异。如果你确实要使用 type\_info 类型，建议仅仅使用它的 operator== 和 operator!= 这两个成员函数（只有这两个函数是明确定义的）

　　所以，如果你确实需要在运行时确定类型，又不想碰到上述问题，可以考虑在自己的类体系中加入类型信息来实现。例如：MFC 和 [wxWidgets](http://www.wxwidgets.org/) 都是这么干的。

　　如果在内部类访问外部类的非公有成员，要把内部类声明为外部类的friend。 　　如下代码存在移植问题。

class COuter
{
private: char\* m\_name; public: class CInner { void Print(COuter\* outer) { cout << outer\->m\_name; } };
};

应该改为如下代码：

class COuter
{
private: char\* m\_name; public: class CInner; // 前置声明 friend class CInner; class CInner { void Print(COuter\* outer) { cout << outer\->m\_name; } };
};

　　先看如下代码：

void Foo(short n)
{ // ....
} void Foo(long n);
{ // ....
} Foo(0); // 会导致二义性错误

　　假如没有出现最后一行的那个调用，光编译前面两个重载的 Foo 函数是【不会】出错的。这反而增加了该问题的隐蔽性。 　　下面俺来解释一下： 　　万一这两个 Foo 函数存在于某个公共函数库中，编译这个库都很正常。但是使用这个库的某个程序调用了 Foo(0); 结果就编译失败了。 　　某些标准类型（例如 int、wchar\_t）的字长会随着具体的平台而改变。 　　某些【老式】的编译器不支持类的静态成员常量，可以用枚举来代替。

class CFoo
{ static const int MIN \= 0; // 【不】可移植 enum { MAX \= 64 }; // 可移植
};

　　今天说了这么一大堆，都比较琐碎，估计会有遗漏的。日后如果大伙儿发现有补充的，欢迎在本帖的评论中指教一二。

　　由于篇幅有限，和异常相关的内容留到[下一个话题](https://program-think.blogspot.com/2009/01/cxx-cross-platform-develop-3-exception.html)来聊。

[回到本系列的目录](https://program-think.blogspot.com/2009/01/cxx-cross-platform-develop-0-overview.html#index)

