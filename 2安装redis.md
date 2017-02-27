一、Linux系统安装Redis

[官网](http://redis.io/)下载Redis包，这里下载的是3.2.3版本

1、编译安装Redis

> [root@localhost ~]# mkdir /app
> 
> [root@localhost ~]# cd /app
> 
> [root@localhost ~]# wget http://download.redis.io/releases/redis-3.2.3.tar.gz
> 
> 解压压缩包
> 
> [root@localhost ~]# tar xf redis-3.2.3.tar.gz
> 
> [root@localhost ~]# cd redis-3.2.3
> 
> 编译Redis
> 
> [root@localhost redis-3.2.3]# make
> 
> 安装Redis
> 
> [root@localhost redis-3.2.3]# make install
> 
> cd src && make install
> 
> make[1]: Entering directory `/app/redis-3.2.3/src'
> 
> Hint: It's a good idea to run 'make test' ;)
> 
> INSTALL install
> 
> INSTALL install
> 
> INSTALL install
> 
> INSTALL install
> 
> INSTALL install
> 
> make[1]: Leaving directory `/app/redis-3.2.3/src'

2、提供配置文件和基础数据目录（我这里将Redis执行文件复制到专门的目录）

> [root@localhost redis-3.2.3]# mkdir -pv /app/redis/{bin,conf,log,db}
> 
> mkdir: created directory ‘/app/redis’
> 
> mkdir: created directory ‘/app/redis/bin’
> 
> mkdir: created directory ‘/app/redis/conf’
> 
> mkdir: created directory ‘/app/redis/log’
> 
> mkdir: created directory ‘/app/redis/db’
> 
> [root@localhost redis-3.2.3]# cd src
> 
> 复制需要的二进制文件
> 
> [root@localhost src]# cp redis-benchmark redis-check-aof redis-check-rdb redis-cli redis-sentinel redis-server /app/redis/bin/
> 
> [root@localhost src]# cd /app/redis
> 
> 提供启动配置文件
> 
> [root@localhost redis]# vim conf/redis.conf
> 
> **daemonize yes**
> 
> **protected-mode no**
> 
> pidfile /var/run/redis.pid
> 
> port 6379
> 
> timeout 0
> 
> tcp-keepalive 0
> 
> databases 16
> 
> save 900 1
> 
> save 300 10
> 
> save 60 10000
> 
> stop-writes-on-bgsave-error yes
> 
> rdbcompression yes
> 
> rdbchecksum yes
> 
> dir /app/redis/db
> 
> dbfilename dump-6379.rdb
> 
> loglevel notice
> 
> logfile /app/redis/log/redis.log
> 
> slave-serve-stale-data yes
> 
> slave-read-only yes
> 
> repl-disable-tcp-nodelay no
> 
> slave-priority 100
> 
> appendonly no
> 
> appendfsync everysec
> 
> no-appendfsync-on-rewrite no
> 
> auto-aof-rewrite-percentage 100
> 
> auto-aof-rewrite-min-size 64mb
> 
> lua-time-limit 5000
> 
> slowlog-log-slower-than 10000
> 
> slowlog-max-len 128
> 
> hash-max-ziplist-entries 512
> 
> hash-max-ziplist-value 64
> 
> list-max-ziplist-entries 512
> 
> list-max-ziplist-value 64
> 
> set-max-intset-entries 512
> 
> zset-max-ziplist-entries 128
> 
> zset-max-ziplist-value 64
> 
> activerehashing yes
> 
> client-output-buffer-limit normal 0 0 0
> 
> client-output-buffer-limit slave 256mb 64mb 60
> 
> client-output-buffer-limit pubsub 32mb 8mb 60
> 
> hz 10
> 
> aof-rewrite-incremental-fsync yes

3.启动Redis服务

> [root@localhost redis]# /app/redis/bin/redis-server /app/redis/conf/redis.conf
> 
> 查看是否启动Redis服务，并监听指定端口
> 
> ![](/assets/redis03.png)
> 
> 这里可以看到，默认的6379已经处于监听状态

4.测试Redis

![](/assets/redis04.png)

5.查看Redis日志

> [root@localhost redis]# tailf /app/redis/log/redis.log

二、Windows安装Redis

下载地址[Github](https://github.com/MSOpenTech/redis/releases)，这里redis-64.3.0.503版本

1.下载并解压，解压后如下

![](/assets/redis01.png)

2.使用cmd进入到Redis解压目录中，并使用脚本(redis-server.exe  redis.windows.conf)执行即可，默认配置文件不需要修改

![](/assets/redis02.png)

