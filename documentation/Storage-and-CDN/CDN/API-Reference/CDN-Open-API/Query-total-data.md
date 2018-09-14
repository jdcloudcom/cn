# **查询总数据**

## **1、描述**

查询总数据 (total_data)

## **2、请求参数**

| **名称**   | **类型** | **是否必填** | **描述**                                                     |
| ---------- | -------- | ------------ | ------------------------------------------------------------ |
| username   | String   | 是           | 京东用户名pin                                                |
| signature  | String   | 是           | 用户签名，通过md5的方式校验用户的身份信息，保障信息安全。  md5=日期+username+秘钥SecretKey日期：格式为 yyyymmddusername：京东用户名pin秘钥：双方约定示例：比如当前日期2016-10-23，用户pin: jcloud_00 ,用户秘钥SecretKey   ：e7a31b1c5ea0efa9aa2f29c6559f7d61那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| domain     | String   | 是           | 待查询的域名,多个域名使用逗号分隔，参数示例“www.a.com,www.b.com” |
| start_time | String   | 是           | 时间格式：yyyy-mm-dd hh:mi 参考示例：2016-12-14 07:00        |
| end_time   | String   | 否           | 不是必填参数，不传默认到当前时间                             |

## 

## **3、返回参数data中说明**

| **名称** | **描述**                       |
| -------- | ------------------------------ |
| status   | 结果状态 0，刷新成功，其他失败 |
| msg      | 提示信息                       |
| data     | 返回数据                       |

## 

## **4、调用示例**

- ### **请求地址**

http://opencdn.jcloud.com/api/total_data

- ### **请求示例**

```
http://opencdn.jcloud.com/api/total_data
{
    "username" :"test_user",
    "signature" :"dbc1c1302d0a1baa48a256cbfc840317",
    "domain":"www.a.com,www.b.com",
    "start_time":"2017-12-18 00:00",
    "end_time":"2017-12-18 23:59"
   
 }
```

- ### **返回说明**

•        json格式

```
{
    "status": 0,//0 表示本次请求成功
    "msg": "成功",
    "data": {
        "domian": "www.a.com,www.b.com",
        "data": {
            "oriflow": 19685.6,//回源流量, MB
            "hitflow": 57683.25,//命中流量, MB
            "oripvPercent": 0,//回源pv占比,%
            "oribandwidth": 5.78,//回源带宽，Mbps
            "oriflowPercent": 18,//回源流量占比，%
            "hitpv": 7454903,//命中pv
            "toptime": "2017-12-18 18:20:00",//峰值带宽时间点
            "pv": 8535492,//pv
            "uv": 300102,//uv
            "flow": 112124.61,//流量, MB
            "oripv": 0,//回源pv
            "bandwidth": 13.84//带宽, Mbps
        }
    }
}
```

- ### **返回示例**

```
{
    "status": 0,
    "msg": "成功",
    "data": {
        "domian": "www.a.com,www.b.com",
        "data": {
            "oriflow": 19685.6,
            "hitflow": 57683.25,
            "oripvPercent": 0,
            "oribandwidth": 5.78,
            "oriflowPercent": 18,
            "hitpv": 7454903,
            "toptime": "2017-12-18 18:20:00",
            "pv": 8535492,
        "uv": 300102,
            "flow": 112124.61,
            "oripv": 0,
            "bandwidth": 13.84
        }
    }
}
```