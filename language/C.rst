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
    stack <stack>
    data <data>
    compile <compile>


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
