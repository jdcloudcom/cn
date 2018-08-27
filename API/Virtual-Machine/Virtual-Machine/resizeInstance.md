# resizeInstance


## 描述
云主机变更规格类型<br>
云主机的状态必须为<b>stopped</b>状态。<br>
16年创建的云硬盘做系统盘的主机，一代与二代规格类型不允许相互调整。<br>
本地盘(local类型)做系统盘的主机，一代与二代规格类型不允许相互调整。<br>
使用高可用组(Ag)创建的主机，一代与二代规格类型不允许相互调整。<br>
云硬盘(cloud类型)做系统盘的主机，一代与二代规格类型允许相互调整。<br>
如果当前主机中的弹性网卡数量，大于规格类型允许的弹性网卡数量，会返回错误。可查询<a href="https://www.jdcloud.com/help/detail/2901/isCatalog/1">DescribeInstanceTypes</a>接口获得指定地域或可用区的规格信息。<br>
当前主机所使用的镜像，需要支持要变更的目标规格类型，否则返回错误。可查询<a href="https://www.jdcloud.com/help/detail/2872/isCatalog/1">DescribeImageConstraints</a>接口获得指定镜像的规格类型限制信息。<br>
云主机欠费时，无法更改规格类型。


## 请求方式
POST

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}:resizeInstance

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True||云主机ID|
|**regionId**|String|True||地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceType**|String|True||规格类型，可查询<a href="https://www.jdcloud.com/help/detail/2901/isCatalog/1">DescribeInstanceTypes</a>接口获得指定地域或可用区的规格信息。|


## 返回参数
|名称|类型|描述|
|---|---|---|



## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|
