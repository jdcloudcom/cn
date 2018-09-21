# 设置禁播

## 1  描述

当主播推送非法内容时，禁止主播推流(forbidStream)

## 2 请求参数

| 名称      | 类型   | 是否必填 | 描述                                                         |
| --------- | ------ | -------- | ------------------------------------------------------------ |
| username  | String | 是       | 京东用户名pin                                                |
| signature | String | 是       | 用户签名，通过md5的方式校验用户的身份信息，保障信息安全。  md5=日期+username+秘钥SecretKey日期：格式为 yyyymmddusername：京东用户名pin秘钥：双方约定示例：比如当前日期2016-10-23，用户pin:   jcloud_00 ,用户秘钥SecretKey ：e7a31b1c5ea0efa9aa2f29c6559f7d61那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| domain    | String | 是       | 禁播域名，目前只支持单域名                                   |
| app       | String | 是       | 封禁推流的app                                                |
| stream    | String | 是       | 禁播流名， 可同时禁播多路流                                  |
| type      | int    | 是       | 禁播类型[1：永久封禁，2：限时封禁]                           |
| time      | long   | 是       | 禁播时长（单位为分钟），如果是永久封禁，time为0              |

 

## 3  返回参数

| **名称** | **描述**                                         |
| -------- | ------------------------------------------------ |
| status   | 表示接口请求成功与否，成功用0表示，其他表示失败, |
| msg      | 提示信息                                         |
| data     | 域名                                             |

 

## 4 调用示例

- ###   请求地址

http://opencdn.jcloud.com/api/live/forbidStream

- ###   请求示例

http://opencdn.jcloud.com/api/live/forbidStream

```
{
    "username" :" test_user ",
    "signature" :"d00f58f89e8cd55dc080aec0d8051845",
    "domain" :"www.a.com",
    "app" :"live",
    "stream": "test17",
    "type" :2,
    "time" :60
 }
```
- ###  返回示例

* json格式
```
{
  "status": 0,
  "msg": "成功",
  "data": "www.a.com "
}
```
