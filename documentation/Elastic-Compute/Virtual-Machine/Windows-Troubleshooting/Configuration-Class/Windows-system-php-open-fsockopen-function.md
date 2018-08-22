# Windows系统php开启fsockopen函数
在安装Discuz 和 phpwind程序时需要开启fsockopen函数，开启方法如下：

php环境配置好之后会有个php.ini文件，这是php的配置文件，以Windows 2008一键安装环境为例，

1.php.ini文件在服务器的C:\websoft\php-5.5.7目录下，其他方法安装的php环境可以在磁盘中搜索一下。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9Fphp%E5%BC%80%E5%90%AFfsockopen%E5%87%BD%E6%95%B001.png)

2.找到php.ini文件，用记事本打开，查找 allow_url_fopen = 看看后面是 off 还On ，如果是off 那就修改成On。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9Fphp%E5%BC%80%E5%90%AFfsockopen%E5%87%BD%E6%95%B002.png)

3.在php.ini文件中继续查找extension=php_openssl.dll，extension=php_openssl.dll这段代码前面有个 ; 号，将 ; 号删除，然后保存。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9Fphp%E5%BC%80%E5%90%AFfsockopen%E5%87%BD%E6%95%B003.png)

4.最后重启IIS，打开IIS信息服务管理器，选择右侧的“重新启动”，重启后fsockopen函数即为正常开启。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/Virtual-Machine/Windows/Windows%E7%B3%BB%E7%BB%9Fphp%E5%BC%80%E5%90%AFfsockopen%E5%87%BD%E6%95%B004.png)

如无法解决您的问题，请向我们提工单。
