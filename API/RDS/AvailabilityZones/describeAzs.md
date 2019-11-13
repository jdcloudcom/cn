# describeAzs


## 描述
查看指定地域下各种RDS数据库支持的可用区，不同类型的RDS支持的可用区不一样

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/azs

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**engine**|String|True| |RDS引擎类型，参见[枚举参数定义](../Enum-Definitions/Enum-Definitions.md)|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#Result)| |

### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**azs**|String[]|可用区的ID的列表|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
