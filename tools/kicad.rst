.. _kicad:

KiCad
===========

.. contents::
    :local:

KiCad简介
-------------

KiCad于1992年由Jean-Pierre Charras在IUT de Grenoble工作时创建。2013年，CERN BE-CO-HT部门开始为KiCad提供资源，帮助促进KiCad与商用EDA工具相媲美。

是一款十分流行且强大的基于GPL的开源EDA，主要包括一个工程管理器和四个主要程序

* kicad - 工程管理器
* eeschema - 原理图编辑器
* cvpcb - 元件封装关联选择器
* pcbnew - PCB布线程序
* gerbview - Gerber(光绘文件)查看器

KiCad优点
~~~~~~~~~~~~~~~~~

* GPL开源软件，同时维护有大量开源资源
* 图形操作界面，鼠标和键盘操作很方便，支持脚本
* 相应功能全面，完全能够满足常规PCB的设计需求
* 跨平台的工具，linux、mac、windows都可以使用
* 可以直接生成gerber文件输出，不用担心文件格式
* 软件不大，对电脑的配置要求不高
* 学习入门的门槛低，相关资料丰富
* 快捷键和热键强大，操作很人性化


pcbnew层描述
-------------

Pcbnew的层描述中F.代表电路板上层（Front），B.代表电路板的下层（Back）

铜层是用于放置和重新布置导线的工作层。 层号从0开始（第一个铜层，在上层，即F.Cu），并以31（最后一个铜层，在下层，即B.Cu）结束。 由于元件不能放置在内层（层1到层30）中，所以只有层0（F.Cu）和层31（B.Cu）是元件层。

任何铜层的名字都是可以编辑的。层0的默认名称为F.Cu，层31的默认名称为B.Cu。当电路板是2层板时，层0和层31之间没有其他的铜层。当电路板是4层板时，层0和层31中间多了两个铜层，名称按从上层到下层的顺序依次为 In1.Cu 和 In2.Cu。当电路板是6层板时，层0和层31中间多了四个铜层，名称按从上层到下层的顺序依次为 In1.Cu，In2.Cu，In3.Cu 和 In4.Cu。

Adhesive (F.Adhes and B.Adhes)粘合层：用于在波峰焊前将SMD元件的粘合剂粘贴到电路板上的粘合层。

Solder Paste (F.Paste and B.Paste)焊膏层：在回流焊接之前生产掩模以允许焊膏放置在SMD元件的焊盘上。

Silk Screen (F.SilkS and B.SilkS)丝印层：元件图样标识的层，用于辅助元件的安装。

Solder Mask (F.Mask and B.Mask)阻焊层：定义了焊接的掩模，也就是不过绿油的区域。

Courtyard (F.CrtYd and B.CrtYd)空间层：用于显示元件在PCB上实际占用的空间大小。

Fabrication (F.Fab and B.Fab)生产层：用于辅助元件贴装。

Edge.Cuts边界层：用于绘制电路板轮廓（在此层上的任何元素（图形、文本…）都显示在所有其他图层上）。


pcbnew提供了至多50个层供电路板设计师使用：

* 32个铜层供导线走线（可覆铜）
* 14个固定用途技术层
* 12个技术层对（上技术层和下技术层对称）: Adhesive, Solder Paste, Silk Screen, Solder Mask, Courtyard, Fabrication共计6对。
* 2个独立技术层：Edge Cuts, Margin
* 4个辅助层可以任意使用：Comments, E.C.O. 1, E.C.O. 2, Drawings
