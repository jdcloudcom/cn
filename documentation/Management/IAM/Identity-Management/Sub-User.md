
# 什么是子用户
子用户是访问控制 (IAM) 中的一种身份，每个子用户对应一个确定的个人实体，如企业的技术人员，运维人员等。本文介绍了如何创建、管理子账号，以及子账号如何登录控制台进行操作。

# 创建子账号
登录京东云控制台，进入访问控制 > 用户管理，点击【创建】按钮，在创建子账号窗口填写子账号信息：

 - 子账号的登录名支持 4-20 位英文、汉字或数字以及短横线 “-” 和下划线 “_”；
 - 子账号的密码长度为 6-20 位，需包含英文字母和数字或符号中的一种字符（不含空格）。
 ![创建子账号](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/%E5%88%9B%E5%BB%BA%E5%AD%90%E8%B4%A6%E6%88%B7.png)

# 为子账号重置密码

在用户管理列表页面，可以编辑子账号的登录名、备注及联系信息，也可以快捷管理子用户的授权和群组，或删除子账号。
![为子账号重置密码](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/%E4%B8%BA%E5%AD%90%E8%B4%A6%E5%8F%B7%E9%87%8D%E7%BD%AE%E5%AF%86%E7%A0%81.png)

点击子用户名，进入子用户详情，从 用户详情 页面右上角的 操作 > 重置密码 入口，您可以重新设置子账号登录密码。
![重置密码1](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/%E9%87%8D%E7%BD%AE%E5%AF%86%E7%A0%811.png)
![重置密码2](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/%E9%87%8D%E7%BD%AE%E5%AF%86%E7%A0%812.png)

# 为子账号授权

在 用户授权策略 页面，可以查看子账号当前的授权情况。
![子账号当前授权](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/%E5%AD%90%E8%B4%A6%E5%8F%B7%E5%BD%93%E5%89%8D%E6%8E%88%E6%9D%83.png)
点击【添加授权策略】，选择需要授权的策略，附加到子账号。为子账号添加多条策略时，子账号的权限为各策略的合集。
![添加授权策略](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/%E6%B7%BB%E5%8A%A0%E7%94%A8%E6%88%B7%E6%8E%88%E6%9D%83%E7%AD%96%E7%95%A5.png)

#将子账号加入群组

在 群组授权策略 页面，点击【加入群组】，选择用户需要加入的用户组。
![加入群组](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/%E5%8A%A0%E5%85%A5%E7%BE%A4%E7%BB%84.png)
同时，在该页面您可以查看用户已加入的群组授权情况，也可以将用户移除特定的群组。
![已加入群组](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/%E5%B7%B2%E5%8A%A0%E5%85%A5%E7%BE%A4%E7%BB%84.png)

# 子账号登录控制台

在您配置访问控制的概览页里，您可以查看已创建的子账号、群组、自定义授权策略的数目。
![子账号登录控制台](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/%E5%AD%90%E8%B4%A6%E5%8F%B7%E7%99%BB%E5%BD%95%E6%8E%A7%E5%88%B6%E5%8F%B0.png)
同时，该页面内显示了子账号登录链接。该链接即为您的所有子账号登录控制台的唯一入口。
![子账号登录页面](https://github.com/jdcloudcom/cn/blob/edit/image/IAM/%E5%AD%90%E8%B4%A6%E5%8F%B7%E7%99%BB%E5%BD%95%E9%A1%B5%E9%9D%A2.png)
