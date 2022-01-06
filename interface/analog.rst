.. _analog:

模拟外设
===============

.. contents::
    :local:

ADC
-----------

技术分类
~~~~~~~~~~~~~~

.. _sar:

SAR
^^^^^^^^^^^^^

逐次逼近式模拟数字转换器SAR(Successive Approximation Register)，在每一次转换过程中，通过遍历所有的量化值并将其转化为模拟值，将输入信号与其逐一比较，最终得到要输出的数字信号。

逐次逼近模数转换器是采样速率低于5Msps的中高分辨率ADC应用的常见结构，SAR式ADC的分辨率一般为8-16位。具有低功耗，小尺寸等特点。

.. _sigma_delta:

Sigma-Delta
^^^^^^^^^^^^^

.. _pipeline:

Pipeline
^^^^^^^^^^^^^

pipeline 更适合高速中等精度的，如 100M 14bit 以上的应用。

100MHz Conversion Rate 12-bit , :ref:`sar` 就要1.4GHz的Clock，而 Pipelined ADC 只需100MHz的 Clock

随着工艺的进步，:ref:`sar` 和 :ref:`sigma_delta` 的速度也上来 ，Pipeline 正在全面被SAR取代，除了12bit以上且大于200MSPS


Audio ADC
~~~~~~~~~~~~~~~~~~~

`Current Characteristics Recognition <https://github.com/stopstopstop/CCR>`_

Audio ADC相较于普通的ADC器件更注重AC信号，DC信号不准，具有相对固定的频率，都是 :ref:`sigma_delta` 型，本质上是1-bit ADC，有较高的分辨率，高分辨率是依靠滤波器滤去噪声后获得，有很大的噪声。

Audio ADC只关心音频频段，其滤波器响应就是按这个频段优化设计的，对于直流和很低的低频就要差些。而在采样直流信号时sigma-delta恰恰会产生低频杂散（idle tone)。

Audio ADC的采集频率较低，对直流采集有偏差，一般不标明非线性误差的。但是有滤波器，价格比较便宜。

TLV320ADC3140/5140/6140
^^^^^^^^^^^^^^^^^^^^^^^^^^

``120dB``

* 动态范围增强器DRE

DRE整体是一套闭环控制的过程，采样的信号经过DRE分析后由可变增益放大器转化，当信号较小时，相关信号也将反馈于前级电子增益进行调整。

DAC
-----------
