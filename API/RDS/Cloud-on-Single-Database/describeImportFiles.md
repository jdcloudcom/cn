# describeImportFiles


## 描述
获取用户通过单库上云工具上传到该实例上的文件列表<br>- 仅支持SQL Server

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/importFiles

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**importFiles**|ImportFile[]|导入文件的集合|
### ImportFile
|名称|类型|描述|
|---|---|---|
|**isLocal**|String|是否所属当前实例.<br> 1：当前实例；<br>0：不是当前实例，为共享文件|
|**name**|String|文件名称|
|**sharedFileGid**|String|如果该文件是共享文件，则有全局ID，如不是共享文件，则为空。该全局ID在文件删除时，需要用到|
|**sizeByte**|Integer|文件大小，单位Byte|
|**uploadTime**|String|文件上传完成时间，格式为：YYYY-MM-DD HH:mm:ss|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
