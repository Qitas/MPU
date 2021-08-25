.. _gcc:

GCC
===========

.. contents::
    :local:

简介
-------------
GCC(GNU Compiler Collection) 是由GNU开发的编程语言译器。GNU编译器套件包括C、C++、 Objective-C、 Fortran、Java、Ada和Go语言前端，也包括了这些语言的库（如libstdc++，libgcj等。）

gcc 与 g++ 分别是 gnu 的 c & c++ 编译器 gcc/g++ 在执行编译工作的时候，总共需要4步：

1、预处理,生成 .i 的文件[预处理器cpp]
2、将预处理后的文件转换成汇编语言, 生成文件 .s [编译器egcs]
3、有汇编变为目标代码(机器代码)生成 .o 的文件[汇编器as]
4、连接目标代码, 生成可执行程序 [链接器ld]


arm-elf-gcc 跟 arm-linux-gcc 一样，也是是基于 ARM 目标机的交叉编译软件。但是它们不是同一个交叉编译软件，两者是有区别的，两者区别主要在于使用不同的 C 库文件。arm-linux-gcc使用 GNU 的 Glibc，而 arm-elf-gcc 一般使用 uClibc/uC-libc 或者使用 RedHat专门为嵌入式系统的开发的C库newlib。只是所应用的领域不同而已，Glibc是针对PC开发的，uClibc/uC-libc是与Glibc API兼容的小型化C语言库，实现了Glibc部分功能。

uC -libc是最早为uClinux开发的库，是Jeff Dionne和Kenneth Albanowski为在EKLs项目中支持m68000在Linux-8086 C库源码上移植的。uC-libc是一个完全的libc实现，但其中有一些api是非标准的，有些libc的标准也没有实现。uC-libc稳定地支持 m68000，ColdFire和没有MMU的ARM。其主要设计目标是“小”、“轻”，并尽量与标准一致，虽然它的API和很多libc兼容，但是似乎并不像它期望的那样和所有标准一致。

uClibc就是为了解决这个问题从uC-libc中发展出来的。它的所有API都是标准的(正确的返回类型，参数等等)，它弥补了uC-libc中没有实现的libc标准，现在已经被移植到多种架构中。一般来讲，它尽量兼容glibc以便使应用程序用uClibc改写变的容易。uClibc能够在标准的 VM linux和uClinux上面使用。为了应用程序的简洁，它甚至可以在许多支持MMU的平台上被编译成共享库。

arm-linux-*和 arm-elf-*的使用没有一个绝对的标准，排除不同库实现的差异，gcc可以编译任何系统。arm-linux-*和 arm-elf-*都可以用来编译裸机程序和操作系统，只是在遵循下面的描述时系统程序显得更加协调：

arm-linux-*针对运行linux的ARM机器，其依赖于指定的C语言库Glibc，因为同样使用Glibc的linux而使得arm-linux-*在运行linux的ARM机器上编译显得更加和谐。

arm-elf-*则是一个独立的编译体系，不依赖于指定的C语言库Glibc，可以使用newlib等其他C语言库，不要求操作系统支持，当其使用为嵌入式系统而设计的一些轻巧的C语言库时编译裸机程序(没有linux等大型操作系统的程序)，如监控程序，bootloader等能使得系统程序更加小巧快捷。


对比
-------------

ARM的嵌入式系统开发中，常常用到交叉编译的GCC工具链有两种： arm-linux-*和 arm-elf-*，两者区别主要在于使用不同的C库文件。
arm-linux-*使用GNU的Glibc，而arm-elf-*一般使用 uClibc/uC-libc或者使用REDHAT专门为嵌入式系统的开发的C库newlib.Glibc。
uClibc/uC-libc以及 newlib都是C语言库文件，只是所应用的领域不同而已，Glibc是针对PC开发的，uClibc/uC-libc是与Glibc API兼容的小型化C语言库，实现了Glibc部分功能。


1、EABIarm-2008q3-39-arm-none-eabi
Sourcery G++ Lite 2008q3-39 All versions...
Sourcery G++ for ARM EABI is for use in bare-metal and/or RTOS environments.（适用于编译裸机或RTOS环境上的应用，比如u-boot等）；Run-Time Libraries：ARMv4 - Little-Endian, Soft-Float；ARMv4 Thumb -Little- Endian, Soft-Float；ARMv6-M Thumb - Little-Endian, Soft-Float；ARMv7 Thumb-2 - Little-Endian, Soft-Float。
2、uClinux arm-2008q3-42-arm-uclinuxeabi
Sourcery G++ Lite 2008q3-42 All versions...
Sourcery G++ for ARM uClinux is for systems running the Linux kernel without using a memory-management unit (MMU). You can use Sourcery G++ to build both the uClinux kernel and uClinux applications. ）适用于编译linux内核和应用程序，不带MMU的CPU）；Run-Time Libraries：ARMv4T - Little-Endian, Soft-Float；ARMv6-M Thumb - Little-Endian, Soft-Float；ARMv7 Thumb-2 - Little-Endian, Soft-Float。
3、GNU/Linux arm-2008q3-41-arm-none-linux-gnueabi
Sourcery G++ Lite 2008q3-41 All versions...
Sourcery G++ for ARM GNU/Linux is for use in developing for systems which run the Linux kernel. You can use Sourcery G++ to build both the Linux kernel and Linux applications.（适用于编译linux内核和应用程序，带MMU的CPU）；Run-Time Libraries：ARMv4T - Little-Endian, Soft-Float, GLIBC；ARMv5T - Little-Endian, Soft-Float, GLIBC；ARMv7-A Thumb-2 - Little-Endian, Soft-Float, GLIBC。
4、SymbianOS arm-2008q3-40-arm-none-symbianelf
Sourcery G++ Lite 2008q3-40 All versions...
适用于编译Symbian应用程序；Run-Time Libraries：ARMv5 - Little-Endian, Soft-Float；ARMv5 - Little-Endian, VFP。


