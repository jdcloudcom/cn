注：OpenAPI入门使用请参看[公共说明](http://docs.jdcloud.com/cn/common-declaration/api/introduction)

### 1.describeMetricsForCreateAlarm

**查询可用于创建监控报警规则的指标列表** 	

示例请求

```
https://monitor.jdcloud-api.com/v1/metricsForCreateAlarm?serviceCode=vm
```

返回

```
{
    "requestId": "11111",
    "result": {
        "serviceCodeList": [
            {
                "serviceCode": "vm",
                "metrics": [
                    {
                        "calculateUnit": "%",
                        "metric": "cpu_util",
                        "metricName": "CPU使用率",
                        "serviceCode": "vm",
                        "downSample": ""
                    },
                    {
                        "calculateUnit": "%",
                        "metric": "memory.usage",
                        "metricName": "内存使用率",
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
        ]
    }
}
```

### 2. createAlarm

**创建报警规则**

示例请求

```
https://monitor.jdcloud-api.com/v1/regions/cn-north-1/alarms
```


参数

```
{
    "clientToken": "vm-1562675527",
    "createAlarmSpec": {
        "calculateUnit": "%",
        "calculation": "avg",
        "contactGroups": [
            "123"
        ],
        "contactPersons": [
            "456"
        ],
        "downSample": "",
        "metric": "cpu_util",
        "noticeLevel": {
            "custom": true,
            "levels": {
                "common": 10,
                "critical": 50,
                "fatal": 70
            }
        },
        "noticePeriod": 3,
        "operation": "gt",
        "period": 2,
        "resourceIds": [
            "i_test01"
        ],
        "serviceCode": "vm",
        "tags": {},
        "threshold": 10,
        "times": 1,
        "webHookUrl": "https://www.jd.com",
        "webHookContent": "{\"content\":\"123\"}",
        "webHookSecret": "123456789012345678901234",
        "webHookProtocol": "https"
    }
}
```


返回

```
{
    "requestId": "b95ad29e-4c73-4654-a720-41ac35e5ef21",
    "result": {
        "alarmIDList": [
            "alarm-fczoaanast"
        ]
    }
}
```

### 3. deleteAlarms

**批量删除规则**

示例请求

```
https://monitor.jdcloud-api.com/v1/regions/cn-north-1/alarms
```

参数

```
{
	"ids":"alarm-fczoaanast|alarm-46o8wi1tjw"
}
```

返回

```
{
    "requestId": "1111"
}
```

### 4. updateAlarm

**修改已创建的报警规则**

示例请求

```
https://monitor.jdcloud-api.com/v1/regions/cn-north-1/alarms/alarm-fczoaanast
```

参数

```
{
    "rule": {
        "metric": "memory.usage",
        "calculateUnit": "%",
        "calculation": "avg",
        "downSample": "",
        "operation": "gt",
        "threshold": 20,
        "tags": {},
        "times": 1,
        "period": 2,
        "noticePeriod": 3,
        "noticeLevel": {
            "custom": true,
            "levels": {
                "common": 20,
                "critical": 50,
                "fatal": 70
            }
        }
    },
    "contacts": [
        {
            "referenceId": 34,
            "referenceType": 1
        }
    ],
    "webHookUrl": "https://www.jd.com",
    "webHookContent": "{\"content\":\"123\"}",
    "webHookSecret": "123456789012345678901234",
    "webHookProtocol": "https"
}
```

返回

```
{
    "requestId": "b95ad29e-4c73-4654-a720-41ac35e5ef21",
    "result": {
        "alarmIDList": [
            "alarm-fczoawasds"
        ]
    }
}
```

### 5. describeAlarms

查询规则

示例请求

```
https://monitor.jdcloud-api.com/v1/regions/cn-north-1/alarms
```

返回

```
{
    "requestId": "7ebd0e7f-b7ce-45e7-a6c8-ed2e2fc06c70",
    "result": {
        "alarmList": [
            {
                "id": "alarm-jfws97535q",
                "metric": "cpu_util",
                "metricName": "cpu使用率",
                "resourceId": "i-test01",
                "region": "cn-north-1",
                "serviceCode": "vm",
                "period": 1,
                "calculation": "max",
                "operation": "gt",
                "threshold": 30,
                "times": 1,
                "noticePeriod": 1,
                "noticeLevel": {
                    "levels": {
                        "common": 30
                    },
                    "custom": false
                },
                "downSample": "",
                "enabled": 1,
                "status": 4,
                "createTime": "2019-06-24T17:26:45+08:00",
                "tags": {},
                "calculateUnit": "%",
                "webHookUrl": "",
                "webHookContent": "",
                "webHookSecret": "",
                "webHookProtocol": ""
            }
        ],
        "total": 1
    }
}
```

