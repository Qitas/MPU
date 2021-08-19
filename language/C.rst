.. _lan_c:

C语言
===============

C 语言是一种通用的、面向过程式的计算机程序设计语言。1972 年，为了移植与开发 UNIX 操作系统，丹尼斯·里奇在贝尔电话实验室设计开发了 C 语言。

C 语言最初是用于系统开发工作，特别是组成操作系统的程序。由于 C 语言所产生的代码运行速度与汇编语言编写的代码运行速度几乎一样，所以采用 C 语言作为系统开发语言。

.. contents::
    :local:


C语言编程
-----------

预编译
~~~~~~~~~~~~~~~~~~~~

预编译又称预处理，是整个编译过程最先做的工作，即程序执行前的一些预处理工作。主要处理#开头的指令。如拷贝#include包含的文件代码、替换#define定义的宏、条件编译#if等。

#是把宏参数转化为字符串的运算符，##是把两个宏参数连接的运算符

*  #define STR(arg) #arg 则宏STR(hello)展开时为”hello”
*  #define NAME(y) name_y 则宏NAME(1)展开时仍为name_y
*  #define NAME(y) name_##y 则宏NAME(1)展开为name_1



RAF(Run and Fix)策略
~~~~~~~~~~~~~~~~~~~~~

现实是大量开发者和团队采用这样的开发策略，通过试错的方式降低精力投入，但在实际编写的代码最后可能会遗留下大麻烦，浪费不少于编码的时间进行修复


* 增加在程序构思阶段的时间投入
* 采用流程图和伪代码，梳理程序逻辑
* 在纸上投入的时间多于电脑
* 事先预测可能的问题并寻找解决方法
* 深思后再编程


.. toctree::
    :caption: C关键词
    :maxdepth: 1

    inline <inline>
    static <static>
    const <const>


C语言工具
-----------

格式化
~~~~~~~~~~~~~~

clang-format，它是基于clang的一个命令行工具，能够自动化格式C/C++/Obj-C代码，支持多种代码风格：Google, Chromium, LLVM, Mozilla, WebKit，也支持自定义风格（通过编写.clang-format文件）很方便的同意代码格式。

静态检查
~~~~~~~~~~~~~~

* 功能度：Cppcheck > TscanCode > Flawfinder
* 友好度：TscanCode > Cppcheck > Flawfinder
* 易用性：TscanCode > Cppcheck > Flawfinder


.. toctree::
    :caption: C编译
    :maxdepth: 1

    data <data>
    stack <stack>
    compile <compile>

C++语言
-----------

C++ 几乎是C的超集，只有少量功能C++不支持。


相关区别
~~~~~~~~~~~~~~

C++中的类具有成员保护功能，并且具有继承，多态这类oo特点，而c里的struct没有。C里面的struct没有成员函数,不能继承,派生等等

C++中struct和class的主要区别在于默认的存取权限不同，struct默认为public ，而class默认为private


GP vs OOP
~~~~~~~~~~~~~~

* GP(generic programming)：类属编程，也叫泛型编程
* OOP(Object Oriented Programming)：面向对象编程


类属编程是构成库的另一种方式， 这与传统的oop是不同的。这类程序库一般由类属组件和类属算法组成，组件和算法通过迭代器组装起来，组件则对迭代器提供一定的封装。这种程序库的优点在于能够提供比传统程序库更灵活的组装方式，而不损失效率。

广义的，将泛型程序设计描述为“利用模板设计的程序”（programming with template），将面向对象程序设计描述为“利用继承的程序设计”（programming with inheritance）。

说面向对象/面向过程区别必然是错的，因为C的程序写大了不可避免地还是要模拟一下面向对象的，而C++本身根本不局限于面向对象……


面向对象4大特性

* 封装(encapsulation)
* 继承(Inheritance)
* 多态(Polymorphism)
* 抽象(abstract)


常见问题
-----------

语法逻辑
~~~~~~~~~~~~

* 判断条件的 && || 的逻辑关系常出现问题，大于两个条件的组合，需要理清楚是否有特殊情况
* 边界条件>=, <=等情况是否理清，在边界上的值是否归属到正常的类别中，有没有两边都属于，或者是两边都不属于


潜在问题
~~~~~~~~~~~~

* 除数为0
* 使用空指针
* 访问已经释放的动态内存
* 字符串尾不是空
* 超出数组范围赋值
* 不同类型的变量进行运算
* 不同类型的指针访问内存
* 终止条件不明确导致无法检查递归函数
* 无法检查地址及其运算
* 使用指针前未初始化
