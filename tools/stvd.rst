.. _stvd:

STVD
===========

.. contents::
    :local:

简介
-------------

相关问题
-------------

用STVD+COSMIC编译工程时出现以下错误（加载的别人的工程）：
#error clnk Debug\demo.lkf:47 can't openfile crtsi0.sm8
#error clnk Debug\demo.lkf:60 can't openfile libis0.sm8
#error clnk Debug\demo.lkf:61 can't openfile libm0.sm8

解决方法：

打开STVD软件，选择Tools-> Options -> Directories -> Show Directories for选择:Libraryfiles 将D:\program files\COSMIC\CXSTM8_32K\Lib添加进去，如安装在其它目录，添加相应的目录即可。


关于启动STVD编译环境，启动编译连接出现错误Error creating process for executable cxstm8 系统找不到指定的文件解决方法

第一步：先点击截图里面的第一个文件来安装，安装过程中，会有很多的提示，直接NEXT，可以。

第二步：点击第二个文件，找到刚才cxstm8_32k.exe。安装路径。点击启动应用按钮，即完成安装。

再来启动STVD软件，点击project项目中的settings.如下截图所示：在project specific toolset p:左侧打上小勾勾，然后单击找到刚才按照CXSTM8_32K的安装路径，即可。
