# describeInstanceClass

描述:查询某区域下的实例规格列表

- 请求方式
```xml
GET https://redis.jdcloud-api.com/v1/regions/{regionId}/instanceClass
```
名称|类型|是否必需|默认值|描述
---|:--:|:--:|:--:|---:
regionId|String|True||缓存Redis实例所在区域的Region ID。目前缓存Redis有华北、华南、华东区域，对应Region ID为cn-north-1、cn-south-1、cn-east-2

- 请求参数<br>
无


- 返回参数

名称|类型|描述
---|:--:|---:
requestId|String|
result|Result

- Result

名称|类型|描述
---|:--:|---:
instanceClasses|InstanceClass[]|
totalCount|Integer

- InstanceClass

名称|类型|描述
---|:--:|---:
bandwidthMbps|Integer|带宽
cpu|Integer|cpu
diskGB|Integer|磁盘
instanceClass|String|实例规格代码,参见实例规格代码表
maxConnetction|Integer|最大链接数
memoryMB|Integer|内存

- 错误码

错误码|描述
---|---:
200|OK
