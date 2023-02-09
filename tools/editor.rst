.. _editor:

Editor
==============

.. toctree::
    :maxdepth: 1

    VSCode <vscode>
    Source Insight <si>

.. _markdown:

Markdown
------------

Markdown是一种轻量级标记语言，创始人为约翰·格鲁伯（John Gruber）。


UTF-8
~~~~~~~~~~~~


UTF-8（8-bit Unicode Transformation Format）是一种针对Unicode的可变长度字符编码，又称万国码，由Ken Thompson于1992年创建。现在已经标准化为RFC 3629。UTF-8用1到6个字节编码Unicode字符。用在网页上可以统一页面显示中文简体繁体及其它语言（如英文，日文，韩文）。

事实证明，对可以用ASCII表示的字符使用UNICODE并不高效，因为UNICODE比ASCII占用大一倍的空间，而对ASCII来说高字节的0对他毫无用处。为了解决这个问题，就出现了一些中间格式的字符集，他们被称为通用转换格式，即UTF（Unicode Transformation Format）。常见的UTF格式有：UTF-7, UTF-7.5, UTF-8,UTF-16, 以及 UTF-32。

如果UNICODE字符由2个字节表示，则编码成UTF-8很可能需要3个字节。而如果UNICODE字符由4个字节表示，则编码成UTF-8可能需要6个字节。用4个或6个字节去编码一个UNICODE字符可能太多了，但很少会遇到那样的UNICODE字符。
UTF-8编码规则：如果只有一个字节则其最高二进制位为0；如果是多字节，其第一个字节从最高位开始，连续的二进制位值为1的个数决定了其编码的字节数，其余各字节均以10开头。

* 优点：UTF-8编码可以通过屏蔽位和移位操作快速读写。字符串比较时strcmp()和wcscmp()的返回结果相同，因此使排序变得更加容易。字节FF和FE在UTF-8编码中永远不会出现，因此他们可以用来表明UTF-16或UTF-32文本（见BOM） UTF-8 是字节顺序无关的。它的字节顺序在所有系统中都是一样的，因此它实际上并不需要BOM。
* 缺点：你无法从UNICODE字符数判断出UTF-8文本的字节数，因为UTF-8是一种变长编码它需要用2个字节编码那些用扩展ASCII字符集只需1个字节的字符 ISO Latin-1 是UNICODE的子集，但不是UTF-8的子集 8位字符的UTF-8编码会被email网关过滤，因为internet信息最初设计为7位ASCII码。因此产生了UTF-7编码。 UTF-8 在它的表示中使用值100xxxxx的几率超过50%， 而现存的实现如ISO 2022， 4873， 6429， 和8859系统，会把它错认为是C1 控制码。因此产生了UTF-7.5编码。


