# **缓存策略变更**

## **1、描述**

缓存策略变更 (changeCache/{status})

## **2、请求参数**

| **名称**  | **类型** | **是否必填** | **描述**                                                     |
| --------- | -------- | ------------ | ------------------------------------------------------------ |
| username  | String   | 是           | 京东用户名pin                                                |
| signature | String   | 是           | 用户签名，通过md5的方式校验用户的身份信息，保障信息安全。  md5=日期+username+秘钥SecretKey日期：格式为 yyyymmddusername：京东用户名pin秘钥：双方约定示例：比如当前日期2016-10-23，用户pin: jcloud_00 ,用户秘钥SecretKey   ：e7a31b1c5ea0efa9aa2f29c6559f7d61那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| domain    | String   | 是           | 加速域名                                                     |
| cacheType | String   | 否           | 缓存方式：0表示不缓存，1表示自定义。 默认是自定义缓存        |
| weight    | String   | 是           | 权重，权重不能重复，权重相同的只能创建一条                   |
| content   | String   | 是           | 缓存策略内容                                                 |
| ttl       | int      | 是           | 过期时间，时间秒                                             |
| status    | String   | 是           | add,update,delete 其中update和delete必须要configid,缓存配置id |

 

## **3、返回参数**

| **名称** | **描述**                                                  |
| -------- | --------------------------------------------------------- |
| status   | 结果状态，表示接口请求成功与否，成功用0表示，其他表示失败 |
| msg      | 提示信息                                                  |
| data     | 返回数据                                                  |

 

## **4、调用示例**

### **请求地址**

http://opencdn.jcloud.com/api/changeCache/add

### **请求示例**

curl请求示例：

```
 curl -H “Content-type: application/json” -X POST -d ‘{“username”:“test_user”,“signature”:“914a3f412fd9bc1eec14bb5eb104d253”,“domain” :“www.a.com”, “weight” :“1”, “ttl” :“7200”, “content” :“.jpg”}’ http://opencdn.jcloud.com/api/changeCache/add
```

* json格式

```
http://opencdn.jcloud.com/api/changeCache/add
{
    "username" :"test_user",
    "signature" :"d00f58f89e8cd55dc080aec0d8051845",
    "domain" :"www.a.com",
    "weight" :"1",
    "ttl" :"7200",
    "configId": "1303",//修改和删除时必填字段，新加缓存配置不需要
    "content" :".jpg"
 }
```

### **返回示例**

• json格式

```
{
  "status": 0,
  "msg": "成功",
  "data": "www.a.com"
}
```
