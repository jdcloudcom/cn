# queryAreaIspList


## 描述
查找地域运营商列表

## 请求方式
GET

## 请求地址
https://cdn.jdcloud-api.com/v1/console:areaIspList


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
|**mainLand**|AreaIspItem[]| |
|**overseas**|AreaIspItem[]| |
|**isp**|AreaIspItem[]| |
### AreaIspItem
|名称|类型|描述|
|---|---|---|
|**description**|String| |
|**code**|String| |

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
