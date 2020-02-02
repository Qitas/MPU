# [docker](https://github.com/Qitas/docker)

## 运行

docker run ：创建一个新的容器并运行一个命令

### 示例 

docker run --name mysql_db -e MYSQL_ROOT_PASSWORD=123456 -d mysql

创建mysql容器并后台运行，指定数据库密码是123456。-e指定环境变量。

docker run --name some-wordpress  --link mysql_db:mysql -p 8001:80 -d daocloud.io/daocloud/dao-wordpress

### OPTIONS说明：

-a stdin: 指定标准输入输出内容类型，可选 STDIN/STDOUT/STDERR 三项；

-d: 后台运行容器，并返回容器ID；

-i: 以交互模式运行容器，通常与 -t 同时使用；

-t: 为容器重新分配一个伪输入终端，通常与 -i 同时使用；

--name="nginx-lb": 为容器指定一个名称；

--dns 8.8.8.8: 指定容器使用的DNS服务器，默认和宿主一致；

--dns-search example.com: 指定容器DNS搜索域名，默认和宿主一致；

-h "mars": 指定容器的hostname；

-e username="ritchie": 设置环境变量；

--env-file=[]: 从指定文件读入环境变量；

--cpuset="0-2" or --cpuset="0,1,2": 绑定容器到指定CPU运行；

-m :设置容器使用内存最大值；

--net="bridge": 指定容器的网络连接类型，支持 bridge/host/none/container: 四种类型；

--link=[]: 添加链接到另一个容器；

--expose=[]: 开放一个端口或一组端口；


## 其他

history   Show the history of an image
              --显示镜像制作的过程，相当于dockfile

save      Save an image(s) to a tar archive
              --将镜像打包，与上面的load命令相对应
              譬如：
              docker save -o nginx.tar nginx

load      Load an image from a tar archive or STDIN
              --与save命令相对应，将sava命令打包的镜像通过load命令导入

tag       Tag an image into a repository
              --对镜像进行重命名

top       Display the running processes of a container
              --查看容器中正在运行的进程

unpause   Unpause all processes within a container
              --恢复容器内暂停的进程，与pause参数相对应

wait      Block until a container stops, then print its exit code
              --捕捉容器停止时的退出码
              执行此命令后，该命令会“hang”在当前终端，直到容器停止，此时，会打印出容器的退出码