# 查询域名带宽流量

## 1  描述

查询域名的流量带宽(bandwidth_flow)

## 2 请求参数

| **名称**   | **类型** | **是否必填** | **描述**                                                     |
| ---------- | -------- | ------------ | ------------------------------------------------------------ |
| username   | String   | 是           | 京东用户名pin                                                |
| signature  | String   | 是           | 用户签名，通过md5的方式校验用户的身份信息，保障信息安全。  md5=日期+username+秘钥SecretKey日期：格式为 yyyymmddusername：京东用户名pin秘钥：双方约定示例：比如当前日期2016-10-23，用户pin: jcloud_00 ,用户秘钥SecretKey   ：e7a31b1c5ea0efa9aa2f29c6559f7d61那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| domain     | String   | 是           | 查询的域名                                                   |
| start_time | String   | 是           | 时间格式：yyyy-mm-dd   hh:mi 参考示例：2016-12-14 07:00；    |
| end_time   | String   | 否           | 不是必填参数，不传默认到当前时间                             |

 

## 3 返回参数

| **名称**  | **描述**                                        |
| --------- | ----------------------------------------------- |
| status    | 表示接口请求成功与否，成功用0表示，其他表示失败 |
| msg       | 提示信息，如发送任务失败的原因等                |
| data      | 域名信息数组                                    |
| bandwidth | 带宽                                            |
| flow      | 流量                                            |

 

## 4 调用示例

- ### 请求地址

http://opencdn.jcloud.com/api/live/ bandwidth_flow

- ### 请求示例

* json格式

http://opencdn.jcloud.com/api/live/ bandwidth_flow
```
{
    "username" :" test_user ",
    "signature" :"f7e472560b470a8d1892ea57626390d6",
    "domain" :" play.live.com ",
    "start_time" :"2018-06-02 17:15,
    "end_time" :"2018-06-02  17:30"
}
```
- ### 返回示例
```
{
    "username" :" test_user ",
    "signature" :" f7e472560b470a8d1892ea57626390d6",
    "domain" :" play.live.com",
    "start_time" :"2018-06-02  17:15",
    "end_time" :"2018-06-02 17:30"
}
{
    "status": 0,
    "msg": "成功",
    "data": [
        {
            "2018-06-02 17:15": {
                " play.live.com ": {
                    "bandwidth": 6.1,
                    "flow": 228.88
                }
            }
        },
        {
            "2018-06-02 17:20": {
                " play.live.com ": {
                    "bandwidth": 122.07,
                    "flow": 4577.64
                }
            }
        },
        {
            "2018-06-02 17:25": {
                " play.live.com ": {
                    "bandwidth": 122.07,
                    "flow": 4577.64
                }
            }
        },
        {
            "2018-06-02 17:30": {
                " play.live.com ": {
                    "bandwidth": 115.97,
                    "flow": 4348.75
                }
            }
        }
    ]
}
```
