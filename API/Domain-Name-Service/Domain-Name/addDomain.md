# addDomain


## 描述
添加主域名

## 请求方式
POST

## 请求地址
https://clouddnsservice.jdcloud-api.com/v1/regions/{regionId}/domainAdd

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**billingType**|Integer|False| |计费类型，收费套餐的域名必填|
|**buyType**|Integer|False| |1->新购买、2->升级，收费套餐的域名必填|
|**domainId**|Integer|False| |域名ID，升级高级版必填|
|**domainName**|String|True| |要添加的域名|
|**packId**|Integer|True| |域名的套餐类型, 0->免费 ,1->企业版, 2->高级版|
|**timeSpan**|Integer|False| |1，2，3 ，时长，收费套餐的域名必填|
|**timeUnit**|Integer|False| |时间单位，收费套餐的域名必填|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|此次请求的ID|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**data**|Domain|新添加的的域名结构|
|**order**|String|添加收费版域名的订单号|
### Domain
|名称|类型|描述|
|---|---|---|
|**createTime**|Integer|创建时间，格式Unix timestamp|
|**domainName**|String|域名字符串|
|**expirationDate**|Integer|过期时间，格式Unix timestamp|
|**id**|Integer|域名的唯一ID|
|**packId**|Integer|套餐类型，0->免费 1->企业版 2->高级版|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
