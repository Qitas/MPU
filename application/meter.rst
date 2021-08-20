.. |SOCHOME| replace:: **www.soc.xin**

.. _meter:

仪器仪表
===============

|SOCHOME| 收集整理了常用的MCU产品开发资源:

.. contents::
    :local:

SCPI
-----------

可编程仪器标准命令（Standard Commands for Programmable Instruments）定义了一套用于控制可编程测试测量仪器的标准语法和命令。

SCPI于1990与IEEE 488.2协议一起面世。这套标准定义了可用于控制一切仪器的语法，命令结构以及数据格式。比如，通用的命令，如配置仪器参数的命令CONFigure，测量命令MEASure等。这些命令可用于任一仪器，并且同一类的命令属于同一子系统里。SCPI同时也定义了若干仪器的种类。比如，任何可控制的电源都会实现DCPSUPPLY基本功能类型。仪器的类别规定了它们会去实现什么样的子系统，当然也包括针对仪器的特定功能。
