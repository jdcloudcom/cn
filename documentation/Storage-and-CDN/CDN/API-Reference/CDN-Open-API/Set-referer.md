# **设置referer黑白名单**

## **1、描述**

设置referer黑白名单信息 (setReferConfig)

## **2、请求参数**

| **名称**   | **类型** | **是否必填** | **描述**                                                     |
| ---------- | -------- | ------------ | ------------------------------------------------------------ |
| username   | String   | 是           | 京东用户名pin                                                |
| signature  | String   | 是           | 用户签名，通过md5的方式校验用户的身份信息，保障信息安全。  md5=日期+username+秘钥SecretKey日期：格式为 yyyymmddusername：京东用户名pin秘钥：双方约定示例：比如当前日期2016-10-23，用户pin: jcloud_00 ,用户秘钥SecretKey   ：e7a31b1c5ea0efa9aa2f29c6559f7d61那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| domain     | String   | 是           | 加速域名                                                     |
| referType  | String   | 是           | refer类型，取值：block（黑名单），allow（白名单）            |
| referList  | String   | 是           | 逗号隔开的域名列表，如果referList传空则为删除即无黑白名单限制 |
| allowEmpty | String   | 否           | 是否允许空refer访问，取值：on(允许),off（拒绝），默认是on    |


## **3、返回参数**

| **名称** | **描述**                                                  |
| -------- | --------------------------------------------------------- |
| status   | 结果状态，表示接口请求成功与否，成功用0表示，其他表示失败 |
| msg      | 提示信息                                                  |
| data     | 返回数据                                                  |


## **4、调用示例**

- ### **请求地址**

http://opencdn.jcloud.com/api/setReferConfig

- ### **请求示例**

 http://opencdn.jcloud.com/api/setReferConfig

\* json格式

```
{
“username” :“test_user”, 
“signature” :“d00f58f89e8cd55dc080aec0d8051845”, 
“domain” :“www.a.com”, 
“referType” :“block”, 
“referList” :“www.baidu.com,www.alibaba.com”, 
“allowEmpty” :“on”
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

 
