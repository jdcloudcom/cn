# createDomain


## 描述
域名注册
域名注册前，请确保用户的京东云账户有足够的资金支付，Openapi接口回返回订单号，可以用此订单号向计费系统查阅详情


## 请求方式
POST

## 请求地址
https://domain.jdcloud-api.com/v1/regions/{regionId}/domain

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainName**|String|True| |域名|
|**term**|Integer|True| |注册年限，最多10年|
|**templateId**|Long|True| |模板ID|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](createDomain#result)| |
|**requestId**|String|此次请求的ID|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[DomainOrder](createDomain#domainorder)|域名购买返回结果，后续需要调用订单支付接口|
### <div id="DomainOrder">DomainOrder</div>
|名称|类型|描述|
|---|---|---|
|**orderId**|String|订单唯一ID|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
