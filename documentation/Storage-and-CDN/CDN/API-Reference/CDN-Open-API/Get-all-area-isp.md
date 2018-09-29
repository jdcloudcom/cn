# **获取所有区域+运营商**

## **1、描述**

获取所有区域+运营商 (region_name)

## **2、请求参数**

| **名称**  | **类型** | **是否必填** | **描述**                                                     |
| --------- | -------- | ------------ | ------------------------------------------------------------ |
| username  | String   | 是           | 京东用户名pin                                                |
| signature | String   | 是           | 用户签名，通过md5的方式校验用户的身份信息，保障信息安全。  md5=日期+username+秘钥SecretKey日期：格式为 yyyymmddusername：京东用户名pin秘钥：双方约定示例：比如当前日期2016-10-23，用户pin: jcloud_00 ,用户秘钥SecretKey   ：e7a31b1c5ea0efa9aa2f29c6559f7d61那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |


## **3、返回参数data中说明**

| **名称** | **描述**                       |
| -------- | ------------------------------ |
| status   | 结果状态 0，刷新成功，其他失败 |
| msg      | 提示信息                       |
| data     | 返回数据                       |


## **4、调用示例**

- ### **请求地址**

http://opencdn.jcloud.com/api/region_name

- ### **请求示例**

```
http://opencdn.jcloud.com/api/region_name
{
    "username" :"test_user",
    "signature" :"dbc1c1302d0a1baa48a256cbfc840317"
 }
```

- ### **返回说明**

•        json格式

```
{
"status": 0,//0 表示本次请求成功
"data":{
"mainLandChina":[//中国大陆
{
region,//地区
name//地区名
}
]
"operators":[//运营商
region,//运营商
name//运营商名
]
 "overseas": [  //海外
 region,//海外区域
name//海外区域名称
]

}
}
```

- ### **返回示例**

```
{
    "status": 0,
    "msg": "成功",
    "data": {
        "mainLandChina": [
            {
                "region": "anhui",
                "name": "安徽"
            }
  {
                "region": "zhejiang",
                "name": "浙江"
            }
        ],
              "operators": [
            {
                "region": "cmcc",
                "name": "移动"
            },
            {
                "region": "cnc",
                "name": "联通"
            }
            {
                "region": "huashu",
                "name": "华数"
            }
        ],
        "overseas": [
            {
                "region": "gangaotai",
                "name": "港澳台"
            },
            {
                "region": "world",
                "name": "国外"
            }
        ]
    }
}
```
