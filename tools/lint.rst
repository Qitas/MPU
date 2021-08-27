.. _lint:

LINT
===========

.. contents::
    :local:

PC-Lint
-------------


PC-Lint版本：PC-lint for C/C++ (NT) Vers. 9.00L (https://files.cnblogs.com/files/godan/Gimpel_PC_Lint_9.rar) 免费可用版本

下载好PC-Lint后，需要再去官网下载最新的patch包。 https://gimpel.com/


安装配置
~~~~~~~~~~~

PC-Lint是C/C++软件代码静态分析工具，你可以把它看作是一种更加严格的编译器。它不仅可以检查出一般的语法错误，还可以检查出那些虽然符合语法要求但不易发现的潜在错误。
C语言的灵活性带来了代码效率的提升，但相应带来了代码编写的随意性，另外C编译器不进行强制类型检查，也带来了代码编写的隐患。PCLint识别并报告C语言中的编程陷阱和格式缺陷的发生。它进行程序的全局分析，能识别没有被适当检验的数组下标，报告未被初始化的变量，警告使用空指针，冗余的代码，等等。软件除错是软件项目开发成本和延误的主要因素。PClint能够帮你在程序动态测试之前发现编码错误。这样消除错误的成本更低。
使用PC-Lint在代码走读和单元测试之前进行检查，可以提前发现程序隐藏错误，提高代码质量，节省测试时间。并提供编码规则检查，规范软件人员的编码行为。
由于PC-LINT对于一般程序员来说可能比较陌生，有好多人安装了也不知道怎样配置和使用。

.. image:: ./images/pclint.jpg
    :target: https://item.taobao.com/item.htm?spm=a1z09.2.0.0.4cb32e8dCPqAi3&id=641754177657&_u=vgas3eue654


代码分析
~~~~~~~~~~~

641: (Warning -- Converting enum 'XXX' to int)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

不能直接把enum转成int;
