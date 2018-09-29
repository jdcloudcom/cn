# describeInstance


## 描述
查询实例

## 请求方式
GET

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceId**|String|True| |实例 ID|
|**regionId**|String|True| |Region ID|

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
|**data**|Instance| |
### Instance
|名称|类型|描述|
|---|---|---|
|**abovePeakCount**|Integer|超峰次数|
|**businessBitslimit**|Integer|业务带宽大小|
|**carrier**|String|线路，UNICOM、TELECOM|
|**ccProtectMode**|Integer|cc防护模式，0正常、1紧急、2宽松、3自定义|
|**ccProtectStatus**|Integer|cc开关状态，0关闭，1开启|
|**ccSpeedLimit**|Integer|cc防护模式为自定义时的限速大小|
|**ccSpeedPeriod**|Integer|cc防护模式为自定义时的限速周期|
|**ccThreshold**|Integer|cc阈值大小|
|**chargeStatus**|String|PAID|ARREARS|EXPIRED|
|**createTime**|Integer|实例的创建的时间|
|**elasticTriggerCount**|Integer|触发弹性带宽的次数|
|**expireTime**|Integer|实例的过期时间|
|**hostQps**|Integer|ccProtectMode为自定义模式时，每个Host的防护阈值|
|**hostUrlQps**|Integer|ccProtectMode为自定义模式时，每个Host+URI的防护阈值|
|**inBitslimit**|Integer|保底带宽|
|**instanceId**|Integer|实例id|
|**ipBlackList**|String[]|ip黑名单列表|
|**ipBlackStatus**|Integer|ip黑名单状态，0关闭，1开启|
|**ipHostQps**|Integer|ccProtectMode为自定义模式时，每个源IP对Host的防护阈值|
|**ipHostUrlQps**|Integer|ccProtectMode为自定义模式时，每个源IP对Host+URI的防护阈值|
|**ipWhiteList**|String[]|ip白名单列表|
|**ipWhiteStatus**|Integer|ip白名单状态，0关闭，1开启|
|**name**|String|实例名称|
|**pin**|String|用户pin|
|**resilientBitslimit**|Integer|弹性带宽|
|**resourceId**|String|资源id，升级和续费时使用|
|**ruleCount**|Integer|非网站类规则数|
|**securityStatus**|String|SAFE|CLEANING|BLOCKING|
|**urlWhitelist**|String[]|url白名单列表|
|**urlWhitelistStatus**|Integer|url白名单状态，0关闭，1开启|
|**webRuleCount**|Integer|网站类规则数|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
