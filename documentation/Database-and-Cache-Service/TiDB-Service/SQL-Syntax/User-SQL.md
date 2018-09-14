# 用户操作

## 创建用户
使用 CREATE USER 语句创建一个用户 tiuser，密码为 123456
```
CREATE USER 'tiuser'@'localhost' IDENTIFIED BY '123456';
```
## 用户授权
授权用户 tiuser 可检索数据库 samp_db 内的表
```
CREATE USER 'tiuser'@'localhost' IDENTIFIED BY '123456';
```

## 用户权限查询
查询用户 tiuser 的权限
```
SHOW GRANTS for tiuser@localhost;
```

## 删除用户
删除用户 tiuser
```
DROP USER 'tiuser'@'localhost';
```
