# **查询域名详情**

## **1、描述**

查询加速域名详情(queryDomainDetail)

## **2、请求参数**

| **名称**  | **类型** | **是否必填** | **描述**                                                     |
| --------- | -------- | ------------ | ------------------------------------------------------------ |
| username  | String   | 是           | 京东用户名pin                                                |
| signature | String   | 是           | 用户签名，通过md5的方式校验用户的身份信息，保障信息安全。  md5=日期+username+秘钥SecretKey日期：格式为 yyyymmddusername：京东用户名pin秘钥：双方约定示例：比如当前日期2016-10-23，用户pin: jcloud_00 ,用户秘钥SecretKey   ：e7a31b1c5ea0efa9aa2f29c6559f7d61那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| domain    | String   | 是           | 加速域名                                                     |

 

## **3、返回参数**

| **名称**       | **描述**                                                     |
| -------------- | ------------------------------------------------------------ |
| status         | 结果状态，表示接口请求成功与否，成功用0表示，其他表示失败    |
| msg            | 提示信息，如发送任务失败的原因等                             |
| data           | 域名信息数组                                                 |
| domain         | 加速域名                                                     |
| type           | 域名服务资源类型，目前只支持web表示   静态小文件，download表示大文件加速，vod表示视频加速   （暂不支持类型：dynamic表示动态加速，live表示直播加速） |
| sourceType     | ips：IP列表，domain：域名，oss:oss回源                       |
| source         | 回源信息，ips和domain 返回json字符串,oss返回域名             |
| backSourceType | 回源类型，只能为http（80端口回源）或者https（443端口回源），默认为http |

 

## **4、调用示例**

- ### **请求地址**

http://opencdn.jcloud.com/api/queryDomainDetail

- ### **请求示例**

curl请求示例：

```
 curl -H “Content-type: application/json” -X POST -d ‘{“username”:“test_user”,“signature”:“914a3f412fd9bc1eec14bb5eb104d253”,“domain” :“www.a.com”}’ http://opencdn.jcloud.com/api/queryDomainDetail
```

•        json格式

```
http://opencdn.jcloud.com/api/queryDomainDetail
{
    "username" :"test_user",
    "signature" :"d847267fc702273abf394dd0c3128d64",
    "domain" :"www.a.com"
    
 }
```

- ### **返回示例**

•        json格式

```
{
    "status": 0,
    "msg": "成功",
    "data": {
        "backSourceType": "http",
        "sourceType": "domain",
        "source": "[{\"priority\":2,\"domain\":\"source2.test1.a.com \"},  {\"priority\":1,\"domain\":\"source1. test1.a.com \"}]",
        "status": "部署中",
        "archiveNo": "京ICP备11041704号-6",
        "domain": "test1.a.com",
        "dailyBandWidth": 200,
        "type": "图片小文件",
        "cname": "test1.a.com.s.galileo.jcloud-cdn.com"
    }
}
```

 