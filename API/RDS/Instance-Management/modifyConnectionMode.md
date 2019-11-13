# modifyConnectionMode


## 描述
修改MySQL实例的连接模式：标准模式(standard) 和高安全模式(security).<br>- **标准模式**：响应时间短，但没有 SQL 审计和拦截的能力。<br>- **高安全模式**：具备一定的 SQL注入拦截能力（通过分析表达式、关键系统函数等来实现防御 SQL 注入攻击），并可开启 SQL 审计，但会增加一定的响应时间。<br>- 仅支持MySQL

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:modifyConnectionMode

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**connectionMode**|String|True| |连接模式<br> - standard：标准模式(缺省)，响应时间短，但没有 SQL 审计和拦截的能力 <br>- security：高安全模式，具备一定的 SQL注入拦截能力，并可开启 SQL 审计，但会增加一定的响应时间|


## 返回参数
无


## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
