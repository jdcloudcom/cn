# 登录数据库提示无权限

## 问题描述

我在登录 MongoDB 数据库时，账号密码输入都正确，但提示鉴权失败。

![](https://github.com/jdcloudcom/cn/blob/master/image/mongodb/mongo-030.png)

## 问题处理

MongoDB 数据库在登录时需输入账号对应的鉴权库，如鉴权库未正确输入则会提示鉴权失败。假设您账号的授权库为test，可使用以下命令登录：

> mongo --host xxxx.jdcloud.com:27017 --authenticationDatabase test -u <username> -p <password>

或者

> mongodb://<username>:<password>@xxxx1.jdcloud.com:27017,xxxx2.jdcloud.com:27017/test?replicaSet=mgset-3937681456 

## 后续处理
  如通过以上操作仍未解决问题，请 [提交工单](https://ticket.jdcloud.com/myorder/form?cateId=166&questionId=238) 或 致电客服 400-615-1212 。
