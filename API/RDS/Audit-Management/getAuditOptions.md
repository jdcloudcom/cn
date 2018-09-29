# getAuditOptions


## 描述
获取当前系统所支持的各种数据库版本的审计选项及相应的推荐选项<br>- 仅支持SQL Server

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/audit:getOptions

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |审计选项类别，**大小写敏感**，目前支持两种类型：<br>（1）AuditOptions开头：在disalbed参数中返回SQL Server各个版本支持的所有选项，支持的名称为<br>AuditOptions2008R2<br>AuditOptions2012<br>AuditOptions2014<br>AuditOptions2016<br>例如输入参数为"AuditOptions2016"，则在disabled字段中返回SQL Server 2016 版本所支持的所有的审计选项<br>（2）AuditDefault开头：京东云建议的默认选项,在enabled参数中返回建议开启的选项，在disabled参数中返回不开启的选项，支持的名称为：<br>AuditDefault2008R2<br>AuditDefault2012<br>AuditDefault2014<br>AuditDefault2016<br>例如输入参数为"AuditDefault2016"，则在enabled字段返回SQL Server 2016 版本中京东云建议开启的审计选项，在disabled字段中返回建议不开启的选项|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**disabled**|String[]| |
|**enabled**|String[]| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
