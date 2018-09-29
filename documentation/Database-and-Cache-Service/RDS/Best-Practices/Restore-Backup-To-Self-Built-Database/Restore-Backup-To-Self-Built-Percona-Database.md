# 将备份文件恢复到自建数据库 Percona 
您可以将云数据库 Percona 实例的备份数据恢复到自建数据库中。

## 注意事项
* 自建数据库版本需要和备份文件的源数据库版本一致。
* 备份的解压软件只支持在 Linux 下执行。
* 解压工具的系统软件依赖：openssl，gzip， tee，python 版本 >= 2.7。
* 当前系统已经安装 percona xtrabackup >= 2.4 ；如果没有安装，请参考 [官方手册](https://www.percona.com/doc/percona-xtrabackup/2.4/index.html)。

## 操作说明
1. 安装环境依赖，见注意事项
2. 下载备份的解压工具，[点击下载](https://jddb-common-public.oss.cn-north-1.jcloudcs.com/percona_backup_extract_tool.tar.gz)，并解压，工具名 `percona_backup_exztract.py`，使用示例如下
    
    ```
    # 查看帮助手册
    ./percona_backup_extract.py -h
     
     # 解压云数据库 Percona 实例的备份数据
     ./percona_backup_extract.py  -v 5.7 -f ./backup.xbstream.gz.enc
    ```
3. 下载备份文件

    ```
    wget -c '<数据备份下载地址>' -O <自定义备份文件名>.xbstream.gz.enc

    -c：启动断点续传
    -O：将下载的结果保存为指定的文件，注意文件的后者必须是 .xbstream.gz.enc
    ```

4. 解压备份数据，解压后的文件会保存在当前目录的子目录 tmp_snapshot 中，假设当前目录为 $HOME。

    ```
    ./percona_backup_extract.py -v 5.7 -f <自定义备份文件名>.xbstream.gz.enc
    
    -v 参数可以不指定，默认：5.7，具体 -v 后面可以跟什么变量可以通过 -h 查看帮助手册得知。
    ```

5. 恢复解压好的备份文件

    ```
    innobackupex --defaults-file=$HOME/tmp_snapshot/backup-my.cnf --apply-log $HOME/tmp_snapshot
    ``` 
    当看到 ***innobackupex completed OK!*** 时， 表明执行成功，你就可以继续下一步操作了。

6. 修改配置文件 backup-my.cnf

    ```
    # The MySQL server
    [mysqld]
    innodb_checksum_algorithm=innodb
    #innodb_log_checksum_algorithm=strict_crc32
    innodb_data_file_path=ibdata1:512M;ibdata2:512M:autoextend
    innodb_log_files_in_group=3
    innodb_log_file_size=536870912
    #innodb_fast_checksum=false
    #innodb_page_size=16384
    #innodb_log_block_size=512
    innodb_undo_directory=.
    innodb_undo_tablespaces=0
    #redo_log_version=1
    ```

7. 修改文件属主，并确定文件所属为 MySQL 用户

    ```
    chown -R mysql:mysql $HOME/tmp_snapshot
    ```

8. 启动 Percona 进程

    ```
    mysqld --defaults-file=$HOME/tmp_snapshot/backup-my.cnf --user=mysql --datadir=$HOME/tmp_snapshot --socket=$HOME/tmp_snapshot/mysql.sock &
    ```

9. 登录 Percona 数据库

    ```
    mysql -uroot -p --socket=$HOME/tmp_snapshot/mysql.sock
    ```

* 密码默认为空， 直接回车即可。
