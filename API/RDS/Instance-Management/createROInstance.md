# createROInstance


## 描述
创建MySQL的只读实例<br> - 仅支持MySQL<br> - 创建的只读实例跟主实例在同一个VPC同一个子网中<br> * 只读实例只支持按配置计费

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:createROInstance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceName**|String|True| |实例名称，具体规则可参见帮助中心文档:[名称及密码限制](../../../documentation/Database-and-Cache-Service/RDS/Introduction/Restrictions/SQLServer-Restrictions.md)|
|**instanceClass**|String|True| |只读实例规格FlavorId|
|**instanceStorageType**|String|False| |存储类型，参见[枚举参数定义](../Enum-Definitions/Enum-Definitions.md)，缺省值为：LOCAL_SSD|
|**instanceStorageGB**|Integer|True| |磁盘空间|
|**azId**|String|True| |可用区ID|
|**vpcId**|String|False| |VPC的ID，如果没有填写就保持和常规实例一样的VPC|
|**subnetId**|String|False| |子网ID，如果没有填写就保持和常规实例一样的subnet|
|**parameterGroup**|String|False| |参数组ID，缺省采用和常规实例一样的参数组|
|**storageEncrypted**|Boolean|False| |实例数据加密(存储类型为云硬盘才支持数据加密)。false：不加密；true：加密。缺省为false。|
|**count**|Integer|False| |创建只读实例的数目,缺省为1|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#Result)| |

### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**roInstanceId**|String[]|新创建的只读实例ID的列表|
|**orderId**|String|订单ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
