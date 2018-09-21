# **查询域名配置**

## **1、描述**

查询域名配置(queryDomainConfigs)

## **2、请求参数**

| **名称**  | **类型** | **是否必填** | **描述**                                                     |
| --------- | -------- | ------------ | ------------------------------------------------------------ |
| username  | String   | 是           | 京东用户名pin                                                |
| signature | String   | 是           | 用户签名，通过md5的方式校验用户的身份信息，保障信息安全。  md5=日期+username+秘钥SecretKey日期：格式为 yyyymmddusername：京东用户名pin秘钥：双方约定示例：比如当前日期2016-10-23，用户pin: jcloud_00 ,用户秘钥SecretKey   ：e7a31b1c5ea0efa9aa2f29c6559f7d61那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| domain    | String   | 是           | 查询的域名，只支持一个域名查询                               |

## **3、返回参数** 

| **名称**         | **描述**                                                     |
| ---------------- | ------------------------------------------------------------ |
| status           | 结果状态, 表示接口请求成功与否，成功用0表示，其他表示失败    |
| msg              | 提示信息                                                     |
| data             | 域名信息数组                                                 |
| domain           | 加速域名                                                     |
| ignoreArgs       | 忽略参数设置，off 关闭，on 打开                              |
| rangeArgs        | Range参数设置，off 关闭，on 打开                             |
| httpType         | http类型，只能为http或者https，默认为http。当设为https时，需要调用“设置通信协议”接口上传证书和私钥 |
| httpsCertificate | https证书， 如果加速域名的HttpType为http，则该项为空         |
| httpsRsaKey      | https私钥，如果加速域名的HttpType为http，则该项为空          |
| httpsJumpType    | 跳转类型，取值：default、http、https                         |



## **4、调用示例**

### **请求地址**

http://opencdn.jcloud.com/api/queryDomainConfigs

### **请求示例**

```
http://opencdn.jcloud.com/api/queryDomainConfigs

{
    "username" :"test_user",
    "signature" :"d847267fc702273abf394dd0c3128d64",
    "domain" :"www.b.com"
    
 }
```

### **返回示例**

•        json格式

```
{
    "status": 0,
    "msg": "成功",
    "data": {
        "rangeArgs": "on",
        "httpsCertificate": "",
        "httpsJumpType": "",
        "httpsRsaKey": "",
        "httpType": "http",
        "ignoreArgs": "on"
    }
}
```
