从[官网](http://www.apache.org/dyn/closer.cgi/zookeeper/)直接下载Zookeeper最新版本\(Zookeeper支持Windows和Linux\)

> \[root@localhost app\]\# ll
> 
> -rw-------. 1 root root 22724574 Sep 6 23:02 zookeeper-3.4.9.tar.gz

一、Linux安装Zookeeper

> \[root@localhost app\]\# tar xf zookeeper-3.4.9.tar.gz
> 
> \[root@localhost app\]\# ln -s zookeeper-3.4.9 zookeeper
> 
> \[root@localhost app\]\# cd zookeeper
> 
> 提供配置文件
> 
> \[root@localhost zookeeper\]\# cp conf\/zoo\_sample.cfg conf\/zoo.cfg

启动Zookeeper服务

> \[root@localhost zookeeper\]\# bin\/zkServer.sh start
> 
> ZooKeeper JMX enabled by default
> 
> Using config: \/app\/zookeeper\/bin\/..\/conf\/zoo.cfg
> 
> Starting zookeeper ... STARTED

查看端口监听

> \[root@localhost zookeeper\]\# netstat -tplan \| grep 2181
> 
> tcp6 0 0 :::2181 :::\* LISTEN 3180\/java

![](/assets/zookeeper03.png)

使用Zookeeper的客户端测试

![](/assets/zookeeper04.png)

二、Windows安装Zookeeper

使用上面下载的Zookeeper文件

1.下载并解压，解压后如下

![](/assets/zookeeper01.png)

2.提供配置文件

将conf目录下的zoo\_sample.conf重命名为zoo.conf

3.到bin目录下，双击zkServer.bat即可

![](/assets/zookeeper02.png)

