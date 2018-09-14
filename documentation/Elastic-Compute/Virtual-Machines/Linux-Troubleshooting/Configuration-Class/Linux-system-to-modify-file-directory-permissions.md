# Linux系统修改文件目录权限

Linux档案的基本权限就有九个，分别是owner/group/others三种身份各有自己的read/write/execute权限

举例：档案的权限字符为 -rwxrwxrwx  这九个权限是三个三个一组的！其中，我们可以使用数字来代表各个权限，各权限的分数对照表如下：

r:4 　　w:2　　　x:1



每种身份(owner/group/others)各自的三个权限(r/w/x)分数是需要累加的，例如当权限为： [-rwxrwx---] 分数则是：

owner = rwx = 4+2+1 = 7

group = rwx = 4+2+1 = 7

others= --- = 0+0+0 = 0



所以我们设定权限的变更时，该档案的权限数字就是770啦！变更权限的指令chmod的语法是这样的：


*[root@www ~]# chmod [-R] xyz* 

档案或目录 选项与参数： xyz : 就是刚刚提到的数字类型的权限属性，为 rwx 属性数值的相加。 -R : 进行递归(recursive)的持续变更，亦即连同次目录下的所有档案都会变更


举例来说，如果要将.bashrc这个档案所有的权限都设定启用，那么执行：


*[root@www ~]# ls -al .bashrc* 

*-rw-r--r-- 1 root root 395 Jul 4 11:45 .bashrc* 

*[root@www ~]# chmod 777 .bashrc* 

*[root@www ~]# ls -al .bashrc* 

*-rwxrwxrwx 1 root root 395 Jul 4 11:45 .bashrc*


那如果要将权限变成 -rwxr-xr-- 呢？那么权限的分数就成为 [4+2+1][4+0+1][4+0+0]=754！所以执行：


*[root@www ~]# chmod 754 filename*


如无法解决您的问题，请向我们提工单。
