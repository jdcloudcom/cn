# Accesskey管理
为了保证云资源的使用安全，当以API调用相关资源和操作时，要求使用 Access Key 验证您和应用程序的身份，以确保访问者具有相关权限。Access Key 包含 Access Key ID 和 Access Key Secret 构成。拥有您的 Access Key 的任何人将与您拥有相同的资源访问和操作权限，可以无限制地访问您账户中的所有资源并进行相应的操作。您可以创建、禁用或删除您的 Access Key，同时也建议您定期轮换 Access Key 以保证您的账户和资源安全。

每个主账号可拥有 5 组有效访问密钥，每个 IAM 用户可拥有 2 组有效的访问密钥，这在您必须轮换用户的访问密钥时非常有用。您可以禁用用户的访问密钥，这意味着该密钥不能用于 API  调用，在轮换密钥或取消用户对 API 的访问时，可以执行此操作。您可以随时删除访问密钥，不过，当您删除访问密钥时，意味着永久删除且无法恢复。

主账户的 Access Key 管理
![](../../../image/User/Account%20Management/AccessKey%20Management/%E4%B8%BB%E8%B4%A6%E6%88%B7%E7%9A%84Accesskey%E7%AE%A1%E7%90%86.png)

主账号为子账号管理 Access Key
![](../../../image/User/Account%20Management/AccessKey%20Management/%E4%B8%BB%E8%B4%A6%E6%88%B7%E7%9A%84Accesskey%E7%AE%A1%E7%90%86.png)

子账号的 Access Key管理
![](../../../image/User/Account%20Management/AccessKey%20Management/%E5%AD%90%E8%B4%A6%E5%8F%B7%E7%9A%84Accesskey%E7%AE%A1%E7%90%86.png)