arm-linux-gcc是针对arm + Linux的开发环境的，kernel使用的是linux，不是uclinux，arm是有硬件MMU的。

　　而arm-elf-gcc是针对no MMU arm + uclinux的开发环境，kernel使用的是uclinux，硬件是廉价的无MMU的arm芯片。

　　arm-linux-gcc倒是有点类似X86 PC环境下的linux开发。


其实这两个交叉编译器只不过是gcc的选项-mfloat-abi的默认值不同. gcc的选项-mfloat-abi有三种值soft,softfp,hard(其中后两者都要求arm里有fpu浮点运算单元,soft与后两者是兼容的，但softfp和hard两种模式互不兼容)：

soft   : 不用fpu进行浮点计算，即使有fpu浮点运算单元也不用,而是使用软件模式。
softfp : armel架构(对应的编译器为gcc-arm-linux-gnueabi)采用的默认值，用fpu计算，但是传参数用普通寄存器传，这样中断的时候，只需要保存普通寄存器，中断负荷小，但是参数需要转换成浮点的再计算。
hard   : armhf架构(对应的编译器gcc-arm-linux-gnueabihf)采用的默认值，用fpu计算，传参数也用fpu中的浮点寄存器传，省去了转换, 性能最好，但是中断负荷高。


arm-none-linux-gnueabi-gcc
~~~~~~~~~~~~~~~~~~~~~~~~~~~

(ARM architecture, no vendor, creates binaries that run on the Linux operating system, and uses the GNU EABI)

主要用于基于ARM架构的Linux系统，可用于编译 ARM 架构的 u-boot、Linux内核、linux应用等。
arm-none-linux-gnueabi基于GCC，使用Glibc库，经过 Codesourcery 公司优化过推出的编译器。
arm-none-linux-gnueabi-xxx 交叉编译工具的浮点运算非常优秀。一般ARM9、ARM11、Cortex-A 内核，带有 Linux 操作系统的会用到。


arm-eabi-gcc
~~~~~~~~~~~~~~~~~~~~~

Android ARM 编译器。

armcc
~~~~~~~~~~~~~~~~~~~~~

ARM 公司推出的编译工具，功能和 arm-none-eabi 类似，可以编译裸机程序（u-boot、kernel），但是不能编译 Linux 应用程序。
armcc一般和ARM开发工具一起，Keil MDK、ADS、RVDS和DS-5中的编译器都是armcc，所以 armcc 编译器都是收费的。


arm-none-uclinuxeabi
~~~~~~~~~~~~~~~~~~~~~

用于uCLinux，使用Glibc。

arm-none-symbianelf
~~~~~~~~~~~~~~~~~~~~~

用于symbian


ABI vs EABI
~~~~~~~~~~~~~~~~~~

ABI：二进制应用程序接口(Application Binary Interface (ABI) for the ARM Architecture)。在计算机中，应用二进制接口描述了应用程序（或者其他类型）和操作系统之间或其他应用程序的低级接口。

EABI：嵌入式ABI。嵌入式应用二进制接口指定了文件格式、数据类型、寄存器使用、堆积组织优化和在一个嵌入式软件中的参数的标准约定。开发者使用自己的汇编语言也可以使用 EABI 作为与兼容的编译器生成的汇编语言的接口。

两者主要区别是，ABI是计算机上的，EABI是嵌入式平台上（如ARM，MIPS等）。


库链接
-------------

我们用gcc编译程序时，可能会用到“-I”（大写i），“-L”（大写l），“-l”（小写l）等参数，下面做个记录：

例：gcc -o hello hello.c -I /home/hello/include -L /home/hello/lib -lworld

上面这句表示在编译hello.c时：

-I /home/hello/include

表示将/home/hello/include目录作为第一个寻找头文件的目录，寻找的顺序是：

/home/hello/include-->/usr/include-->/usr/local/include


存储访问
-------------

_no_init用于禁止系统启动时的变量初始化，我想知道，什么情况下需要用这个关键字使系统禁止变量的初始化，禁止变量初始化用在什么场合，为什么要这样做，有什么意义吗？
另外__ramfunc也有类似疑问，书上只是说用__ramfunc定义的函数企图访问ROM将导致编译器产生警告，请问什么情况下才需要用__ramfunc
arm-none-eabi-gcc（ARM architecture，no vendor，not target an operating system，complies with the ARM EABI）
用于编译 ARM 架构的裸机系统（包括 ARM Linux 的 boot、kernel，不适用编译 Linux 应用 Application），一般适合 ARM7、Cortex-M 和 Cortex-R 内核的芯片使用，所以不支持那些跟操作系统关系密切的函数，比如fork(2)，他使用的是 newlib 这个专用于嵌入式系统的C库。


SDCC
---------------

.. toctree::
    :maxdepth: 1

    SDCC  <sdcc>

