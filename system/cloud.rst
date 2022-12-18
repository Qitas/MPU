
.. _cloud:

云平台
===============

.. contents::
    :local:
    :depth: 1

阿里云
-----------


华为云
-----------


私有云
-----------

运维监控: 当项目的业务越来越庞大，人为去运维服务器已经是不可能了，需要把运维尽量自动化，部署open-falcon、Zabbix等运维监控系统，监控服务器网络、系统、服务等状态，出现问题及时报警，通知运维管理员，管理员接到通知尽快解决问题，保证服务器业务的正常运营。

文件监控: 使用inotify、FileMonitor等开源文件监控系统，监听系统中重要的敏感文件，常见的用户、密码、权限、主机系统、网络配置、服务程序配置等文件：passwd、shadow、group、hosts等。同样，可以使用shell脚本来完成。

进程监控: 使用monit、supervisord等开源进程监控系统，监听Web等服务进程是正常运行，也可以使用脚本周期性查看进程是否正在运行。

日志监控: 使用log_monitor 、Log Watcher等开源日志监控系统，监听Web服务等日志信息，对高频IP进行报警。如果，日志监控系统不存在自定义的功能需求，可以使用脚本来完成，获取我们关心的日志信息。

漏洞扫描: 使用openvas、nessus等漏洞扫描系统，定期更新漏洞库与扫描插件，也定期扫描服务器所在的网络，及时发现网络上的脆弱点以及服务器等主机存在的漏洞，修复暴露出来的问题，避免漏洞被入侵者利用，入侵网络系统。

防火墙: 在服务器上或者在网关上配置防护墙，控制网络流量，过滤掉不必要的网络数据报文，之允许服务器上服务相关的流量通过。这里，把ping流量禁止掉，可以隐藏一些操作系统类型信息。当然，把防火墙部署在单独的网关上面，可以减轻服务器的负担，服务器可以使用全部资源支持当前运营的服务。

入侵防御: 把snort系统配置成入侵防御的模式，系统直连在服务器的网络路线上，充当服务器的安全网关，抵御网络攻击。当然，这样会对服务器的网络性能产生影响。

入侵检测: 安装snort轻量级入侵检测系统，部署在网络的旁路，既可以监听流过的网络流量是否存在入侵攻击，也不会影响服务器的网络性能。


常用系统命令
~~~~~~~~~~~~~~~

Vmstat、sar、iostat、netstat、free、ps、top


利用sar命令监控系统CPU

sar对系统每方面进行单独统计，但会增加系统开销，不过开销可以评估，对系统的统计结果不会有很大影响。
下面是sar命令对某个系统的CPU统计输出：

[root@webserver ~]# sar -u 3 5

输出解释如下：

* %user列显示了用户进程消耗的CPU 时间百分比。
* %nice列显示了运行正常进程所消耗的CPU 时间百分比。
* %system列显示了系统进程消耗的CPU时间百分比。
* %iowait列显示了IO等待所占用的CPU时间百分比
* %steal列显示了在内存相对紧张的环境下pagein强制对不同的页面进行的steal操作 。
* %idle列显示了CPU处在空闲状态的时间百分比。


systemctl是CentOS7的服务管理工具中主要的工具，它融合之前service和chkconfig的功能于一体。

chkconfig
~~~~~~~~~~~

chkconfig [--add][--del][--list][系统服务] 或 chkconfig [--level <levels等级代号>][系统服务][on/off/reset]

使用范例：

chkconfig --list        #列出所有的系统服务
chkconfig --add httpd        #增加httpd服务
chkconfig --del httpd        #删除httpd服务
chkconfig --level  2345  httpd  on        #设置httpd在运行级别为2、3、4、5的情况下都是on（开启）的状态
chkconfig --list        #列出系统所有的服务启动情况
chkconfig --list mysqld        #列出mysqld服务设置情况
chkconfig --level 35 mysqld on        #设定mysqld在等级3和5为开机运行服务，--level 35表示操作只在等级3和5执行，on表示启动，off表示关闭
chkconfig mysqld on        #设定mysqld在各等级为on，“各等级”包括2、3、4、5等级
