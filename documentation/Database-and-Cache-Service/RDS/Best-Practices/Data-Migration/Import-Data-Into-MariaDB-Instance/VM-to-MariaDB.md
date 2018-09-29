# 从云主机 MariaDB 迁移到云数据库 MariaDB 
这里主要讲下如何从云主机自建 MariaDB 迁移到京东云云数据库 MariaDB，自建 MariaDB 需要您自己做 MariaDB 服务日常的运维，监控，备份等等其他操作，使用京东云云数据库 MariaDB 就省去了这些烦恼，只需要关注使用即可。

## 注意事项
* 新建的 MariaDB 实例需要和云主机在同一个 ***私有网络*** 内。
* 新建的 MariaDB 实例的容量空间要确保不能小于在云主机中自建的 MariaDB 。

## 操作步骤
1. 创建云数据库 MariaDB，具体的创建步骤请参考 [创建云数据库 RDS 实例](../../../Operation-Guide/Instance/Create-Instance.md)。
2. 通过控制台进行库的创建，确保云主机自建的 MariaDB 中需要导出的库名在云数据库 MariaDB 中同样的创建了一遍，具体的创建步骤请参考 [创建库](../../../Operation-Guide/Database-Management/Create-Database.md)。
3. 通过控制台进行数据库账号的创建，也可以使用创建云数据库 MariaDB 的时候的账号，然后赋予这个账号在第 2 步操作中新建的库的 ***读写*** 权限，具体的创建步骤请参考 [创建账号](../../../Operation-Guide/Account/Create-Account.md)。
4. 完成云数据库 MariaDB 创建和初始化工作之后，开始从云主机中自建的 MariaDB 进行数据导出到云主机本地的操作，执行命令

    ```
    mysqldump -u用户名 -p密码 --single-transaction --set-gtid-purged=OFF -B 数据库名称 > /路径/导出文件名.sql

    参数描述
        用户名：自建数据库的用户名。
        密码：自建数据库的密码。
        数据库名称：填写您需要导出的库名，多个库名通过空格来分隔。
    ```

5. 完成云主机中自建的 MariaDB 数据导出到本地之后，就可以将数据导入到云数据库 MariaDB 中，执行命令

    ```
    mysql -u用户名 -p密码 -h 云数据库域名 < /路径/导出文件名.sql

    参数描述
        用户名：第 3 步操作中的用户名。
        密码：第 3 步操作中的用户对应的密码。
        数据库域名：云数据库 MariaDB 的域名可以在实例的详情页查看。
    ```
    
6. 如果没有任何错误提示，表示导入成功。您可以登录到云数据库 MariaDB 里面查看，是否数据真的已经导入进去了。
