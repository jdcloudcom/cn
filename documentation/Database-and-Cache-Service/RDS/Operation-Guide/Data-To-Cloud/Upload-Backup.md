# 上传备份文件
## 1. 生成文件上传的Key值
- 点击【生成上传Key】,可以生成一个Key，用于文件的身份验证，登录等
- 点击Key最后的图标，可以自动拷贝Key

![上传备份1](../../../image/RDS/Upload-Backup-1.png)

## 2. 下载上传工具

- 在SQL Server实例详情中，进入【单库上云】页面，点击【下载上传工具】，下载upload-tool.exe。
- 上传工具目前仅支持windows版本。

![上传备份2](../../../image/RDS/Upload-Backup-2.png)

## 3. 上传文件

执行upload-tool.exe，上传备份文件，upload-tool.exe的命令格式为：
```
upload-tool.exe -r [区域代码] -f [备份文件本地路径] -k [上传key值]
```
## 如果备份文件已经在京东云内网中，建议使用内网方式上传，上传效率更高，命令如下：
```
upload-tool.exe -r [区域代码] -f [备份文件本地路径] -k [上传key值] -i

## -i:表示使用内网进行文件上传
```

区域代码支持以下区域

|区域名称|区域代码|
|-|-|
|华北-北京|cn-north-1|
|华东-宿迁|cn-east-1|
|华东-上海|cn-east-2|
|华南-广州|cn-south-1|

**命令示例：** 将“z:/Backup/testdb.bak”这个备份文件上传到华北-北京区域。
```
upload-tool.exe -r cn-north -f z:/Backup/testdb.bak -k   U2FsdGVkX19c7B0ZGP0mU++sXgWZoHCeGP0tacbRz3TpoOKPsXmncA
```
## 注意事项：

1. 出于安全考虑，key值在1个小时之内有效。Key过期后需点击按钮重新生成
2. 为安全起见，上传文件时不支持同名文件的覆盖，请先删除原文件后再上传。
