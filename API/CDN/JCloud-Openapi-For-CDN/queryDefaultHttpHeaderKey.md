# queryDefaultHttpHeaderKey


## 描述
查询默认http header头部参数列表

## 请求方式
GET

## 请求地址
https://cdn.jdcloud-api.com/v1/defaultHttpHeaderKey


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
|**reqDefaultHttpHeaderKey**|String[]|默认的http请求头|
|**respDefaultHttpHeaderKey**|String[]|默认的http响应头|

## 返回码
|返回码|描述|
|---|---|
|**200**||
|**404**|NOT_FOUND|
