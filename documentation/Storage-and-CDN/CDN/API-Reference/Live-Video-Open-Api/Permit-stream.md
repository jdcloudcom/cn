# 解除禁播

## 1  描述

解除封禁流，允许该主播重新推流(permitStream)

## 2 请求参数

| 名称          | 类型   | 是否必填 | 描述                                                         |
| ------------- | ------ | -------- | ------------------------------------------------------------ |
| username      | String | 是       | 京东用户名pin                                                |
| signature     | String | 是       | 用户签名，通过md5的方式校验用户的身份信息，保障信息安全。  md5=日期+username+秘钥SecretKey日期：格式为 yyyymmddusername：京东用户名pin秘钥：双方约定示例：比如当前日期2016-10-23，用户pin:   jcloud_00 ,用户秘钥SecretKey ：e7a31b1c5ea0efa9aa2f29c6559f7d61那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| domain        | String | 是       | 禁播域名，目前只支持单域名                                   |
| deleteStreams | Array  | 是       | 解禁的流名，需明确流名所在app，如下示例：“[{‘app’:‘App1’,‘stream’:‘stream1’},{‘app’:‘App2’,‘stream’:‘stream2’}]” |

## 3 返回参数

| **名称** | **描述**                                        |
| -------- | ----------------------------------------------- |
| status   | 表示接口请求成功与否，成功用0表示，其他表示失败 |
| msg      | 提示信息                                        |
| data     | 域名                                            |

## 4  调用示例

- ###    请求地址

http://opencdn.jcloud.com/api/live/permitStream

- ### 请求示例

http://opencdn.jcloud.com/api/live/permitStream

```
{
    "username" :"jd_cdntest",
    "signature" :"914a3f412fd9bc1eec14bb5eb104d253",
    "domain" :"a.live.com",
    "deleteStreams" :[{'app':'App1','stream':'stream1'},{'app':'App2','stream':'stream2'}]
 }
```
 

- ###  返回示例

* json格式
```
{
  "status": 0,
  "msg": "成功",
  "data": "a.live.com"
}
```
