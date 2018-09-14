# deleteCacheInstance

描述:删除单个缓存Redis实例

- 请求方式
```xml
DELETE https://redis.jdcloud-api.com/v1/regions/{regionId}/cacheInstance/{cacheInstanceId}
```

名称|类型|是否必需|默认值|描述
---|:--:|:--:|:--:|---:
cacheInstanceId|String|True||缓存Redis实例ID
regionId|String|True||缓存Redis实例所在区域的Region ID。目前缓存Redis有华北、华南、华东区域，对应Region ID为cn-north-1、cn-south-1、cn-east-2

- 请求参数<br>
无

- 返回参数

名称|类型|描述
---|:--:|---:
requestId|String|

- 错误码

错误码|描述
---|---:
200|OK
