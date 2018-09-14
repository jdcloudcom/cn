# **查询加速域名**

## **1、描述**

查询加速域名(queryDomains)

## **2、请求参数**

| **名称**   | **类型** | **是否必填** | **描述**                                                     |
| ---------- | -------- | ------------ | ------------------------------------------------------------ |
| username   | String   | 是           | 京东用户名pin                                                |
| signature  | String   | 是           | 用户签名，通过md5的方式校验用户的身份信息，保障信息安全。  md5=日期+username+秘钥SecretKey日期：格式为 yyyymmddusername：京东用户名pin秘钥：双方约定示例：比如当前日期2016-10-23，用户pin: jcloud_00 ,用户秘钥SecretKey   ：e7a31b1c5ea0efa9aa2f29c6559f7d61那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| domain     | String   | 否           | 模糊匹配加速域名                                             |
| pageNumber | int      | 否           | 查询分页页码，不传默认为1                                    |
| pageSize   | int      | 否           | 查询分页条数，不传默认10条                                   |
| type       | String   | 否           | 域名服务资源类型，目前只支持：web表示 静态小文件download表示大文件加速vod表示视频加速（暂不支持类型：dynamic表示动态加速，live表示直播加速） |
| status     | String   | 否           | 状态，不传查询全部域名，0(查询停用域名)，1（查询启动状态域名），4（查询部署中域名），5（查询审核中域名），6（查询审核驳回域名） |

## **3、返回参数**

| **名称** | **描述**                                                     |
| -------- | ------------------------------------------------------------ |
| status   | 结果状态，表示接口请求成功与否，成功用0表示，其他表示失败    |
| msg      | 提示信息，如发送任务失败的原因等                             |
| data     | 域名信息数组                                                 |
| domain   | 加速域名                                                     |
| cname    | cname                                                        |
| type     | 域名服务资源类型，目前只支持web表示 静态小文件，download表示大文件加速，vod表示视频加速 （暂不支持类型：dynamic表示动态加速，live表示直播加速） |
| status   | 域名申请开通状态，审核中，审核通过，运行中，停止             |

 

**4、调用示例**

- **请求地址**

http://opencdn.jcloud.com/api/queryDomains

- ### **请求示例**

curl请求示例： 

```
curl -H “Content-type: application/json” -X POST -d ‘{“username”:“test_user”,“signature”:“914a3f412fd9bc1eec14bb5eb104d253”,“pageNumber”:1,“pageSize”:10}’ http://opencdn.jcloud.com/api/queryDomains
```

• json格式

```
http://opencdn.jcloud.com/api/queryDomains
{
    "username" :"test_user",
    "signature" :"b036e6094db32b5a5abc47e6be426c50",
    "pageNumber":1,
    "pageSize":10
   
 }
```

- ### **返回示例**

  ### •        json格式

```
{
    "status": 0,
    "msg": "成功",
    "data": {
        "total": 10,
        "domains": [
            {
                "cname": "www.a.com.s.galileo.jcloud-cdn.com",
                "domain": "www.a.com",
                "status": "部署中",
                "type": "图片小文件"
            },
            {
                "cname": "www.b.com.s.galileo.jcloud-cdn.com",
                "domain": " www.b.com ",
                "status": "部署中",
                "type": "图片小文件"
            }
            ]
    }
}
```

 