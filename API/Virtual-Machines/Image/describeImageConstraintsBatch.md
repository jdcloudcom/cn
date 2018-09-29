# describeImageConstraintsBatch


## 描述
批量查询镜像的实例规格限制。<br>
通过此接口可以查看镜像不支持的实例规格。只有官方镜像、第三方镜像有实例规格的限制，个人的私有镜像没有此限制。


## 请求方式
GET

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/imageConstraints

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ids**|String[]|False| |镜像ID列表|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**imageConstraints**|ImageConstraint[]|镜像限制|
### ImageConstraint
|名称|类型|描述|
|---|---|---|
|**imageId**|String|镜像ID|
|**imageInstanceTypeConstraint**|ImageInstanceTypeConstraint|使用镜像创建实例的规格限制|
### ImageInstanceTypeConstraint
|名称|类型|描述|
|---|---|---|
|**constraintsType**|String|限制类型。取值：excludes：不支持的实例类型；includes：支持的实例类型。|
|**instanceTypes**|String[]|实例规格列表|

## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|
