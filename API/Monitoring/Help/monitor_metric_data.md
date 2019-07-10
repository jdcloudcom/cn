注：OpenAPI入门使用请参看[公共说明](http://docs.jdcloud.com/cn/common-declaration/api/introduction)

### 1. describeMetrics

**根据产品线查询可用监控项列表**

示例请求

```json
https://monitor.jdcloud-api.com/v1/metrics?serviceCode=vm
```

返回

```
{
    "requestId": "3f1f6026-216b-4ced-8249-12aa6acc3773",
    "result": {
        "metrics": [
            {
                "calculateUnit": "%",
                "metric": "memory.usage",
                "metricName": "内存使用率",
                "serviceCode": "vm",
                "downSample": ""
            },
            {
                "calculateUnit": "%",
                "metric": "cpu_util",
                "metricName": "CPU使用率",
                "serviceCode": "vm",
                "downSample": ""
            },
            {
                "calculateUnit": "Bps",
                "metric": "vm.disk.bytes.read",
                "metricName": "磁盘读吞吐量",
                "serviceCode": "vm",
                "downSample": ""
            },
            {
                "calculateUnit": "Bps",
                "metric": "vm.disk.bytes.write",
                "metricName": "磁盘写吞吐量",
                "serviceCode": "vm",
                "downSample": ""
            },
            {
                "calculateUnit": "bps",
                "metric": "vm.network.bytes.incoming",
                "metricName": "网络入速率",
                "serviceCode": "vm",
                "downSample": ""
            },
            {
                "calculateUnit": "bps",
                "metric": "vm.network.bytes.outgoing",
                "metricName": "网络出速率",
                "serviceCode": "vm",
                "downSample": ""
            }
        ]
    }
}
```

### 2. describeMetricData

**查看某资源单个监控项数据**

示例请求

```json
https://monitor.jdcloud-api.com/v1/regions/cn-north-1/metrics/memory.usage/metricData?timeInterval=1h&serviceCode=vm&resourceId=i-test01&tags.1.key=role&tags.1.values.1=M
```

返回

```json
{
    "requestId": "4b2d2495-33d4-4b44-a0c1-a9deb31370a1",
    "result": {
        "metricDatas": [
            {
                "data": [
                    {
                        "timestamp": 1562723040000,
                        "value": "4.1667"
                    },
                    {
                        "timestamp": 1562723100000,
                        "value": "4.0000"
                    },
                               .......
                               .......
                               .......
                    {
                        "timestamp": 1562726460000,
                        "value": "4.0000"
                    },
                    {
                        "timestamp": 1562726520000,
                        "value": "4.0000"
                    },
                    {
                        "timestamp": 1562726580000,
                        "value": "4.0000"
                    }
                ],
                "tags": [
                    {
                        "tagKey": "dataCenter",
                        "tagValue": "bj_02"
                    },
                    {
                        "tagKey": "hostname",
                        "tagValue": "A01-TEST.JCLOUD.COM"
                    },
                    {
                        "tagKey": "project_id",
                        "tagValue": "123456789"
                    },
                    {
                        "tagKey": "resourceId",
                        "tagValue": "i-test01"
                    },
                    {
                        "tagKey": "serviceCode",
                        "tagValue": "vm"
                    },
                    {
                        "tagKey": "az",
                        "tagValue": "prod_bj03"
                    }
                ],
                "metric": {
                    "calculateUnit": "%",
                    "metric": "memory.usage",
                    "metricName": "内存使用率",
                    "aggregator": "avg",
                    "period": "1min"
                }
            }
        ]
    }
}
```

### 3. lastDownsample

**查看某资源的最后一个监控数据点**

请求示例

```json
https://monitor.jdcloud-api.com/v1/regions/cn-north-1/metrics/memory.usage/lastDownsample?timeInterval=1h&serviceCode=vm&resourceId=i-test01
```

返回

```json
{
    "requestId": "345b7934-f178-46a2-bfc8-786e8af363fb",
    "result": {
        "items": [
            {
                "metric": "memory.usage",
                "name": "i-test01",
                "value": 4
            }
        ]
    }
}
```

