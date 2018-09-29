# **回源带宽统计**

## **1、描述**

回源带宽统计接口 (origin_ratio)

## **2、请求参数**

| **名称**   | **类型** | **是否必填** | **描述**                                                     |
| ---------- | -------- | ------------ | ------------------------------------------------------------ |
| username   | String   | 是           | 京东用户名pin                                                |
| signature  | String   | 是           | 用户签名，通过md5的方式校验用户的身份信息，保障信息安全。  md5=日期+username+秘钥SecretKey日期：格式为 yyyymmddusername：京东用户名pin秘钥：双方约定示例：比如当前日期2016-10-23，用户pin: jcloud_00 ,用户秘钥SecretKey   ：e7a31b1c5ea0efa9aa2f29c6559f7d61那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| domain     | String   | 是           | 待查询的域名，支持多域名查询，参数示例“www.a.com,www.b.com”  |
| start_time | String   | 是           | 时间格式：yyyy-mm-dd hh:mi 参考示例：2016-12-14 07:00        |
| end_time   | String   | 否           | 不是必填参数，不传默认到当前时间                             |


## **3、返回参数data中说明**

| **名称** | **描述**                       |
| -------- | ------------------------------ |
| status   | 结果状态 0，刷新成功，其他失败 |
| msg      | 提示信息                       |
| data     | 返回数据                       |


## **4、调用示例**

- ### **请求地址**

http://opencdn.jcloud.com/api/origin_ratio

- ### **请求示例**

```
http://opencdn.jcloud.com/api/origin_ratio
{
    "username" :"test_user",
    "signature" :"d847267fc702273abf394dd0c3128d64",
    "domain" :"www.a.com,www.b.com",
    "start_time" :"2016-12-14 07:00",
    "end_time" :"2016-12-14 12:59"
 }
```

- ### **返回说明**

  ### •        json格式

```
{
"status": 0,//0 表示本次请求成功
"data": [
{
"domain": "DOMAIN",//查询的域名, 不要包含 http://
"data": [
{
"time":TS,//时间戳
"bandwidth":BANDWIDTH,//带宽, Mbps
"originBandwidth":ORIGINBANDWIDTH,//回源带宽, Mbps
"originRatio":ORIGINRATIO,//占比，百分比，计算公式 (回源带宽/总带宽)*100
},
],
},
]
}
```

- ### **返回示例**

```
{
    "status": 0,
    "msg": "成功",
    "data": [
        {
            "domain": "www.a.com",
            "data": [
                {
                    "time": 1513540200,
                    "originRatio": 23.62,
                    "originBandwidth": 1.53,
                    "bandwidth": 6.46
                },  
{
                    "time": 1513588500,
                    "originRatio": 6,
                    "originBandwidth": 0.81,
                    "bandwidth": 13.5
                }
            ]
        }
    ]
}
```
