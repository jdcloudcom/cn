# queryLiveDomainDetail


## 描述
查询直播域名详情

## 请求方式
GET

## 请求地址
https://cdn.jdcloud-api.com/v1/liveDomain/{domain}

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domain**|String|True| |用户域名|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String| |

### Result
|名称|类型|描述|
|---|---|---|
|**domainType**|String|域名类型|
|**playDomain**|String|播放域名|
|**publishDomain**|String|推流域名|
|**originDomain**|String|回源域名|
|**createdTime**|String|创建时间|
|**cname**|String|cname|
|**siteType**|String|站点类型推流push，拉流pull|
|**status**|String|域名状态|
|**source**|BackSourceInfo|回源信息|
|**sourceType**|String|域名回源类型|
|**backSourceType**|String|回源类型目前只能未rtmp|
|**videoType**|String|视频格式 H.264|
|**audioType**|String|音频格式AAC|
|**type**|String|域名类型|
|**defaultSourceHost**|String|默认回源host|
|**archiveNo**|String|备案号|
|**rtmpDomain**|String|rtmpDomain|
|**rtmpCname**|String|rtmpCname|
|**hdlDomain**|String|hdlDomain|
|**hdlCname**|String|hdlCname|
|**hlsDomain**|String|hlsDomain|
|**hlsCname**|String|hlsCname|
|**forwardCustomVhost**|String|forwardCustomVhost|
|**flvUrls**|String[]|flvUrls|
|**hlsUrls**|String[]|hlsUrls|
|**rtmpUrls**|String[]|rtmpUrls|
|**protocolConverts**|ProtocolConvert[]|转协议|
|**certificate**|String|https证书|
|**rsaKey**|String|https私钥|
|**accesskeyType**|Integer|url鉴权开关|
|**accesskeyKey**|String|url鉴权key|
|**playAuthLifeTime**|Integer|playAuthLifeTime|
|**authLifeTime**|Integer|authLifeTime|
|**forwardAccessKeyType**|Integer|转推鉴权开关|
|**forwardPrivateKey**|String|转推鉴权key|
|**originAccessKeyType**|Integer|回源鉴权开关|
|**originPrivateKey**|String|回源鉴权key|
|**allowApps**|String[]|app列表|
|**ips**|String[]|ip黑名单列表|
|**blackIpsEnable**|String|是否开启ip黑名单|
|**externId**|String|外部关联id|
|**ignoreQueryString**|String|ignoreQueryString|
|**referType**|String|referType|
|**referList**|String[]|referList|
|**allowNoReferHeader**|String|允许无refer|
|**allowNullReferHeader**|String|允许空refer|
|**pushWhiteIps**|Arrary|推流IP白名单|
|**publishNormalTimeout**|String|推流中断超时时间(单位秒)|
|**notifyCustomUrl**|String|推断流通知Url|
|**notifyCustomAuthKey**|String|推断流通知key|
|**certFrom**|String|证书来源有两种类型：default,ssl|
|**sslCertId**|String|ssl证书id|
|**certName**|String|证书名称|
|**certType**|String|证书类型|
|**sslCertStartTime**|String| |
|**sslCertEndTime**|String| |
### ProtocolConvert
|名称|类型|描述|
|---|---|---|
|**sourceProtocol**|String|源协议,目前只能为rtmp|
|**targetProtocol**|String|目标协议|
### BackSourceInfo
|名称|类型|描述|
|---|---|---|
|**ips**|IpSourceInfo[]| |
|**domain**|DomainSourceInfo[]| |
|**ossSource**|String| |
### DomainSourceInfo
|名称|类型|描述|
|---|---|---|
|**priority**|Integer| |
|**sourceHost**|String| |
|**domain**|String| |
### IpSourceInfo
|名称|类型|描述|
|---|---|---|
|**master**|Integer| |
|**ip**|String| |
|**ratio**|Double| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**404**|NOT_FOUND|
