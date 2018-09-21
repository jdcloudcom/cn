# 查询推流实时帧率码率参数

## 1 描述

查询推流域名下某路流的实时（一分钟粒度）码率、帧率信息(queryStreamData)

## 2 请求参数

| **名称**   | **类型** | **是否必填** | **描述**                                                     |
| ---------- | -------- | ------------ | ------------------------------------------------------------ |
| username   | String   | 是           | 京东用户名pin                                                |
| signature  | String   | 是           | 用户签名，通过md5的方式校验用户的身份信息，保障信息安全。  md5=日期+username+秘钥SecretKey日期：格式为 yyyymmddusername：京东用户名pin秘钥：双方约定示例：比如当前日期2016-10-23，用户pin: jcloud_00 ,用户秘钥SecretKey   ：e7a31b1c5ea0efa9aa2f29c6559f7d61那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| domain     | String   | 是           | 目前只支持单个推流域名查询，参数示例“publish.jcloud.com”     |
| app        | String   | 是           | 目前只支持单个app的查询，不支持多个app同时查询               |
| stream     | String   | 是           | 目前只支持单路流的查询，暂不支持多路流同时查询               |
| start_time | String   | 否           | 时间格式：yyyy-mm-dd   hh:mi 参考示例：2016-12-14 07:00； 不传开始时间，默认为查询时间为最近一小时 |
| end_time   | String   | 否           | 不是必填参数，不传默认到当前时间                             |

 

## 3 返回参数

| **名称** | **描述**                                        |
| -------- | ----------------------------------------------- |
| status   | 表示接口请求成功与否，成功用0表示，其他表示失败 |
| msg      | 提示信息，如发送任务失败的原因等                |
| data     | 域名信息数组                                    |

 

## 4  调用示例

- ### 请求地址

http://opencdn.jcloud.com/api/live/queryStreamData

- ### 请求示例

•        json格式

http://opencdn.jcloud.com/api/live/queryStreamData
```
{
    "username" :"test_user",
    "signature" :"3a4eb9fc81c548bf6f2fea1b2b85f1df",
    "domain":"www.a.com",
    "start_time":"2018-05-16 16:56",
    "end_time":"2018-05-16 16:58",
    "app":"live",
    "stream":"test"
 }
```

- ### 返回参数说明

•        json格式
```
{
    "status": 0,
    "msg": "成功",
    "data": {
        "domain": "DOMAIN",//域名
        "app": "APP",//APP名
        "starttime": "2018-05-16 16:56",
        "endtime": "2018-05-16 16:58",
        "data": [
            {
                "2018-05-16 16:57": {//时间
                    "steam1": {//流
                        "bit_rate": BIT_RATE,//实时码率单位kbps
                        "frame_rate": FRAME_RATE//实时帧率
                    }
                }
            },
            {
                "2018-05-16 16:58": {//时间
                    "stream1": {//流
                        "bit_rate": BIT_RATE,//实时码率单位kbps
                        "frame_rate": FRAME_RATE//实时帧率
                    }
                }
            },
     ]
    }
   }
```

- ### 返回示例

•        json格式
```
{
    "status": 0,
    "msg": "成功",
    "data": {
        "domain": " www.a.com ",
        "app": "live",
        "starttime": "2018-05-16 16:56",
        "endtime": "2018-05-16 16:58",
        "data": [
            {
                "2018-05-16 16:57": {
                    "test": {
                        "bit_rate": 406,
                        "frame_rate": 25
                    }
                }
            },
            {
                "2018-05-16 16:58": {
                    "test": {
                        "bit_rate": 512,
                        "frame_rate":30
                    }
                }
            }
        ]
    }
}
```
