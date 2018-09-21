# 连接实例 
如果您购买了分布式数据库 TiDB 实例，可以通过 MySQL 连接器连接，也可以使用 API 连接。数据库连接器为客户端提供了连接数据库服务端的方式，APIs 提供了使用 MySQL 协议和资源的底层接口。无论是连接器还是 API，都可以用来在不同的语言和环境内连接服务器并执行 sql 语句，包括 odbc、java(jdbc)、Perl、Python、PHP、Ruby 和 C。 

## 通过京东云主机连接 TiDB
在京东云主机安装 MySQL 客户端后，可进入命令行方式连接 TiDB。 
1. 命令格式：mysql -h域名 -P端口 -u用户名-p密码 。
2. 域名：要访问的实例的域名，域名展示在实例的详情页面。
3. 端口：端口号展示在实例的详情页。
4. 用户名：实例的用户名，目前只支持 root。 
5. 密码：用户名 root 对应的密码。

## 使用 MySQL 连接器连接 TiDB  
官方提供了以下连接器 , TiDB 可以兼容所有这些：
- MySQL Connector/C：C 语言的客户端库，是 libmysqlclient 的替代品
- MySQL Connector/C++：C++ 语言的客户端库
- MySQL Connector/J：Java 语言的客户端库，基于标准 JDBC 接口
- MySQL Connector/Net：.Net 语言的客户端库，MySQL for Visual Studio使用这个库，支持 Microsoft Visual Studio 2012，2013，2015和2017版本
- MySQL Connector/ODBC：标准的 ODBC 接口，支持 Windows，Unix 和 OS X
- MySQL Connector/Python：Python 语言的客户端包，和 Python DB API version 2.0 一致


## 使用 MySQL API 连接 TiDB
如果使用 C 语言程序直接连接 TiDB，可以直接链接 libmysqlclient 库，使用 MySQL 的 C API，这是最主要的一种 C 语言连接方式，被各种客户端和 API 广泛使用，包括 Connector/C。

更多的API：
- MySQL PHP API
- MySQL Perl API
- MySQL Python API
- MySQL Ruby APIs
- MySQL Tcl API
- MySQL Eiffel Wrapper
- Mysql Go API