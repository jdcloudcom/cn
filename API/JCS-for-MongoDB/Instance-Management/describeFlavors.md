# describeFlavors


## 描述
获取规格

## 请求方式
GET

## 请求地址
https://mongodb.jdcloud-api.com/v1/regions/{regionId}/flavors

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |Region ID|

## 请求参数
无


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |

### Result
|名称|类型|描述|
|---|---|---|
|**flavors**|Flavor[]| |
### Flavor
|名称|类型|描述|
|---|---|---|
|**cpu**|Integer|CPU核数|
|**diskStep**|Integer|磁盘步长|
|**iops**|Integer|iops|
|**maxDisk**|Integer|最大磁盘数,单位GB|
|**maxLink**|Integer|最大连接数|
|**memory**|Integer|内存 ,单位GB|
|**minDisk**|Integer|最下磁盘数,单位GB|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
