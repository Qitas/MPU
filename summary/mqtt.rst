
.. _mqtt:

MQTT
===============

.. contents::
    :local:

EMQ
-----------

EMQ对客户端链接使用链接进程(emqtt_client)和session进程(emqtt_session)分开的策略。 当一个mqtt的客户端连接到EMQ的服务器上的时候，首先会建立一个负责管理连接的进程(emqtt_client)，当验证客户端有效后会建立另一个进程(emqtt_session)，负责该客户端的会话。

在EMQ中，每一个clientID只能登录一次，因此后登录的客户端会将先登录的客户端踢下线。

主要内存消耗（一个connection大约占10K内存）

数据表
当一个客户端成功完成了验证，EMQ会在mqtt_session中添加一个表项目，同时会在mqtt_local_session和mqtt_client这两张ets表中添加表项目。

进程上下文
链接进程(emqtt_client)负责接收客户端发来的数据和接受服务器内部要发送给客户端的数据，并使用编解码器进行编解码，因此链接进程的上下文消耗，主要取决接收到的数据包大小和将要发送的数据包大小和数量。

session进程(emqtt_session)会保持一个inflight队列，用来对QoS大于0的消息进行应答等待，默认会保存32个消息在等待应答，如果超过这个量级就会放入等待队列。因此session进程(emqtt_session)的主要内存消耗，取决于多少等待应答的消息，以及这些需要应答消息的数据包的大小。

主要CPU消耗

定时器
链接进程(emqtt_client)，默认会启动一个心跳定时器，定期的检查链接是否存活。session进程(emqtt_session)同样会开启一个重新发送定时器，用来检查QoS大于0的消息的infligt响应，当客户端发布QoS为2的消息时还会开启另外一个定时器，用来检测REPL信息的响应，当然session进程(emqtt_session)有可能会在客户端离线后保持一段时间，因此在这段时间会建立一个超时退出的定时器。因此session进程(emqtt_session)在某一个时刻会同时存在三个定时器。

监控
session进程(emqtt_session)为了发现链接进程的退出，会建立一个针对链接进程的监控。而在客户端上线成功后后在向mqtt_local_session和mqtt_client这两张ets表中添加项目的时候，会分别建立两个监控，用来监控session进程(emqtt_session)和链接进程(emqtt_client)的退出。

进程消息
因为EMQ使用了链接进程(emqtt_client)和session进程(emqtt_session)分开的策略，因此产生进程消息传递是无法避免的。因为session进程(emqtt_session)会负责接收服务器发送给客户端的消息，并进行预先处理，处理完之后再交付给链接进(emqtt_client)程进行发送。

当使用持久化session的时候，session进程(emqtt_session)的查找和恢复时也会产生大量的进程消息。

总结
从上面的介绍中，可以看出，在部署一个EMQ服务器前需要考虑，一个客户端平均消息的量级，QoS占比和数据包大小，同时根据有多少客户端进行CPU频率和数量的选择（参考Actor模型中的调度部分）。
