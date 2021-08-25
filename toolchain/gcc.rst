.. _gcc:

GCC
===========

.. contents::
    :local:

简介
-------------

arm-linux-gcc arm-elf-gcc 区别
ARM的嵌入式系统开发中，常常用到交叉编译的GCC工具链有两种： arm-linux-*和 arm-elf-*，两者区别主要在于使用不同的C库文件。arm-linux-*使用
GNU的Glibc，而arm-elf-*一般使用 uClibc/uC-libc或者使用REDHAT专门为嵌入式系统
的开发的C库newlib.Glibc。uClibc/uC-libc以及 newlib都是C语言库文件，只是所应
用的领域不同而已，Glibc是针对PC开发的，uClibc/uC-libc是与Glibc API兼容的小型
化C语言库，实现了Glibc部分功能。


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


存储访问
-------------

_no_init用于禁止系统启动时的变量初始化，我想知道，什么情况下需要用这个关键字使系统禁止变量的初始化，禁止变量初始化用在什么场合，为什么要这样做，有什么意义吗？
另外__ramfunc也有类似疑问，书上只是说用__ramfunc定义的函数企图访问ROM将导致编译器产生警告，请问什么情况下才需要用__ramfunc


SDCC
---------------

.. toctree::
    :maxdepth: 1

    SDCC  <sdcc>

