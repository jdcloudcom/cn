# describeImageConstraintsBatch


## 描述
批量查询镜像的规格类型限制。<br>
通过此接口可以查看镜像不支持的规格类型。只有官方镜像、第三方镜像有规格类型的限制，个人的私有镜像没有此限制。


## 请求方式
GET

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/imageConstraints

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ids**|String[]|False||镜像ID列表|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**imageConstraints**|[ImageConstraint[]](##ImageConstraint)|镜像限制|
### <a name="ImageConstraint">ImageConstraint</a>
|名称|类型|描述|
|---|---|---|
|**imageId**|String|镜像ID|
|**imageInstanceTypeConstraint**|[ImageInstanceTypeConstraint](##ImageInstanceTypeConstraint)|镜像规格类型限制|
### <a name="ImageInstanceTypeConstraint">ImageInstanceTypeConstraint</a>
|名称|类型|描述|
|---|---|---|
|**constraintsType**|String|受限制的规格类型。excludes：排除指定的实例类型；includes：只包含指定的实例类型，暂不支持includes|
|**instanceTypes**|String[]|规格类型列表|

## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|

## 请求示例
GET
```

```

## 返回示例
无
