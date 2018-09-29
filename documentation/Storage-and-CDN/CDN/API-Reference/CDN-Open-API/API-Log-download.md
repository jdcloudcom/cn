# **日志下载**

## **1、描述**

查询日志下载地址 (downloadUrlInterval)

## **2、请求参数**

| **名称**   | **类型** | **是否必填** | **描述**                                                     |
| ---------- | -------- | ------------ | ------------------------------------------------------------ |
| username   | String   | 是           | 京东用户名pin                                                |
| signature  | String   | 是           | 用户签名，通过md5的方式校验用户的身份信息，保障信息安全。  md5=日期+username+秘钥SecretKey日期：格式为 yyyymmddusername：京东用户名pin秘钥：双方约定示例：比如当前日期2016-10-23，用户pin: jcloud_00 ,用户秘钥SecretKey   ：e7a31b1c5ea0efa9aa2f29c6559f7d61那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| domain     | String   | 是           | 需要下载日志的域名，支持多域名下载，参数示例“www.a.com,www.b.com” |
| start_time | String   | 是           | 时间格式：yyyy-mm-dd hh:mi 参考示例：2016-12-14 07:00        |
| end_time   | String   | 否           | 不是必填参数，不传默认到当前时间                             |
| interval   | String   | 否           | HOUR(按小时下载)，DAY（按天下载）不传或者传错都是按照小时下载。注：HOUR(按小时下载)是.log文件，DAY（按天下载）是.zip文件。 |


## **3、** **返回参数data中说明**

| **名称** | **描述**                                                   |
| -------- | ---------------------------------------------------------- |
| status   | 结果状态，0表示成功，其他表示失败                          |
| msg      | 提示信息                                                   |
| data     | 返回数据                                                   |
| urls     | 日志所有地址，如果查询一天，则返回24条数据，每小时一条url  |
| url      | 日志下载URL，有时效性限制，2小时内下载，超时则需要重新请求 |


## **4、调用示例**

 **请求地址**

http://opencdn.jcloud.com/api/downloadUrlInterval

 **请求示例**

- curl格式

```
curl -H "Content-type:application/json" -X POST -d '{"username":"test_user","signature":"d847267fc702273abf394dd0c3128d64","domain":"www.a.com,www.b.com","start_time":"2017-10-19 00:00","end_time":"2017-10-19 23:59","interval":"DAY"}' http://opencdn.jcloud.com/api/downloadUrlInterval
```

* json格式

```
http://opencdn.jcloud.com/api/downloadUrlInterval
{
    "username" :"test_user",
    "signature" :"d847267fc702273abf394dd0c3128d64",
    "domain" :" www.a.com,www.b.com ",
    "start_time" :"2017-10-19 00:00",
    "end_time" :"2017-10-19 23:59",
    "interval" :"DAY",//按天下载
 }
```

 **返回说明** 

 **json格式**
 
```
{
"status": 0,//0 表示本次请求成功
"data": [
{
"domain": "DOMAIN",//查询的域名, 不要包含 http://
"urls": [
[
"URL"//日志URL 
],
],
},
]
}
```

**返回示例**

```
{
    "status": 0,
    "msg": "成功",
    "data": [
        {
            "domain": "www.a.com",
            "urls": [
                "http://oss.cn-north-1.jcloudcs.com/cdnuserlog/www.a.com/20171019.zip?Expires=1508753731&AccessKey=ImtdrS1VXMdkph&Signature=2br%2B5KwRY5Nk5YvLp7%2BfAwsQVAM%10D"
            ]
        },
        {
            "domain": " www.b.com ",
            "urls": [
                "http://oss.cn-north-1.jcloudcs.com/cdnuserlog/www.b.com/20171019.zip?Expires=1508753731&AccessKey=ImtsrS1VXMfeikph&Signature=HdM1weVHJbHuS%2FEiZm82o9GrZSY%6D"
            ]
        }
    ]
}
```
