.. _lan_c_const:

const
===============

C语言关键字const就是用来限定一个变量不允许被改变的修饰符（Qualifier）。ANSI C规定数组定义时长度必须是“常量”（C99标准，数组下标可以用变量来表示），“只读变量”也是不可以的，“常量”不等于“不可变的变量”。但是在C++中，局部数组是可以使用变量作为其长度的。

.. contents::
    :local:


相关定义
-----------

const修饰的数据类型是指常类型，常类型的变量或对象的值是不能被更新的。

常量，例如5，"abc"等，肯定是只读的，因为常量是被编译器放在内存中的只读区域，当然也就不能够去修改它。而“只读变量”则是在内存中开辟一个地方来存放它的值，只不过这个值由编译器限定不允许被修改

const使用的基本形式：

1）const在前面
* const int nValue；      //int是const
* const char *pContent;   //char是const, pContent可变
* const char* const pContent; //pContent和*pContent都是const

2）const在后面
* int const nValue; //nValue是const
* char const * pContent; //*pContent是const, pContent可变
* char* const pContent; //pContent是const,*pContent可变
* char const* const pContent; //pContent和*pContent都是const

一个简单的判断方法：指针运算符*，是从右到左，那么如：char const * pContent，可以理解为char const (* pContent)，即* pContent为const，而pContent则是可变的。

int const * p1,p2;
p2是const；(*p1)是一整体，因此(*p1)是const，但p1是可变的。int * p1,p2只代表p1是指向整型的指针，要表示p1、p2都是指针是需写成int * p1,* p2。所以无论是* const p1,p2还是const * p1,p2，里面的*都是属于p1的。


int const * const p1,p2;
p2是const，是前一个const修饰的，*p1也被前一个const修饰，而p1被后一个const修饰。


int * const p1,p2;
p1是const，（* const p1）是整体，所以const不修饰p2。

指针指向及其指向变量的值的变化，const在*的左边，则指针指向的变量的值不可直接通过指针改变（可以通过其他途径改变）；在*的右边，则指针的指向不可变。简记为“左定值，右定向”。
