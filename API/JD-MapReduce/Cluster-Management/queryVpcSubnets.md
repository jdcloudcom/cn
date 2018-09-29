# queryVpcSubnets


## 描述
查询Vpc子网集合

## 请求方式
POST

## 请求地址
https://idata-jmr-api.jcloud.com/v1/regions/{regionId}/vpcSubnets/{vpcId}:query

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|
|**vpcId**|String|True| | |

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|QueryVpcSubnets[]|VPC子网信息集合|
|**message**|String| |
|**status**|String| |
### QueryVpcSubnets
|名称|类型|描述|
|---|---|---|
|**vpcSubnetId**|String|VPC 子网id|
|**vpcSubnetName**|String|VPC 子网名称|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**500**|Internal server error|
