.. _ide:

Keil
===========

.. contents::
    :local:

优化等级
-----------

-O0
最少的优化，可以最大程度上配合产生代码调试信息，可以在任何代码行打断点，特别是死代码处。

-O1
有限的优化，去除无用的inline和无用的static函数、死代码消除等，在影响到调试信息的地方均不进行优化。在适当的代码体积和充分的调试之间平衡，代码编写阶段最常用的优化等级。

-O2
高度优化，调试信息不友好，有可能会修改代码和函数调用执行流程，自动对函数进行内联等。

-O3
最大程度优化，产生极少量的调试信息。会进行更多代码优化，例如循环展开，更激进的函数内联等。

另外，可以通过单独设置 --loop_optimization_level=option 来控制循环展开的优化等级。


编程算法FLM
------------

MDK在下载程序之前需要都在Debug设置的Flash Download子选项卡选择编程算法。大多数时候，我们只要安装了芯片包之后，就可以直接得到对应的编程算法，并不需要我们去修改它。

但是，当你是一个芯片包的开发者，或者你有独特的下载需求（比如在你的程序里加入一些校验信息），这个时候你就需要去了解它了！

编程算法主要功能就是擦除相应的内存块，并将我们的程序写入到相应的内存区域上去。在你点击下载按钮的时候，这段程序会被先下载到RAM上（RAM for Algorithm上的设置），然后才会通过它，将你的程序写入到指定的内存区域内。


格式输出
-----------

使用fromelf工具,通过上面的示例,想必都能很轻松的生成bin文件,今天补写一下fromelf工具的基本命令:

    --bin:输出二进制文件
    --i32:Intel 32位Hex
    --m32：Motorola 32位Hex
    --output <file>:file为输出文件名
    -o<file>:这个是armcc编译器命令,也可用于这里,指定输出文件的名字

fromelf --bin "$L@L.axf" --output "$L@L.bin"

勾选了“use cross-module optimization//跨模块优化，KEIL每次都要编译全部文件并且每个文件编译三次


常见问题
-----------

MDK偶尔会出现错误提示“Error: Encountered an improper argument”。大概意思是说“错误：遇到不正确的参数”。
出现这种情况时，对话框关掉之后会再次出现，只能使用任务管理器强制停止才行。在官网上查一下这个错误信息，原来是Keil软件的BUG。

在某些情况下，当您退出调试会话时，可能会显示一个错误对话框，提示“遇到不正确的参数”。 如果发生这种情况，μVision需要使用Windows任务管理器终止。
在大多数情况下，亚洲使用Windows操作系统的客户在项目路径中使用亚洲字符时会受到此问题的影响。
很有可能你的工程路径中有中文（不过之前Keil是支持的），将路径变成中文就可以的了。


WARNING L2: REFERENCE MADE TO UNRESOLVED EXTERNAL

如果你在用C51编译器出现上面的警告，这个只是初学者和粗心者才会犯的错误：没把C文件添加到项目中！
另外，还有可能是因为存在没有被调用的已经定义的函数，或者相关的已经定义的变量没有使用。

WARNING L15: MULTIPLE CALL TO SEGMENT

该警告表示连接器发现有一个函数可能会被主函数和一个中断服务程序(或者调用中断服务程序的函数)同时调用，或者同时被多个中断服务程序调用。

出现这种警告的原因一般有两种：

* 第一：这个函数是不可重入函数，当该函数运行时可能被打断，打断后该函数又被再次运行，从而造成函数内部数据丢失；
* 第二：该函数的内部变量数据所占有的内存在link时被连接器认为是可覆盖的，因此在连接时进行了数据覆盖优化，但是连接器同时发现该函数在运行时被打断后，其他函数（如中断服务子程序）的运行造成了该函数的数据被覆盖。

WARNING L16: UNCALLED SEGMENT, IGNORED FOR OVERLAY PROCESS

定义的函数没有调用而已


IAR
===========

IAR STM8
-----------

extern volatile BYTE sppRxStatus;
extern volatile BYTE sppTxStatus;
__no_init SPP_RX_STRUCT rxData @ "PM0_XDATA";
__no_init SPP_TX_STRUCT txData @ "PM0_XDATA";
_no_init在编程环境中是蓝色的字。

@是指定地址，__no_init 是一个SEGMENT，是给LINKER用的，定义到不初始化的块中去。
@就是指定地址，这个应该没什么好说的了，大部分编译器都这么用。你应该理解这个吧。
你定义全局变量的时候比如int char;  即使你没有赋值给他，编译器还是会给他一个初始化值0，编译的时候编译器把他分配到初始化为零的那个SEGMENG中去了。编译器默认的有几个块，初始化为零的块，初始化不为零的块，和不初始化的块，你可以定义自己的块，如你的PM0_XDATA，这个就是你自己定义的一个块，那你的这个块是个什么属性呢，就是，__no_init 属性，有了这个属性，编译器只给你分配空间，不给你初始化。


IAR 8051
-----------
Error[e16]: Segment ISTACK (size: 0xc0 align: 0) is too long for segment definition. At least 0xe more bytes needed. The problem occurred while processing the segment placement command

解决：依次打开Project -> Options -> General Option -> Target，在Target标签中找到“Number of virtual”，原来默认为16，修改为8。

常见问题
-----------

Warning[Pa082]: undefined behavior: the order of volatile accesses is undefined in this statement

``运算符两边都是volatile变量的警告``

报警的这条语句中有两个或两个以上被 volatile 定义过的变量。编译器会认为有问题。
用volatile修饰的变量一般不直接参与运算，volatile就以为着这个变量在运算过程中有可能已经改变了



Keil vs IAR
=============

Keil MDK-ARM（旧称RealView MDK）开发工具源自德国Keil公司，被全球上百万的嵌入式开发工程师验证和使用，是ARM公司目前最新推出的针对各种嵌入式处理器的软件开发工具。

KEIL MDK集成了业内最领先的技术，包括uVision3、uVision4、uVision5集成开发环境与 ARM编译器。支持ARM7、ARM9、Cortex-M0、Cortex-M0+、Cortex-M3、Cortex-M4、Cortex-R4内核核处理器。

Keil MDK可以自动配置启动代码，集成Flash烧写模块，强大的Simulation设备模拟，性能分析等功能，与ARM之前的工具包ADS等相比，ARM编译器的最新版本可将性能改善超过20％以上。
　　
IAR Embedded Workbench是一套用于编译和调试嵌入式系统应用程序的开发工具，支持汇编、C和C++语言。它提供完整的集成开发环境，包括工程管理器、编辑器、编译链接工具和C-SPY调试器。

IAR Systems以其高度优化的编译器而闻名。每个C/C++编译器不仅包含一般全局性的优化，也包含针对特定芯片的低级优化，以充分利用您所选芯片的所有特性，确保较小的代码尺寸。IAR Embedded Workbench能够支持由不同的芯片制造商生产，且种类繁多的8位、16位或32位芯片。



主要区别
-----------

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
