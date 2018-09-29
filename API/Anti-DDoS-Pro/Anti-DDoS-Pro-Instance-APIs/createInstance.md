# createInstance


## 描述
创建实例

## 请求方式
POST

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/instances

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceSpec**|InstanceSpec|True| |创建实例请求参数|

### InstanceSpec
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**bp**|Integer|False| |保底带宽：单位Gbps|
|**buyType**|Integer|False| |购买类型：1新购 3升级|
|**bw**|Integer|False| |业务带宽：单位Mbps|
|**carrier**|String|False| |线路：TELECOM为电信线路，UNICOM为联通线路，CMCC为移动线路|
|**ep**|Integer|False| |弹性带宽：单位Gbps|
|**name**|String|False| |实例名称|
|**returnUrl**|String|False| |支付成功后跳转的页面，控制台交互模式传该字段|
|**timeSpan**|Integer|False| |购买时长跨度|
|**timeUnit**|Integer|False| |购买时长单位：3月 4年|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String| |
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**orderId**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
