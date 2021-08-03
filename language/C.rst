.. _lan_c:

C语言
===============

.. contents::
    :local:

.. toctree::
    :caption: 关键词
    :maxdepth: 1

    inline <inline>
    static <static>
    const <const>

面向对象OOP
-----------

* 封装(encapsulation)
* 继承(Inheritance)
* 多态(Polymorphism)
* 抽象(abstract)




GP vs OOP
-----------

GP：generic programming 类属编程 另一术语 泛型编程 (多么大气的一个词汇)

OOP：Object Oriented Programming 面向对象编程

类属编程是构成库的另一种方式， 这与传统的oop是不同的。这类程序库一般由类属组件和类属算法组成，组件和算法通过迭代器组装起来，组件则对迭代器提供一定的封装。这种程序库的优点在于能够提供比传统程序库更灵活的组装方式，而不损失效率。

广义的，将泛型程序设计描述为“利用模板设计的程序”（programming with template），将面向对象程序设计描述为“利用继承的程序设计”（programming with inheritance）。

说面向对象/面向过程区别必然是错的，因为C的程序写大了不可避免地还是要模拟一下面向对象的，而C++本身根本不局限于面向对象……

C++ 几乎是 C 的超集，只有少量功能 C++ 不支持。


格式化
-----------

clang-format，它是基于clang的一个命令行工具，能够自动化格式C/C++/Obj-C代码，支持多种代码风格：Google, Chromium, LLVM, Mozilla, WebKit，也支持自定义风格（通过编写.clang-format文件）很方便的同意代码格式。

静态检查
-----------

* 检测能力：Cppcheck > TscanCode > Flawfinder
* 友好度：TscanCode > Cppcheck > Flawfinder
* 易用性：TscanCode > Cppcheck > Flawfinder


常见问题
-----------

* 判断条件的 && || 的逻辑关系是常出现问题的地方，大于两个条件的组合，需要理清楚是否有特殊情况
* 边界条件，>=, <=等情况是否理清，在边界上的值是否归属到正常的类别中，有没有两边都属于，或者是两边都不属于

.. toctree::
    :caption: 编译相关
    :maxdepth: 1

    data <data>
    stack <stack>
    compile <compile>
