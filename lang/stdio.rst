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


.. code-block:: bash

    double x = 218.82631;
    printf("%-6.2e\n", x);


%：表示格式说明的起始符号，也是转义符号，有一题 printf（“%%%%”）输出几个？答案输出%% 两个
-：有-表示左对齐输出，如省略表示右对齐输出
0：有0表示指定空位填0,如省略表示指定空位不填

.. code-block:: bash

    m.n
    m指域宽，即对应的输出项在输出设备上所占的字符数。
    n指精度，用于说明输出的实型数的小数位数，没有指定n时，隐含的精度为n=6位。
    e格式表示以指数形式输出实数

** 以左对齐、指数形式、总长度m =6、小数n=2两位 输出 **


数学运算
-----------

c中的函数申明为 int abs(int num);

正常情况下,num为0或正数时，函数返回num值；
当num为负数且不是最小的负数时（不要问我最小的int类型负数是多少，上面那个图里面有真相），函数返回num的对应绝对值数，即将内存中该二进制位的符号位取反，并把后面数值位取反加一；
当num为最小的负数时（即0x80000000），由于正数里int类型32位表示不了这个数的绝对值，所以依然返回该负数。
