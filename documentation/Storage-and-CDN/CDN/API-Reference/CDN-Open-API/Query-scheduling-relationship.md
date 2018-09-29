# **实时调度覆盖关系**

## **1、描述**

实时调度覆盖关系 (area_isp_ip)

## **2、** **请求参数**

| **名称**  | **类型** | **是否必填** | **描述**                                                     |
| --------- | -------- | ------------ | ------------------------------------------------------------ |
| username  | String   | 是           | 京东用户名pin                                                |
| signature | String   | 是           | 用户签名，通过md5的方式校验用户的身份信息，保障信息安全。  md5=日期+username+秘钥SecretKey日期：格式为 yyyymmddusername：京东用户名pin秘钥：双方约定示例：比如当前日期2016-10-23，用户pin: jcloud_00 ,用户秘钥SecretKey   ：e7a31b1c5ea0efa9aa2f29c6559f7d61那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| domain    | String   | 是           | 待查询的域名,多个域名使用逗号分隔，参数示例“www.a.com,www.b.com” |


## **3、返回参数data中说明**

| **名称** | **描述**                       |
| -------- | ------------------------------ |
| status   | 结果状态 0，刷新成功，其他失败 |
| msg      | 提示信息                       |
| data     | 返回数据                       |


## **4、** **调用示例**

- ### **请求地址**

http://opencdn.jcloud.com/api/area_isp_ip

- ### **请求示例**

```
http://opencdn.jcloud.com/api/area_isp_ip
{
    "username" :"test_user",
    "signature" :"d847267fc702273abf394dd0c3128d64",
    "domain" :"www.a.com,www.b.com"
 }
```

- ### **返回说明**

•        json格式

```
 {
    "domain1":{ // 查询的第一个域名
    "isp1":{ // 运营商
    "area1":[ip1,ip2,ip3......], // 地区+ip， 需要列出所有当前放出的解析
    "area2":[ip4,ip5,ip6......]
    ......
    },
    "isp2":{
    "area1":[ip1,ip2,ip3......],
    ......
    },
    ......
    } "
    domain2":{
    "isp1":{
    "area1":[ip7,ip8,ip9......]
    ......
    } .
    .....
    }
}
```

- ### **返回示例**

```
{
    "status": 0,
    "msg": "成功",
    "data": {
        "ne-www.a.com": {
            "cmcc": {
                "yunnan": [
                    "1.1.1.1"
                ],
                "sichuan": [
                    "2.2.2.2",
                    "3.3.3.3"
                ]
            }
        },
        "www.a.com": {
            "cmcc": {
               "guangxi": [
                    "4.4.4.4"
                ],
                 "beijing": [
                    "5.5.5.5"
                ]
            }
        }
    }
}
```

 
