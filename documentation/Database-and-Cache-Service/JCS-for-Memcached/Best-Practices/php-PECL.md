# php客户端: PECL
## 客户端介绍：
http://pecl.php.net/support.php?spm=a2c4g.11186623.2.5.uh6Uqi
## 客户端版本介绍：
http://pecl.php.net/package/memcached?spm=a2c4g.11186623.2.6.5EavrO
## 安装 SASL 相关环境：
<code>yum install -y cyrus-sasl-plain cyrus-sasl cyrus-sasl-devel cyrus-sasl-lib </code>
## 安装PECL：
```
wget http://pecl.php.net/get/memcached-2.2.0.tgz
tar zxvf memcached-2.2.0.tgz
cd memcached-2.2.0
phpize
./configure --with-libmemcached-dir=/usr/local/libmemcached --enable-memcached-sasl
make && make install
```
## 添加php外挂模块：修改php.ini文件（默认在/etc目录下），添加：
```
extension=memcached.so 
memcached.use_sasl = 1
```
## php代码示例1（密码访问）：
```
<?php
$memcached = new Memcached;
$memcached->addServer('ip', port); 
$memcached->setOption(Memcached::OPT_BINARY_PROTOCOL, true);
$memcached->setSaslAuthData('username', 'port'); 
$memcached->set("key", "value");
echo 'key: ',$memcached->get("key");
$memcached->delete("key",0);
$memcached->quit();
```
## php代码示例2（免密访问）：
```
<?php
$memcached = new Memcached;
$memcached->addServer('ip', port); 
$memcached->set("key", "value");
echo 'key: ',$memcached->get("key");
$memcached->delete("key",0);
$memcached->quit();
?>
```
