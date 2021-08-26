.. _ide:

IDE
===========

.. contents::
    :local:


Keil
---------------

Keil MDK-ARM（旧称RealView MDK）开发工具源自德国Keil公司，被全球上百万的嵌入式开发工程师验证和使用，是ARM公司目前最新推出的针对各种嵌入式处理器的软件开发工具。

KEIL MDK集成了业内最领先的技术，包括uVision3、uVision4、uVision5集成开发环境与 ARM编译器。支持ARM7、ARM9、Cortex-M0、Cortex-M0+、Cortex-M3、Cortex-M4、Cortex-R4内核核处理器。

Keil MDK可以自动配置启动代码，集成Flash烧写模块，强大的Simulation设备模拟，性能分析等功能，与ARM之前的工具包ADS等相比，ARM编译器的最新版本可将性能改善超过20％以上。
　　
.. toctree::
    :maxdepth: 1

    keil  <keil>

IAR
---------------

IAR Embedded Workbench是一套用于编译和调试嵌入式系统应用程序的开发工具，支持汇编、C和C++语言。它提供完整的集成开发环境，包括工程管理器、编辑器、编译链接工具和C-SPY调试器。

IAR Systems以其高度优化的编译器而闻名。每个C/C++编译器不仅包含一般全局性的优化，也包含针对特定芯片的低级优化，以充分利用您所选芯片的所有特性，确保较小的代码尺寸。IAR Embedded Workbench能够支持由不同的芯片制造商生产，且种类繁多的8位、16位或32位芯片。


.. toctree::
    :maxdepth: 1

    IAR  <iar>


对比
------------

MDK vs IAR
~~~~~~~~~~~~~~

一般来说，如果主要是采用C，并且也不会有太多的library需要连接，MDK和IAR都能胜任。不过这种情形就比较推荐IAR，因为其非常简洁，上手也快，代码层次也能清晰明了。

如果主要是采用C++，并且用到很多特性，或是需要有多个工程进行协作，那么注定只能选择MDK，只不过这样就一定要每个文件最后加上新的空行了。

* 1、MDK不支持层叠文件夹，在文件夹的下一级中必须为文件；IAR支持层叠，可以比较方便管理代码，理清层次。
* 2、MDK连接library，直接添加到文件夹即可；IAR则需要从工程中选项中设置。这应该不算什么问题，毕竟大多数IDE都是这么做的，但最让人很郁闷的是，IAR不能采用相对路径。比如../MUF/MUF.LIB在编译时，就会连接到别的目录，只能采用d:/MUF/MUF.lib绝对路径的形式。
* 3、MDK支持dynamic_cast<>运算符，而IAR文档中明确表示不支持。如果在IAR中强行使用该运算符，则编译会报错：Error[Pe020]: identifier "dynamic_cast" is undefined
* 4、MDK默认只创建工程，工作区是不会直接创建。如果想多个工程聚合，则首先需要创建一个multi的工作区，然后再添加相应的工程。  IAR，默认是创建工程和工作区，如果想多个工程并存，直接添加即可。  相比之下，MDK创建工程的文件比较少，而IARM创建工程生成的文件比较多。
* 5、MDK编译时，只有level的选择；IAR有debug和Release的快速选择
* 6、默认状态，MDK的工具栏功能比较多，有点繁杂；IAM的比较简洁，但相对，也比较单薄。
* 7、MDK的C++有std::这个命名空间；IAR下面的所有容器和算法，都不采用std命名空间
* 8、MDK的程序文件，最后必须要有一个新的空行，否则会有编译警告：warning:  #1-D: last line of file ends without a newline
