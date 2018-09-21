# **查询Top URL**

## **1、描述**

查询Top URL (queryTopUrl)

## **2、** **请求参数**

| **名称**   | **类型** | **是否必填** | **描述**                                                     |
| ---------- | -------- | ------------ | ------------------------------------------------------------ |
| username   | String   | 是           | 京东用户名pin                                                |
| signature  | String   | 是           | 用户签名                                                     |
| domain     | String   | 是           | 待查询的域名，支持多域名查询，参数示例“www.a.com,www.b.com”  |
| start_time | String   | 是           | 时间格式：yyyy-mm-dd hh:mi 参考示例：2016-12-14 07:00        |
| end_time   | String   | 否           | 不是必填参数，不传默认到当前时间                             |
| topfield   | String   | 是           | pv(请求数),flow(流量),bandwidth(带宽)                        |
| params     | String   | 否           | 是否带参数，true或者false，true表示带参数，false表示不带参数，不传就是不带参数 |
| pageNumber | int      | 否           | 查询分页页码，不传默认为1                                    |
| pageSize   | int      | 否           | 查询分页条数，不传默认100条                                  |


## **3、返回参数**

| **名称** | **描述** |
| -------- | -------- |
| status   | 结果状态 |
| msg      | 提示信息 |
| data     | 返回数据 |


## **4、调用示例**

- ### **请求地址**

http://opencdn.jcloud.com/api/queryTopUrl

- ### **请求示例**

```
http://opencdn.jcloud.com/api/queryTopUrl
{
    "username" :"test_user",
    "signature" :"1e28b8b4a1feddcacce74fa8b7131499",
    "domain":"www.a.com",
    "start_time":"2017-12-18 00:00",
    "end_time":"2017-12-18 23:59",
    "topfield":"pv",
    "params":"true"
   
 }
```

- ### **返回说明**

•        json格式

```
{
    "status": 0,
    "msg": "成功",
    "data": {
        "count": 6,
        "list": [
            {
                "rank": 1,
                "pvRatio": 0.38,
                "pv": 44155,
                "flow": 51446.52,
                "flowRatio": 57.58,
                "url": "www.a.com/no-cache/resource.ppt",
                "bandwidth": 131.25
            },
            {
                "rank": 2,
                "pvRatio": 0.23,
                "pv": 27337,
                "flow": 31841.6,
                "flowRatio": 35.64,
                "url": " www.a.com /cdn-mon/resource.ppt",
                "bandwidth": 71.98
            }
            ]
    }
}
```

- ### **返回示例**

•        json格式

```
 {
    "status": 0,
    "msg": "成功",
    "data": {
        "count": 6,
        "list": [
            {
                "rank": 1,
                "uv": 44191,
                "oridata": null,
                "pvRatio": 97.27,
                "pv": 12437657,
                "flow": 6121.59,
                "flowRatio": 5.33,
                "bandwidth": 6121.59,
                "url": "www.a.com/cdn-mon/monitor.html"
            },
            {
                "rank": 2,
                "uv": 153,
                "oridata": null,
                "pvRatio": 2,
                "pv": 256271,
                "flow": 146.04,
                "flowRatio": 0.13,
                "bandwidth": 6121.59,
                "url": "www.a.com/no-cache/monitor.html"
            },
            {
                "rank": 3,
                "uv": 4884,
                "oridata": null,
                "pvRatio": 0.36,
                "pv": 46620,
                "flow": 54321.06,
                "flowRatio": 47.32,
                "bandwidth": 6121.59,
                "url": "www.a.com/cdn-mon/resource.ppt"
            },
            {
                "rank": 4,
                "uv": 4875,
                "oridata": null,
                "pvRatio": 0.36,
                "pv": 46533,
                "flow": 54199.88,
                "flowRatio": 47.22,
                "bandwidth": 6121.59,
                "url": "www.a.com/no-cache/resource.ppt"
            },
            {
                "rank": 5,
                "uv": 5,
                "oridata": null,
                "pvRatio": 0,
                "pv": 7,
                "flow": 0.01,
                "flowRatio": 0,
                "bandwidth": 6121.59,
                "url": "www.a.com/"
            },
            {
                "rank": 6,
                "uv": 1,
                "oridata": null,
                "pvRatio": 0,
                "pv": 1,
                "flow": 0,
                "flowRatio": 0,
                "bandwidth": 6121.59,
                "url": "www.a.com/cdn-mon/monitor.jpg?Mon%20Dec%2018%202017%2000:08:48%20GMT+0800%20(CST)0.12802168394632263"
            }
        ]
    }
}
```
