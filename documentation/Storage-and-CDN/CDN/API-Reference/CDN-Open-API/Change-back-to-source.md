# **回源策略变更**

## **1、 描述**

回源策略变更 (changeSource)

## **2、 请求参数**

| **名称**       | **类型** | **是否必填** | **描述**                                                     |
| -------------- | -------- | ------------ | ------------------------------------------------------------ |
| username       | String   | 是           | 京东用户名pin                                                |
| signature      | String   | 是           | 用户签名，通过md5的方式校验用户的身份信息，保障信息安全。  md5=日期+username+秘钥SecretKey日期：格式为 yyyymmddusername：京东用户名pin秘钥：双方约定示例：比如当前日期2016-10-23，用户pin: jcloud_00 ,用户秘钥SecretKey   ：e7a31b1c5ea0efa9aa2f29c6559f7d61那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| domain         | String   | 是           | 加速域名                                                     |
| type           | String   | 是           | 域名服务资源类型，目前只支持web表示   静态小文件，download表示大文件加速，vod表示视频加速   （暂不支持类型：dynamic表示动态加速，live表示直播加速） |
| sourceType     | String   | 是           | ips：IP列表，domain：域名，oss:oss回源                       |
| source         | String   | 是           | ips和domain必须是json格式                                    |
| httpType       | String   | 否           | http类型，只能为http或者https，默认为http。当设为https时，需要调用“设置通信协议”接口上传证书和私钥 |
| backSourceType | String   | 否           | 回源类型，只能为http（80端口回源）或者https（443端口回源），默认为http |

 

## **3、 返回参数**

| **名称** | **描述**                                                  |
| -------- | --------------------------------------------------------- |
| status   | 结果状态，表示接口请求成功与否，成功用0表示，其他表示失败 |
| msg      | 提示信息                                                  |
| data     | 返回数据                                                  |

 

## **4、调用示例**

- ### **请求地址**

http://opencdn.jcloud.com/api/changeSource

- ### **请求示例**

curl请求示例： 

```
curl -H “Content-type: application/json” -X POST -d ‘{“username”:“test_user”,“signature”:“914a3f412fd9bc1eec14bb5eb104d253”,“domain” :“www.b.com”, “type” :“web”,“sourceType” :“domain”,“source” :“[{’domain’:’source1.www.a.com’,’priority’:’1’},{’domain’:’source2.www.a.com’,’priority’:’2’}]”}’ http://opencdn.jcloud.com/api/changeSource
```

•        json格式

```
html http://opencdn.jcloud.com/api/changeSource
{ 
“username”:“test_user”, 
“signature”:“d00f58f89e8cd55dc080aec0d8051845”, 
“domain”:“www.a.com”, 
“type”:“web”, 
“sourceType”:“domain”, 
“source”:“[{‘domain’:‘source1.www.a.com’,‘priority’:‘1’},{‘domain’:‘source2.www.a.com’,‘priority’:‘2’}]” 
}
```

- ### **返回示例**

•        json格式

```
{
  "status": 0,
  "msg": "成功",
  "data": "www.a.com"
}
```

 