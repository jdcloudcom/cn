# Windows系统php开启PDO
1. 打开php.ini文件

2. 打开后，搜索 *extension=php_pdo.dll* 和 *extension=php_pdo_mysql.dll* ，去掉前面“;”的注释。 

最终这两行配置内容如下： 


***extension=php_pdo.dll*** 

***extension=php_pdo_mysql.dll***

3.重新启动apache或者iis服务

4.新建一个PHP测试，内容为


<?php

phpinfo();

?>

可以测试PDO模块是否开启。



如无法解决您的问题，请向我们提工单。
