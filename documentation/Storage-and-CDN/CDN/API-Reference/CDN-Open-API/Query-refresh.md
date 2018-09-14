# **查询刷新任务**

## **1、描述**

查询已刷新url或者目录下的任务信息(refreshQuery)

## **2、请求参数**

| **名称**  | **类型** | **是否必填** | **描述**                                                     |
| --------- | -------- | ------------ | ------------------------------------------------------------ |
| username  | String   | 是           | 京东用户名pin                                                |
| signature | String   | 是           | 用户签名，通过md5的方式校验用户的身份信息，保障信息安全。  md5=日期+username+秘钥SecretKey日期：格式为 yyyymmddusername：京东用户名pin秘钥：双方约定示例：比如当前日期2016-10-23，用户pin: jcloud_00 ,用户秘钥SecretKey   ：e7a31b1c5ea0efa9aa2f29c6559f7d61那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| taskid    | String   | 是           | 任务id,刷新时返回参数的taskid,32位，如：545ec2e2-e9e5-47b8-8f34-44c104a84fd3 |

## **3、返回参数data中说明**

| **名称** | **描述**                                        |
| -------- | ----------------------------------------------- |
| status   | 结果状态 0，刷新成功，1正在进行中，2刷新失败    |
| msg      | 提示信息                                        |
| taskid   | 任务id,用来查询是否刷新成功的唯一标示，uid 32位 |

## **4、调用示例**

- ###  **请求地址**

http://opencdn.jcloud.com/api/refreshQuery

- ### **请求示例**

```
http://opencdn.jcloud.com/api/refreshQuery
{
    "username":"jcloud_00",
    "signature":"d847267fc702273abf699dd0c3128d64",
    "taskid":"545ec2e2-e9e5-47b8-8f34-44c104a84fd3"
}
```

- ### **返回示例**

•        json格式

```
{
  "status": 0,
  "data": {
    "taskid": "545ec2e2-e9e5-47b8-8f34-44c104a84fd3",
    "status": 1,
    "msg": "进行中"
  }
}
```

 