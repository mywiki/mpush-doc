部署环境，这里将各个服务，分开部署，模拟分布式部署环境，各个服务器上可以根据情况进行集群方式部署。

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

