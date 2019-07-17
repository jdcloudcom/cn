# **查询IP是否为厂商IP**

 ## **1. 描述**

 查询IP是否为京东云节点IP

 ## **2. 请求参数**

 | **名称**   | **类型** | **是否必填** | **描述**                                                     |
| ---------- | -------- | ------------ | ------------------------------------------------------------ |
| username   | String   | 是           | 京东用户名pin                                                |
| signature  | String   | 是           |用户签名，通过md5的方式校验用户的身份信息，保障信息安全。</br>md5=日期+username+秘钥SecretKey; 日期：格式为 yyyymmdd; username：京东用户名pin; 秘钥：双方约定; </br>示例：比如当前日期2016-10-23,用户pin:jcloud_00,用户秘钥SecretKey：e7a31b1c5ea0efa9aa2f29c6559f7d61,那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61)|
| ips     | String   | 是           | 待查询的ip,多个ip使用逗号分隔，参数示例“1.1.1.1,2.2.2.2”,支持IPV6查询|

 ## **3. 返回参数**

 | **名称**   | **描述** | 
| ---------- | -------- |
| status  | 表示接口请求成功与否，成功用0表示，其他表示失败  | 
| msg  | 提示信息 | 
| data | 返回数据| 

 ## **4. 调用示例**

 - ### **请求地址**

 https://opencdn.jcloud.com/api/include_node_ip

 - ### **请求示例**

 ```
{
    "username":"user_test",
    "signature":"ca4c56f85e3582f4d814cc77949c82a7",
    "ips":"1.1.1.1,2.2.2.2"
}
```

 - ### **返回示例**

 ```
{
    "code": 0,
    "message": "",
    "codeDesc": "Success",
    "data": {
        "last_update_time": TS, // 时间戳 
        "list": [
            {
                "ip": "2.2.2.2",// ip
                "platform": "yes",// 是否归属
                "country_code": "1",// 国家
                "prov_code": "123"// 省份
                "city_code ": "123"// 城市
                "isp_code ": "21"// 运营商
            },
            {
                "ip": "1.1.1.1",
                "platform": "no",
                "country_code": "1",// 国家
                "prov_code": "123"// 省份
                "city_code ": "123"// 城市
                "isp_code ": "21"// 运营商
            }
        ]
    }
}
 ```
