# **预热**

## **1、描述**

url预热 (prefetch)

## **2、请求参数**

| **名称**     | **类型** | **是否必填** | **描述**                                                     |
| ------------ | -------- | ------------ | ------------------------------------------------------------ |
| username     | String   | 是           | 京东用户名pin                                                |
| signature    | String   | 是           | 用户签名，通过md5的方式校验用户的身份信息，保障信息安全。  md5=日期+username+秘钥SecretKey日期：格式为 yyyymmddusername：京东用户名pin秘钥：双方约定示例：比如当前日期2016-10-23，用户pin: jcloud_00 ,用户秘钥SecretKey   ：e7a31b1c5ea0efa9aa2f29c6559f7d61那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| publish_urls | String   | 是           | 支持string或者String[]，预热url，多个域名中间采用，号分割,例如["http://www.a.com/text1.css","http://www.a.com/text2.js"]单次预热最多100个url |


## **3、返回参数**

| **名称** | **描述**                                        |
| -------- | ----------------------------------------------- |
| status   | 表示接口请求成功与否，成功用0表示，其他表示失败 |
| msg      | 提示信息，如发送任务失败的原因等                |
| taskid   | 任务id,用来查询是否预热成功的唯一标示，uid 32位 |


## **4、调用示例**

- ### **请求地址**

http://opencdn.jcloud.com/api/prefetch

- ### **请求示例**

```
http://opencdn.jcloud.com/api/prefetch
{
    "username":"jcloud_00",
    "signature":"d847267fc702273abf699dd0c3128d64",
    "publish_urls":["http://jiekou.jcloud.com/text.css","http://jiekou.jcloud.com/text.js"]
}
```

- ###  **返回示例**

•        json格式

```
{
  "status": 0,
  "msg": "成功",
  "taskid": "93820486-226d-459b-b33f-5124b566cab7"//任务id，查询预热任务时使用
}
```
