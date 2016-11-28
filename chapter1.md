部署环境，这里将各个服务，分开部署，模拟分布式部署环境，各个服务器上可以根据情况进行集群方式部署。




| 主机 | IP | 端口 || --- | --- | --- || Redis | 192.168.0.118 | 6379 || Zookeeper | 192.168.0.119 | 2181 || Mpush | 192.168.0.120 | 3000 || Alloc | 192.168.0.121 | 9999 || Android | 192.168.0.103 | |

服务器版本为Centos7，最小化安装。

note：

1）最小化安装，默认网卡没有开机自动启动，可以编辑网卡文件\(默认为ifcfg-eth0\)，将ONBOOT设置为yes

> \[root@localhost ~\]\# vim \/etc\/sysconfig\/network-scripts\/ifcfg-eth0&gt; &gt; TYPE=Ethernet&gt; &gt; BOOTPROTO=dhcp&gt; &gt; DEFROUTE=yes&gt; &gt; PEERDNS=yes&gt; &gt; PEERROUTES=yes&gt; &gt; IPV4\_FAILURE\_FATAL=no&gt; &gt; IPV6INIT=yes&gt; &gt; IPV6\_AUTOCONF=yes&gt; &gt; IPV6\_DEFROUTE=yes&gt; &gt; IPV6\_PEERDNS=yes&gt; &gt; IPV6\_PEERROUTES=yes&gt; &gt; IPV6\_FAILURE\_FATAL=no&gt; &gt; NAME=eno16777736&gt; &gt; UUID=a4ad8a0c-ff3a-4a49-87fe-639f0053873f&gt; &gt; DEVICE=eno16777736&gt; &gt; **ONBOOT=yes**

2）安装系统基本依赖包，用于编译安装软件

> \[root@localhost ~\]\# yum install net-tools vim wget make gcc g++ gc++ -y

3）关闭防火墙和SELinux，防止系统干扰导致部署不成功

> \[root@localhost ~\]\# setenforce 0&gt; &gt; \[root@localhost ~\]\# iptables -F&gt; &gt; \[root@localhost ~\]\# iptables -X

