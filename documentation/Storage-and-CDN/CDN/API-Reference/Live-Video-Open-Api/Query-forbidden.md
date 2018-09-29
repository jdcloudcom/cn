# 查询禁播流列表

## 1 描述

查询某段时间内禁播流列表(queryForbidden)

## 2 请求参数

| 名称       | 类型   | 是否必填 | 描述                                                         |
| ---------- | ------ | -------- | ------------------------------------------------------------ |
| username   | String | 是       | 京东用户名pin                                                |
| signature  | String | 是       | 用户签名，通过md5的方式校验用户的身份信息，保障信息安全。  md5=日期+username+秘钥SecretKey日期：格式为 yyyymmddusername：京东用户名pin秘钥：双方约定示例：比如当前日期2016-10-23，用户pin:   jcloud_00 ,用户秘钥SecretKey ：e7a31b1c5ea0efa9aa2f29c6559f7d61那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| domain     | String | 是       | 禁播域名，目前只支持单域名                                   |
| app        | String | 否       | 发布点，目前支持单发布点的查询，不支持同时查询多个，当不输入app，只输入域名时，查询结果为该域名下的所有禁播流 |
| stream     | String | 否       | 流名，支持多个流名的查询，以英文字母分割，如stream1, stream2；输入流名时必须输入app |
| start_time | String | 否       | 查询开始时间，时间格式：yyyy-mm-dd hh:mi；没有输入开始时间时默认为今天；有开始时间没有结束时间默认为开始时间到当前时间；无开始有结束时间，以结束时间的天单位的0点作为开始时间，如如结束时间是20180529 14:29,开始时间为20180529 00:00 |
| end_time   | String | 否       | 查询结束时间，时间格式：yyyy-mm-dd hh:mi；                   |
| pageNumber | int    | 否       | 查询分页页码，不传默认为1                                    |
| pageSize   | int    | 否       | 查询分页条数，不传默认10条                                   |

 

## 3   返回参数

| **名称**  | **描述**                                         |
| --------- | ------------------------------------------------ |
| status    | 表示接口请求成功与否，成功用0表示，其他表示失败, |
| msg       | 提示信息                                         |
| data      | 域名信息数组                                     |
| total     | 该域名下禁播流总数                               |
| streams   | 禁播流列表                                       |
| app       | 禁播app                                          |
| stream    | 禁播stream                                       |
| type      | 禁播类型[1：永久封禁，2：限时封禁]               |
| typeDes   | 禁播类型描述                                     |
| startTime | 查询开始时间                                     |
| endTime   | 查询结束时间                                     |
| time      | 限时封禁时的禁播时长                             |

## 4 调用示例

- ### 请求地址

http://opencdn.jcloud.com/api/live/queryForbidden

- ### 请求示例

http://opencdn.jcloud.com/api/live/queryForbidden
```
{
    "username" :"jd_cdntest",
    "signature" :"5fdd933ad652298f9f0fd4c87883e283",
    "domain" :"wshplay-113.live.com",
    "app":"live",
    "stream":"shitest1",
    "pageNumber":1,
    "pageSize":"100",
    "start_time" :"2018-05-31 00:05",
    "end_time" :"2018-06-01 21:49"
 }
```
- ### 返回示例

* json格式
```
{
    "status": 0,
    "msg": "成功",
    "data": {
        "total": 1,
        "streams": [
            {
                "app": "live",
                "stream": "shitest1",
                "type": 2,
                "typeDes": "限时封禁",
                "startTime": "2018-06-01 15:41:23",
                "endTime": "2018-06-01 15:46:23",
                "time": 5
            }
        ]
    }
}
```
