一、Linux安装Mpush-Alloc

> \[root@localhost app\]\# tar xf alloc-release-0.0.5.tar.gz
> 
> \[root@localhost app\]\# ln -s mpush-alloc-0.0.5 mpush-alloc
> 
> 编辑配置文件\(注意，这里不需要修改，如果分布式部署，修改zookeeper地址信息即可\)。
> 
> \[root@localhost app\]\#vim conf\/mpush.conf
> 
> 给脚本执行权限
> 
> \[root@localhost mpush\]\# chmod +x bin\/\*.sh
> 
> \[root@localhost mpush\]\# bin\/mp.sh start

![](/assets/alloc01.png)

查看日志和启动情况

![](/assets/alloc02.png)

二、Windows安装Mpush-Alloc

1.解压alloc-release-0.0.5.tar.gz

2.修改配置文件\(注意，这里不需要修改，如果分布式部署，修改zookeeper地址信息即可\)。

3.使用cmd进入到alloc的bin目录，使用如下命令启动\(\)

