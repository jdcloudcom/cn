# **设置通信协议**

## **1、 描述**

设置通信协议 (setHttpType)

## **2、请求参数**

| **名称**    | **类型** | **是否必填** | **描述**                                                     |
| ----------- | -------- | ------------ | ------------------------------------------------------------ |
| username    | String   | 是           | 京东用户名pin                                                |
| signature   | String   | 是           | 用户签名，通过md5的方式校验用户的身份信息，保障信息安全。  md5=日期+username+秘钥SecretKey日期：格式为 yyyymmddusername：京东用户名pin秘钥：双方约定示例：比如当前日期2016-10-23，用户pin: jcloud_00 ,用户秘钥SecretKey   ：e7a31b1c5ea0efa9aa2f29c6559f7d61那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| domain      | String   | 是           | 加速域名                                                     |
| httpType    | String   | 是           | http类型*，*只能为http或者https，默认为http。当设为https时，需要上传证书和私钥 |
| certificate | String   | 否           | 用户证书，当httpType为https时必须设置                        |
| rsaKey      | String   | 否           | 证书私钥，当httpType为https时必须设置                        |
| jumpType    | String   | 否           | 设置跳转类型，有三种类型：default、http、https；默认是default，遵循源站，当httpType为https时必须设置 |

## 

## **3、返回参数**

| **名称** | **描述**                                                  |
| -------- | --------------------------------------------------------- |
| status   | 结果状态，表示接口请求成功与否，成功用0表示，其他表示失败 |
| msg      | 提示信息                                                  |
| data     | 返回数据                                                  |

## 

## **4、调用示例**

- ### **请求地址**

http://opencdn.jcloud.com/api/setHttpType

- ### **请求示例**

curl请求示例： 

```
curl -H “Content-type: application/json” -X POST -d ‘{“username”:“test_user”,“signature”:“914a3f412fd9bc1eec14bb5eb104d253”,“domain” :“www.a.com”,“httpType” :“https”,“certificate” :“start—-stop”,“rsaKey” :“start—stop”,“jumpType” :“https”}’ http://opencdn.jcloud.com/api/setHttpType
```

- json格式

```
html http://opencdn.jcloud.com/api/setHttpType
{
  “username” :“test_user”, 
  “signature” :“d00f58f89e8cd55dc080aec0d8051845”, 
  “domain” :“www.a.com”, 
  “httpType” :“https”, 
  “certificate” :“start—-stop”, 
  “rsaKey” :“start—stop”, 
  “jumpType” :“https”
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