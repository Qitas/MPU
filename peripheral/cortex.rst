.. _cortex_m0:

Cortex M0
===============

.. contents::
    :local:

STM32F0
-----------

F0属于M0内核，不同于M0+、M3和M4等内核，没有专门的中断向量控制寄存器，中断向量的设置只能采用拷贝到SRAM方式。具体实现方式——定义一个位于SRAM首地址全局数组变量，将M0的所有中断入口地址拷贝到该变量内，再将SRAM的地址映射到地址0x00000000，发生中断后，MCU自动从地址0x00000000对应的偏移处寻找中断入口，如下：

///// 定义全局数组以存储中断向量表，M0共48个
#if (defined (__CC_ARM) ) //// for keil MDK compiler
__IO uint32_t VectorTable[48] __attribute__((at(0x20000000)));
#elif (defined (__ICCARM__) ) //// for IAR compiler
#pragma location=0x20000000
__no_init __IO uint32_t VectorTable[48];
#elif (defined ( __GNUC__) ) //// for GNU compiler
__IO uint32_t VectorTable[48] attribute__((section(".RAMVectorTable")));
#elif (defined ( __TASKING__) ) //// for TASKING compiler
__IO uint32_t VectorTable[48] at(0x20000000);
#endif


备份域使用
-----------

在实际产品中使用时，发现备份SRAM中的数据丢失！检查在硬件上并没有出现任何问题，于是从软件一步步分析如下：

产品中实现了IAP、APP在线升级，备份域在这两部程序中均有使用（两部分程序中均对备份域进行了初始化）。
在由IAP跳转到APP后，发现初始化的备份SRAM中原有数据全部丢失
检查发现，STM32芯片在上电后默认以内部低速时钟源（HSI运行），如果用户配置了使用外部时钟源，则再配置外部时钟源，然后将时钟切换为外部。程序在APP中配置时钟前是正常的，一旦时钟源出现切换则导致备份域再次初始化之后就无效了！

在IAP跳转到APP前，将备份域的各时钟失能，这样APP中配置的备份SRAM才会有效。至于具体原因暂时未知！
