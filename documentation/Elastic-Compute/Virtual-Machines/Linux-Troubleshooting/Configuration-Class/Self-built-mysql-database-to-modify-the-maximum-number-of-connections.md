# 自建mysql数据库修改最大连接数

连接在云主机上搭建的mysql数据库时，有时会报1040错误，提示过多连接，如图

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/%E8%87%AA%E5%BB%BAmysql%E6%95%B0%E6%8D%AE%E5%BA%93%E4%BF%AE%E6%94%B9%E6%9C%80%E5%A4%A7%E8%BF%9E%E6%8E%A5%E6%95%B001.png)

此时需要修改/etc/my.cnf文件，在[mysqld]部分中新增或修改max_connections=N条目，默认值为100，可根据需要进行调整，如图

![](https://github.com/jdcloudcom/cn/blob/cn-VirtualMachine-Linux/image/Elastic-Compute/Virtual-Machine/Linux/%E8%87%AA%E5%BB%BAmysql%E6%95%B0%E6%8D%AE%E5%BA%93%E4%BF%AE%E6%94%B9%E6%9C%80%E5%A4%A7%E8%BF%9E%E6%8E%A5%E6%95%B002.png)

修改完后wq保存文件，重启mysql数据库，验证是否生效。
