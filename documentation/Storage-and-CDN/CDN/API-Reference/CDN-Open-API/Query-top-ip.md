# **查询Top IP**

## **1、描述**

查询Top IP (queryTopIP)

## **2、请求参数**

| **名称**   | **类型** | **是否必填** | **描述**                                                    |
| ---------- | -------- | ------------ | ----------------------------------------------------------- |
| username   | String   | 是           | 京东用户名pin                                               |
| signature  | String   | 是           | 用户签名                                                    |
| domain     | String   | 是           | 待查询的域名，支持多域名查询，参数示例“www.a.com,www.b.com” |
| start_time | String   | 是           | 时间格式：yyyy-mm-dd hh:mi 参考示例：2016-12-14 07:00       |
| end_time   | String   | 否           | 不是必填参数，不传默认到当前时间                            |
| topfield   | String   | 是           | top查询的字段，只能传pv或者flow。 pv(请求数),flow(流量)     |
| pageNumber | int      | 否           | 查询分页页码，不传默认为1                                   |
| pageSize   | int      | 否           | 查询分页条数，不传默认100条                                 |

 

## **3、返回参数**

| **名称** | **描述** |
| -------- | -------- |
| status   | 结果状态 |
| msg      | 提示信息 |
| data     | 返回数据 |

## 

## **4、调用示例**

- ### **请求地址**

http://opencdn.jcloud.com/api/queryTopIP

- ### **请求示例**

```
http://opencdn.jcloud.com/api/queryTopIP
{
    "username" :"test_user",
    "signature" :"1e28b8b4a1feddcacce74fa8b7131499",
    "domain":"www.a.com",
    "start_time":"2017-12-18 00:00",
    "end_time":"2017-12-18 23:59",
    "topfield":"pv"
   
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
                "rank": 1,//top排名
                "pv": 12437657,//pv
                "flow": 6121.59,//流量
                "ip": "120.11.23.12"//TOPIP值
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
        "count": 3,
        "list": [
            {
                "rank": 1,
                "pv": 12437657,
                "flow": 6121.59,
                "ip": "1.1.1.1"
            },
            {
                "rank": 2,
                "pv": 256271,
                "flow": 146.04,
                "ip": "2.2.2.2"
            },
            {
                "rank": 3,
                "pv": 46620,
                "flow": 54321.06,
                "ip": "3.3.3.3"
            }
        ]
    }
}
```