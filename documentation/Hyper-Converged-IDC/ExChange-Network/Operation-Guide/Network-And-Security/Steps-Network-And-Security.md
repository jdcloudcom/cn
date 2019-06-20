## 操作步骤

下面以建一个filter表防火墙为例：

### **1. 清除原有规则**

```
[root@jd ~]# iptables -F    #清除预设表filter中的所有规则链的规则
[root@jd ~]# iptables -X    #清除预设表filter中使用者自定链中的规则
```
### **2. 设定预设规则**

```
[root@jd ~]# iptables -P OUTPUT ACCEPT
[root@jd ~]# iptables -P FORWARD DROP
```

### **3.保存规则**
```
[root@jd ~]# iptables -L –n        #查看是否设置好， 看到全部 DROP 了。这条命令只是临时的， 重启服务器还是会恢复到原有规则。
[root@jd ~]# service iptables save #将规则保存在 /etc/sysconfig/iptables，使重启后也可生效。
```

### **4.添加规则**

远程SSH登录（开启22端口）
```
[root@jd ~]# iptables -A INPUT -p tcp --dport 22 -j ACCEPT
[root@jd ~]# iptables -A OUTPUT -p tcp --sport 22 -j ACCEPT
```
WEB服务器（开启80端口）
```
[root@jd ~]# iptables -A INPUT -p tcp --dport 80 -j ACCEPT
```
邮件服务器（开启25、110端口）
```
[root@jd ~]# iptables -A INPUT -p tcp --dport 110 -j ACCEPT
[root@jd ~]# iptables -A INPUT -p tcp --dport 25 -j ACCEPT
```
FTP服务器（开启21端口）
```
[root@jd ~]# iptables -A INPUT -p tcp --dport 21 -j ACCEPT
```
DNS服务器（开启53端口）
```
[root@jd ~]# iptables -A INPUT -p tcp --dport 53 -j ACCEPT
```
HTTPS (开启443端口)
```
[root@jd ~]# iptables -A INPUT -p tcp --dport 443-j ACCEPT
```
允许ICMP（允许ping）
```
[root@jd ~]# iptables -A OUTPUT -p icmp -j ACCEPT
[root@jd ~]# iptables -A INPUT -p icmp -j ACCEPT
```
允许loopback(禁止loopback会导致DNS无法正常关闭等问题)
```
[root@jd ~]# iptables -A INPUT -i lo -p all -j ACCEPT
[root@jd ~]# iptables -A OUTPUT -o lo -p all -j ACCEPT
```
禁止某个IP的tcp访问
```
[root@jd ~]# iptables -A INPUT -p tcp -s 192.168.1.2 -j DROP
```

### **5.删除规则**

首先我们要知道 这条规则的编号，每条规则都有一个编号

通过 iptables -L -n --line-number 可以显示规则和相对应的编号
```
[root@jd ~]# iptables -L -n --line-number
```

```
num target     prot opt source               destination
1    DROP       tcp -- 0.0.0.0/0            0.0.0.0/0           tcp dpt:3306
2    DROP       tcp -- 0.0.0.0/0            0.0.0.0/0           tcp dpt:21
3    DROP       tcp -- 0.0.0.0/0            0.0.0.0/0           tcp dpt:80
```
 

多了 num 这一列， 这样我们就可以 看到刚才的规则对应的是 编号2。那么我们就可以进行删除了。
```
[root@jd ~]# iptables -D INPUT 2
```
删除INPUT链编号为2的规则。

再 iptables -L -n 查看一下 已经被清除了。
