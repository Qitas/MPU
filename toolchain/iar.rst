.. _iar:

IAR
===========

.. contents::
    :local:

ARM
-----------

STM8
-----------




.. code-block:: bash

    extern volatile BYTE sppRxStatus;
    extern volatile BYTE sppTxStatus;
    __no_init SPP_RX_STRUCT rxData @ "PM0_XDATA";
    __no_init SPP_TX_STRUCT txData @ "PM0_XDATA";

_no_init在编程环境中是蓝色的字。

@是指定地址，__no_init 是一个SEGMENT，是给LINKER用的，定义到不初始化的块中去。
@就是指定地址，这个应该没什么好说的了，大部分编译器都这么用。你应该理解这个吧。
你定义全局变量的时候比如int char;  即使你没有赋值给他，编译器还是会给他一个初始化值0，编译的时候编译器把他分配到初始化为零的那个SEGMENG中去了。编译器默认的有几个块，初始化为零的块，初始化不为零的块，和不初始化的块，你可以定义自己的块，如你的PM0_XDATA，这个就是你自己定义的一个块，那你的这个块是个什么属性呢，就是，__no_init 属性，有了这个属性，编译器只给你分配空间，不给你初始化。

常见问题
~~~~~~~~~

用IAR打开STM8时，出现“Unable to create configuration 'Debug' using tool chain ‘STM8’,

出现这个问题的原因是按装的IAR不正确，要装ST for STM8版本的，而不能用ST for ARM版本的

IAR安装多个不同的版本，会存在点击eww文件自动通过上次打开的版本打开工程文件，所以会有这个问题，解决办法是通过点击打开STM8对应的IAR版本，通过文件导入打开工程文件，之后就可以通过点击打开STM8的开发文件了


8051
-----------


常见问题
~~~~~~~~~

Warning[Pa082]: undefined behavior: the order of volatile accesses is undefined in this statement

``运算符两边都是volatile变量的警告``

报警的这条语句中有两个或两个以上被 volatile 定义过的变量。编译器会认为有问题。
用volatile修饰的变量一般不直接参与运算，volatile就以为着这个变量在运算过程中有可能已经改变了


Error[e16]: Segment ISTACK (size: 0xc0 align: 0) is too long for segment definition. At least 0xe more bytes needed. The problem occurred while processing the segment placement command

解决：依次打开Project -> Options -> General Option -> Target，在Target标签中找到“Number of virtual”，原来默认为16，修改为8。

