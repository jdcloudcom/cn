# 创建账号

在创建 MongoDB 实例时，系统已为您创建了 root 账号，拥有 MongoDB 的 root 权限，您可以使用此账号登录数据库后，创建其他账号。

## 创建账号命令

> db.createUser(user, writeConcern)

user文档格式如下
```
{ user: "<name>",
  pwd: "<cleartext password>",
  customData: { <any information> },
  roles: [
    { role: "<role>", db: "<database>" } | "<role>",
    ...
  ]
 }
```

## 示例

1. 在products库创建accountAdmin01账号。

   ```
   use products
   db.createUser( { user: "accountAdmin01",
                    pwd: "changeMe",
                    customData: { employeeId: 12345 },
                    roles: [ { role: "clusterAdmin", db: "admin" },
                             { role: "readAnyDatabase", db: "admin" },
                             "readWrite"] },
                  { w: "majority" , wtimeout: 5000 } )
   ```


2. 创建带角色的用户

   以下操作在products库创建账号accountUser，并给账号赋予readWrite、dbAdmin角色。
   ```
   use products
   db.createUser(
      {
        user: "accountUser",
        pwd: "password",
        roles: [ "readWrite", "dbAdmin" ]
      }
   )
   ```
3. 创建不带角色的用户

   以下操作在admin库创建账号reportsUser，但未赋予角色。
   ```
   use admin
   db.createUser(
      {
        user: "reportsUser",
        pwd: "password",
        roles: [ ]
      }
   )
   ```

4. 创建带角色的管理员账号

   以下操作在admin库中创建appAdmin账号，并给账号赋予config库的readWrite角色。
   ```
   use admin
   db.createUser(
      {
        user: "appAdmin",
        pwd: "password",
        roles:
          [
            { role: "readWrite", db: "config" },
            "clusterAdmin"
          ]
      }
   )
   ```

## 常用角色

- 数据库用户角色：read，readWrite
- 数据库管理员角色：dbAdmin，dbOwner，userAdmin
- 集群管理员角色：clusterAdmin，clusterManager，clusterMonitor，hostManager
- 备份恢复角色：backup，restore
- 所有库角色：readAnyDatabase，readWriteAnyDatabase，userAdminAnyDatabase，dbAdminAnyDatabase
- 超级管理员角色：root 


关于MongoDB创建用户的详情说明请参见“ [MongoDB官方文档](https://docs.mongodb.com/v3.2/reference/method/db.createUser/#local-database)”。



## 相关参考

- [修改密码](Reset-Password.md)
