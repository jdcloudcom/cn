# **查询节点IP**

## **1、描述**

查询节点IP (node_ip)

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


## **4、调用示例**

- ### **请求地址**

http://opencdn.jcloud.com/api/node_ip

- ### **请求示例**

```
http://opencdn.jcloud.com/api/node_ip
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
    "status": 0, //0 代表成功
    "message": "success",
    "data": {
    DOMAIN: [
    IP1,
    IP2,
    ],
    },
}
```

- ### **返回示例**

```
{
    "status": 0,
    "msg": "成功",
    "data": {
        "www.a.com": [
            "1.1.1.1",
            "2.2.2.2"
        ],
        "www.b.com": [
            "3.3.3.3",
            "4.4.4.4"
             ]
    }
}
```
