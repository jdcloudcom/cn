## 上报监控数据
自定义监控功能为您提供上报监控数据的接口，方便您将自己采集的时序数据上报到云监控。目前支持OpenAPI的方式进行上报，可上报原始数据和已聚合的统计数据。

### 上报接口描述

1. 接口名称：putMetricData

2. 公网域名：

地域 | 域名
---|---
华北-北京 |monitor.cn-north-1.jdcloud-api.com
华南-广州 |monitor.cn-south-1.jdcloud-api.com
华东-宿迁 |monitor.cn-east-1.jdcloud-api.com
华东-上海 |monitor.cn-east-2.jdcloud-api.com

3. 支持批量上报方式。单次请求最多包含 50 个数据点；数据大小不超过 256k。

注：OpenAPI入门使用请参看<a href="http://docs.jdcloud.com/cn/common-declaration/api/introduction">公共说明</a>

### 请求方式

POST   https://{公网域名}/v1/customMetrics

例如： POST    https://monitor.cn-north-1.jdcloud-api.com/v1/customMetrics

### 请求参数

名称 | 类型 | 是否必选 | 描述
---|---|---|---
metricDataList|	MetricDataCm[] |	False |	数据参数   

### MetricDataCm

名称 | 类型 | 是否必选 | 描述
---|---|---|---
dimensions|Object |True|数据维度，数据类型为map类型，支持最少一个，最多五个标签，总长度不大于255字节，只允许英文、数字、下划线_、点., [0-9][a-z] [A-Z] [. _ ]，  其它会返回err
metric|	String |True |	监控指标名称，长度不超过255字节，只允许英文、数字、下划线_、点.,  [0-9][a-z] [A-Z] [. _ ]， 其它会返回err               
namespace |	String|	True|命名空间 ，长度不超过255字节，只允许英文、数字、下划线_、点., [0-9][a-z] [A-Z] [. _ ]，  其它会返回err               
timestamp|Integer|True|上报数据点的时间戳,只支持10位，秒级时间戳，不能写入过去30天的时间                              
type |Integer|True |数据上报类型，1为原始值，2为聚合数据。当上报聚合数据时，建议为60s的周期时行上报、否则无法正常查询                           
values |	Object |	True |指标值集合，数据类型必须为map类型，key为数据类型，value为数据值，当type=1时，key只能为”value”，上报的是原始值，当type=2时，K的值可以为"avg","sum","last","max","min","count"，只支持以上类型，否则会报错，value内容为整型或浮点型数字，最大值为9223372036854775807，count只支持>=0的数  

### 返回参数  

名称 | 类型 | 是否必选 
---|---|---
error |Object| 错误信息 。     
requestId|String |请求的标识id                        
result |Result |                
                      
### Result
名称 | 类型 | 是否必选 
---|---|---
errMetricDataList|MetricDataList[]|
success|Boolean  |全部写入成功为true，否则为false   

### MetricDataList
名称 | 类型 | 是否必选 
---|---|---
errDetail|string	| 错误数据描述
errMetricData |string |错误数据              

### 返回码  
名称 | 类型 
---|---
200	|OK
400	|invalid parameter
500 |internal server error
429	|quota exceed


### 示例代码

请求示例
```
[
        {
            "namespace":"test",
            "metric":"vm.mem.usage1",
            "tags":{
                "host":"1.2.3.23",
                "datacenter":"cn-north-1 "
            },
             "timestamp":15305424971,
             "type":1,
             "values":{
             "value":"12342213"        
            }
        },

        {
            "namespace":"test1",
            "metric":"vm.cpu.usage",
            "dimensions":{
                "host":"1.2.3.19",
                "tag":"bj "
            },
             "timestamp":1530542497,
             "type":2,
             "values":{
             "avg":"80",
             "max":"32424244120"
            }
        }
]
```

#### 返回示例

```
success：

{
    "requestId": "1111",
    "result": {
        "success": true,
        "metricDataList": []
    }
}
fail：
{
   "requestId": "1111",
    "result": {
        "success": false,
        "metricDataList": [
            {
                "data": {
                    "namespace": "test",
                    "metric": "vm.mem.usage1",
                    "dimensions": {
                        "host": "1.2.3.23",
                        "tag": "cn-north-1"
                    },
                    "timestamp": 15305424971,
                    "type": 1,
                    "values": {
                        "value": "12342213"
                    }
                },
                "errDetail": "Time value only allowed Secondtimestamps,length is 10"
            }
        ]
    },
    "error": {
        "code": 400,
        "message": "INVALID_ARGUMENT",
        "status": "INVALID_ARGUMENT",
        "details": null
    }
}
```
