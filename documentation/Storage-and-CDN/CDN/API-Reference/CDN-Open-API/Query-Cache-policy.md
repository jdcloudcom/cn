# **查询域名缓存策略**

## **1、描述**

查询域名缓存配置(queryDomainCache)

## **2、 请求参数**

| **名称**  | **类型** | **是否必填** | **描述**                                                     |
| --------- | -------- | ------------ | ------------------------------------------------------------ |
| username  | String   | 是           | 京东用户名pin                                                |
| signature | String   | 是           | 用户签名，通过md5的方式校验用户的身份信息，保障信息安全。  md5=日期+username+秘钥SecretKey日期：格式为 yyyymmddusername：京东用户名pin秘钥：双方约定示例：比如当前日期2016-10-23，用户pin: jcloud_00 ,用户秘钥SecretKey   ：e7a31b1c5ea0efa9aa2f29c6559f7d61那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| domain    | String   | 是           | 加速域名                                                     |

 

## **3、** **返回参数**

| **名称**   | **描述**                                                  |
| ---------- | --------------------------------------------------------- |
| status     | 结果状态，表示接口请求成功与否，成功用0表示，其他表示失败 |
| msg        | 提示信息                                                  |
| data       | 域名信息数组                                              |
| domain     | 加速域名                                                  |
| cacheRules | 加速域名的所有缓存规则                                    |
| configId   | 缓存配置id                                                |
| content    | 缓存配置规则                                              |
| ttl        | 缓存时间                                                  |
| weight     | 优先级，只能是1-10之间，1表示优先级最高                   |
| cacheType  | 缓存方式：0表示不缓存，1表示自定义                        |

 

## **4、 调用示例**

- ### **请求地址**

http://opencdn.jcloud.com/api/queryDomainCache

- ### **请求示例**

curl请求示例：

```
 curl -H “Content-type: application/json” -X POST -d ‘{“username”:“test_user”,“signature”:“914a3f412fd9bc1eec14bb5eb104d253”,“domain” :“www.b.com”}’ http://opencdn.jcloud.com/api/queryDomainCache
```

 

•        json格式

```
http://opencdn.jcloud.com/api/queryDomainCache
{
    "username" :"test_user",
    "signature" :"d847267fc702273abf394dd0c3128d64",
    "domain" :"www.b.com"
    
 }
```

- ###  **返回示例**

  ### •        json格式 

```
{
    "status": 0,
    "msg": "成功",
    "data": {
        "total": 2,
        "cacheRules": [
            {
                "configId": "1304",
                "content": ".jpg",
                "ttl": 7200,
                "weight": 2
            },
            {
                "configId": "1305",
                "content":    ".wmv;.mp3;.wma;.ogg;.fiv;.mp4;.avi;.mpg;.mpeg;.f4v;.hlv;.rmvb;.rm;.3gp;.img;.m3u8;.ts",
                "ttl": 3600,
                "weight": 3
            }
        ]
    }
}
```