# **查询流列表**

## **1. 描述**

查询某段时间内流列表信息，包括推流开始结束时间、客户端IP、边缘节点IP等

## **2. 请求参数**

| **名称**   | **类型** | **是否必填** | **描述**                                                     |
| ---------- | -------- | ------------ | ------------------------------------------------------------ |
| username   | String   | 是           | 京东用户名pin                                                |
| signature  | String   | 是           |用户签名，通过md5的方式校验用户的身份信息，保障信息安全。</br>md5=日期+username+秘钥SecretKey; 日期：格式为 yyyymmdd; username：京东用户名pin; 秘钥：双方约定; </br>示例：比如当前日期2016-10-23,用户pin:jcloud_00,用户秘钥SecretKey：e7a31b1c5ea0efa9aa2f29c6559f7d61,那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61)|
| domain     | String   | 是           |查询的加速域名，只支持一个域名查询|
|app| String   | 否  |app名，不是必传项，如果按照流名过滤，则必传 |
|stream | String   | 否 | 流名，传空表示查询全部流名|
|startTime | String   | 是 | 推流开始时间格式：yyyy-MM-dd HH:mm |
|endTime | String   | 是| 推流结束时间格式：yyyy-MM-dd HH:mm  |
|pageNum | String   | 否 | 不传默认第一页	|
|pageSize| String   | 否  |分页大小，不传默认10条 |

## **3. 返回参数**

| **名称**   | **描述** | 
| ---------- | -------- |
| status| 表示接口请求成功与否，0表示成功，其他表示失败  | 
|msg |提示信息 | 
|data | 返回数据 | 
| domain| 查询域名  | 
|pushStreams | 流列表 | 
| app| 发布点名称 | 
|stream |流名 | 
| clientIp| 客户端IP|
| nodeIp| 边缘节点IP| 
| startTime| 推流开始时间，格式UTC时间 | 
|endTime| 推流结束时间，格式UTC时间| 

## **4. 调用示例**

- ### **请求地址**

https://opencdn.jcloud.com/api/live/queryPublishStream

- ### **请求示例**

```
{
  "username": "test_user",
  "signature": "03b10d0f0a8dd3bb9014ece6f8be72bc",
  "domain": "live.a.com",
  "startTime": "2019-05-17 00:00",
  "endTime": "2019-05-18 01:00"，
  "appName":"app_test1"
  "pageNum": 1,
  "pageSize": 10
}

```

- ### **返回示例**

```
{
    "status": 0,
    "msg": "",
    "data": {
        "domain": "live.a.com",
        "total": 2,
        "pushStreams": [
            {
                "stream": "test1",
                "clientIp": "10.226.143.204",
                "nodeIp": "",
                "startTime": "2019-05-17T09:05:15Z",
                "endTime": "2019-05-17T09:15:12Z",
                "duration": 597
            },
            {
                "stream": "test2",
                "clientIp": "10.226.143.204",
                "nodeIp": "",
                "startTime": "2019-05-17T09:05:15Z",
                "endTime": "2019-05-17T09:15:12Z",
                "duration": 597
            }
        ]
    }
}

```
