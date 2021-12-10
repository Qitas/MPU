.. _lan_c_stdio:

标准函数
===============

.. contents::
    :local:


输入输出
-----------

.. code-block:: bash

    #include <stdio.h>

    int main() {
        char ch = -1;
        printf(" %02x, %02x", ch, (unsigned char)ch);
        return (0);
    }

* 输出答案： ffffffff,ff

%x默认输出unsigned int;所以char会被自动扩展至unsigned int;
因此会扩展符号位;而unsigned char扩展至unsigned int;会直接用0填充;
