

| 主机 | IP | 端口 |
| --- | --- | --- |
| Redis | 103.246.161.44 | 6379 |
| ZooKeeper | 103.246.161.44 | 2181 |
| Mpush | 103.246.161.44 | 3000 |
| Alloc | 103.246.161.44 | 9999 |

服务器版本为Centos7，最小化安装。

note：

1）最小化安装，默认网卡没有开机自动启动，可以编辑网卡文件\(默认为ifcfg-eth0\)，将ONBOOT修改为yes

> \[root@localhost ~\]\# vim \/etc\/sysconfig\/network-scripts\/ifcfg-eth0
> 
> **ONBOOT=yes**

2）安装系统基本依赖包，用于编译安装软件

> \[root@localhost ~\]\# yum install net-tools vim wget make gcc g++ gc++ -y

3）关闭防火墙和SELinux，防止系统干扰导致部署不成功

> \[root@localhost ~\]\# setenforce 0
> 
> \[root@localhost ~\]\# iptables -F
> 
> \[root@localhost ~\]\# iptables -X



安装JDK

> \[root@localhost app\]\# ll
> 
> -rw-------. 1 root root 181352138 Sep 6 22:54 jdk-8u101-linux-x64.tar.gz

1、安装JDK并设置环境变量

> \[root@localhost app\]\# tar xf jdk-8u101-linux-x64.tar.gz
> 
> \[root@localhost app\]\# ln -s jdk1.8.0\_101 jdk
> 
> 设置JAVA环境变量
> 
> \[root@localhost app\]\# vim \/etc\/profile.d\/java.sh
> 
> JAVA\_HOME=\/app\/jdk
> 
> PATH=$JAVA\_HOME\\/bin:$PATH
> 
> CLASSPATH=.:$JAVA\_HOME\/lib\/dt.jar:$JAVA\_HOME\/lib\/tools.jar
> 
> export JAVA\_HOME PATH CLASSPATH
> 
> 给脚本执行权限
> 
> \[root@localhost app\]\# chmod +x \/etc\/profile.d\/java.sh
> 
> 讲JAVA环境变量应用到当前shell
> 
> \[root@localhost app\]\# source \/etc\/profile.d\/java.sh
> 
> \[root@localhost app\]\# java -version
> 
> java version "1.8.0\_101"
> 
> Java\(TM\) SE Runtime Environment \(build 1.8.0\_101-b13\)
> 
> Java HotSpot\(TM\) 64-Bit Server VM \(build 25.101-b13, mixed mode\)

