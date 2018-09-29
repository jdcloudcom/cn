# 从云数据库 MySQL 迁移到云数据库 Percona
这里主要讲下如何从京东云云数据库 MySQL 迁移到京东云云数据库 Percona，云数据库 Percona 相对于云数据库 MySQL 提供了一些更加高级的功能和特性，详细的 Percona 和 MySQL 的比较可以参见 [Perocna 官方手册](https://www.percona.com/software/mysql-database/percona-server/feature-comparison)。

## 注意事项
* 如果要将云数据库 MySQL 数据导入到云数据库 Percona，需要通过云主机作为传输媒介。
* 新建的云数据库 Percona 实例，云主机需要和云数据库 MySQL 在同一个 私有网络 内。
* 新建的云数据库 Percona 实例的容量空间要确保不能小于云数据库 MySQL。

## 操作步骤
1. 创建云主机，具体的创建步骤请参考 [创建云主机](https://www.jdcloud.com/help/detail/303/isCatalog/1)，创建云主机时候需要注意以下几点
    * 请确保云主机和云数据库 MySQL 在同一个 ***私有网络*** 内。
    * 请确保云主机所在子网的 ***网络 ACL*** 是允许访问云数据库 MySQL 。
2. 完成云主机创建工作之后，开始将云数据库 MySQL 数据导出到云主机中，执行命令

    ```
    mysqldump -u用户名 -p密码 --single-transaction  --set-gtid-purged=OFF -B 数据库名称 > /路径/导出文件名.sql

    参数描述
        用户名：云数据库 MySQL 的用户名。
        密码：云数据库 MySQL 的密码。
        数据库名称：填写您需要导出的库名，多个库名通过空格来分隔。
    ```

3. 完成云数据库 MySQL 数据导出到云主机中之后，接下来就开始创建云数据库 Percona 了。
4. 创建云数据库 Percona，具体的创建步骤请参考 [创建云数据库 RDS 实例](../../../Operation-Guide/Instance/Create-Instance.md)。
5. 通过控制台进行库的创建，确保云数据库 MySQL 中需要导出的库名在云数据库 Percona 中同样的创建了一遍，具体的创建步骤请参考 [创建库](../../../Operation-Guide/Database-Management/Create-Database.md)。
6. 通过控制台进行数据库账号的创建，也可以使用创建云数据库 Percona 的时候的账号，然后赋予这个账号在第 2 步操作中新建的库的 读写 权限，具体的创建步骤请参考 [创建账号](../../../Operation-Guide/Account/Create-Account.md)。
7. 完成云数据库 Percona 创建和初始化工作之后，开始将云主机中的数据导入到云数据库 Percona 中，执行命令

    ```
    mysql -u用户名 -p密码 -h 云数据库域名 < /云主机路径/导出文件名.sql

    参数描述
        用户名：第 6 步操作中的用户名。
        密码：第 6 步操作中的用户对应的密码。
        数据库域名：云数据库 Percona 的域名可以在实例的详情页查看。
    ```

8. 如果没有任何错误提示，表示导入成功。您可以登录到云数据库 Percona 里面查看，是否数据真的已经导入进去了。
