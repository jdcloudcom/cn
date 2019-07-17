# **创建直播加速域名**

## **1. 描述**

创建直播加速域名，包含推流模式和拉流模式以及混合模式的域名创建

## **2. 请求参数**

| 名称           | 类型   | 是否必填 | 描述                                                         |
| -------------- | ------ | -------- | ------------------------------------------------------------ |
| username       | String | 是       | 京东用户名pin                                                |
| signature      | String | 是       |用户签名，通过md5的方式校验用户的身份信息，保障信息安全。</br>md5=日期+username+秘钥SecretKey; 日期：格式为 yyyymmdd; username：京东用户名pin; 秘钥：双方约定; </br>示例：比如当前日期2016-10-23,用户pin:jcloud_00,用户秘钥SecretKey：e7a31b1c5ea0efa9aa2f29c6559f7d61,那签名为MD5(20161023jcloud_00e7a31b1c5ea0efa9aa2f29c6559f7d61) |
| siteType | String | 是 | 直播业务模式类型，推流模式（主播推流到CDN）用“push”，拉流模式（CDN回客户源站拉流播放）用“pull”,混合模式（一推流域名对应多个播放域名或者多个拉流域名以及转推域名等状态）用“mix” |
|domainType | String | 是 | 域名类型，参数值为push/pull，push表示推流域名，pull表示拉流域名，即播放域名；业务模式为pull类型时，domainType只能为pull；|
|domain | String | 是 | 加速域名|
|protocol | String |否| 协议，参数可为all、rtmp、hdl（即为http-flv）、hls；all表示不区分协议，当protocol为all时，对应的域名可以直接转rtmp、hls、flv|
|referDomain | String |否 |关联的推流域名，推流模式，混合模式下创建播放域名时，为必须的字段，其他情况非必须|
|sourceType | String |否|混合模式和拉流模式下为必填 |
|source | String |否 |回源信息配置，ip回源时master 表示主，slave 表示备，ratio表示权重，所有ratio的配置项相加应该为1；域名回源时，priority表示优先级 |
|forwardDomain| String |否|转推域名 |
|audioType| String |否|当前只支持AAC,非必填项 |
|videoType| String |否|当前只支持H.264,非必填项 |
 
## **3. 返回参数**

| **名称** | **描述**                                                  |
| -------- | --------------------------------------------------------- |
| status   | 结果状态, 表示接口请求成功与否，成功用0表示，其他表示失败 |
| msg      | 提示信息 |
| data     | 域名  |
| requestId| 创建任务|
 
## **4. 调用示例**

- ### **请求地址**

https://opencdn.jcloud.com/api/live/createDomain

 - ### **请求示例**

```
{
    "username":"jcloud_username",
    "signature":"xxxxxxxxx",
    "siteType":"push/pull/mix",//业务模式， 推流模式，拉流模式，混合模式(推拉流模式)
    "domainType":"push/pull",  //本次添加的域名类型,业务模式为pull类型时，domainType只能为pull
    "domain":"newDomain.ex.com",//本次需要添加的域名
    "protocol":"rtmp/hls/hdl/all",//如果创建的是拉流域名，那么为必须的字段
    "referDomain":"xxxxx",//关联的推流域名，推流模式，混合模式下创建播放域名时，为必须的字段，其他情况非必须
    "sourceType":"ips/domain" , //ip or domain，混合模式和拉流模式下为必填
    "source":{   //回源信息配置
        "ips": {
            "master": {//所有ratio的配置项相加应该为1
                "1.1.1.1": {
                    "isp": "default",
                    "ratio": 0.25
                },
                "1.1.1.2": {
                    "isp": "CM",
                    "ratio": 0.49
                },
                "1.1.1.3": {
                    "isp": "CT",
                    "ratio": 0.43
                }
            },
            "slave": {
                "1.1.1.5": {
                    "isp": "default",
                    "ratio": 0.73
                },
                "1.1.1.6": {
                    "isp": "default",
                    "ratio": 0.76
                }
            }
        },
        "domain": {  //
            "a.jd.com": {"priority": 3},
            "c.jd.com": {"priority": 1}
         }
        }, 
    "forwardDomain":"forward.jcloud.com",
    "audioType":"AAC", //当前只支持AAC,非必填项
    "videoType":"H.264"   //当前只支持H.264,非必填项
}
```

- #### **创建混合模式下的推流域名**
```
{
    "username":"jcloud_username",
    "signature":"xxxxxxxxx",
    "siteType":"mix",//混合模式(推拉流模式)
    "domainType":"push",  //本次添加的域名类型:推流域名
    "domain":"push.ex.com",//本次需要添加的推流域名
    "forwardDomain":"forward.jcloud.com" //配置的转推域名，允许为空
}
```

- #### **创建混合模式下的拉流域名**
```
{
    "username":"jcloud_username",
    "signature":"xxxxxxxxx",
    "siteType":"mix",//混合模式(推拉流模式)
    "domainType":"pull",  //本次添加的域名类型
    "domain":"pull.ex.com",//本次需要添加的域名
    "protocol":"rtmp",//如果创建的是拉流域名，那么为必须的字段
    "referDomain":"push.ex.com",//关联的推流域名
    "sourceType":"domain" , //ip or domain，混合模式和拉流模式下为必填
    "source":{   //回源信息配置
         "domain": {  
            "origin1.jcloud.com": {"priority": 3},
            "origin2.jcloud.com": {"priority": 1}
         }
     }
}
```

- #### **创建拉流模式下的拉流域名**
```
{
    "username":"jcloud_username",
    "signature":"xxxxxxxxx",
    "siteType":"pull",//拉流模式
    "domainType":"pull",  //本次添加的域名类型
    "domain":"pullRtmp.ex.com",//本次需要添加的域名
    "protocol":"rtmp",//如果创建的是拉流域名，那么为必须的字段
    "sourceType":"domain" , //ip or domain，混合模式和拉流模式下为必填
    "source":{   //回源信息配置
         "domain": {  
            "origin1.jcloud.com": {"priority": 3},
            "origin2.jcloud.com": {"priority": 1}
         }
     }
}
```

- #### **创建推流模式下的推流域名**
```
{
    "username":"jcloud_username",
    "signature":"xxxxxxxxx",
    "siteType":"push",//推流模式
    "domainType":"push",  //本次添加的域名类型:推流域名
    "domain":"push1.ex.com",//本次需要添加的推流域名
    "forwardDomain":"forward.jcloud.com" //配置的转推域名，允许为空
}
```

- #### **创建推流模式下的拉流域名**
```
{
    "username":"jcloud_username",
    "signature":"xxxxxxxxx",
    "siteType":"push",//推流模式
    "domainType":"pull",  //本次添加的域名类型
    "domain":"pullHls.ex.com",//本次需要添加的域名
    "protocol":"hls",//如果创建的是拉流域名，那么为必须的字段
    "referDomain":"push1.ex.com"//关联的推流域名
}
```

- ### **返回示例**

*正常响应
```
{
    "status": 0,
    "msg": "",
    "requestId":"xxxxxxxxxxxx",
    "data": {
    }
}
```
*异常响应
```
{
    "status": 1 ,//或其他错误码
    "msg": "错误原因",
    "requestId":"xxxxxxxxxxxx",
    "data": {
    }
}
```
