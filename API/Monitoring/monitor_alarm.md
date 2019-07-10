注：OpenAPI入门使用请参看[公共说明](http://docs.jdcloud.com/cn/common-declaration/api/introduction)

### 1. createAlarm

**创建报警规则**

示例请求

```go
https://monitor.jdcloud-api.com/v1/regions/cn-north-1/alarms
```


参数

```json
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
            "mysqltag_2"
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

```json
{
    "requestId": "b95ad29e-4c73-4654-a720-41ac35e5ef21",
    "result": {
        "alarmIDList": [
            "alarm-fczoaanast"
        ]
    }
}
```

### 2. deleteAlarms

**批量删除规则**

示例请求

```json
https://monitor.jdcloud-api.com/v1/regions/cn-north-1/alarms
```

参数

```json
{
	"ids":"alarm-fczoaanast|alarm-46o8wi1tjw"
}
```

返回

```json
{
    "requestId": "1111"
}
```

### 3. updateAlarm

**修改已创建的报警规则**

示例请求

```json
https://monitor.jdcloud-api.com/v1/regions/cn-north-1/alarms/alarm-fczoaanast
```

参数

```json
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

```json
{
    "requestId": "b95ad29e-4c73-4654-a720-41ac35e5ef21",
    "result": {
        "alarmIDList": [
            "alarm-fczoawasds"
        ]
    }
}
```

### 4. describeAlarms

查询规则

示例请求

```json
https://monitor.jdcloud-api.com/v1/regions/cn-north-1/alarms
```

返回

```json
{
    "requestId": "7ebd0e7f-b7ce-45e7-a6c8-ed2e2fc06c70",
    "result": {
        "alarmList": [
            {
                "id": "alarm-jfws97535q",
                "metric": "cpu_util",
                "metricName": "cpu使用率",
                "resourceId": "i-asdasd",
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

