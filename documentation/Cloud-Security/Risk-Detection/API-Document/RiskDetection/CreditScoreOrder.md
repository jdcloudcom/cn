# creditScoreOrder


## 描述
订单风险识别

## 请求方式
POST

## 请求地址
https://bri.jdcloud-api.com/v1/creditScore:check


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**tasks**|CreditTaskOrder|True| |检测任务列表，包含一个或多个元素。每个元素是个结构体，最多可添加100元素，即最多对100个数据进行评分。每个元素的具体结构描述见creditTaskOrder。|

### <div id="CreditTaskOrder">CreditTaskOrder</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**dataId**|String|False| |数据Id。需要保证在一次请求中所有的Id不重复|
|**content**|string|True| |待检测数据字符串，最长4096个字符，为可解析字符串json，数据结构如creditTaskOrderDetail|
|**resourceType**|String|True| |数据类型，order-订单|
### <div id="CreditTaskOrderDetail">CreditTaskOrderDetail</div>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**member_id**|String|True| |注册账号ID|
|**mobile**|String|True| |注册手机号，国内手机：11位手机号|
|**platform**|String|True| |设备类型，例如ios,android|
|**version**|String|True| |APP版本号，例如6.25.0|
|**signup_channel**|String|True| |注册渠道或注册终端，例如：APP、小程序|
|**timestamp**|String|True| |登录时间，用户登录完成时间，时间戳类型：YYYY-mm-dd HH:ii:ss:SSS  精确到毫秒，例如：2020-16-20 12:16:01:000|
|**device_id**|String|True| |注册设备号，设备指纹编码，例如7E8XXX|
|**ip**|String|True| |注册IP，用户注册IP，IPV4 或 IPV6|
|**receiver_phone**|String|True| |收货人手机号|
|**order_at**|String|True| |下单时间,时间戳类型：YYYY-mm-dd HH:ii:ss 精确到秒，例如：2021-04-17 12:17:45|
|**receiver_name**|String|True| |收货人姓名，例如张三\|F|
|**receiver_city**|String|True| |收货人城市|
|**receiver_area**|String|True| |收货人区域|
|**receiver_addr**|String|True| |收货人详细地址|
|**shop_id**|String|True| |门店id，例如：9344|
|**order_id**|String|True| |订单id|
|**goods_id_list**|String|False| |商品清单, 例如['1294265', '8775', '2214']|
|**order_amt**|Integer|False| |订单总额，double类型|
|**reduce_amt**|Integer|False| |优惠总额, double类型|
|**promotion_code**|Integer|False| |优惠码, 例如DJ-MRBK-329-331-59-6|
|**activity_code**|Integer|False| |活动码，例如DJ-MRBK-329-331|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#result)|API请求成功或者部分成功时返回数据|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**data**|[CreditResult[]](#creditresult)|结果数组|
### <div id="CreditResult">CreditResult</div>
|名称|类型|描述|
|---|---|---|
|**success**|Boolean|是否成功，没成功会在failMsg附上错误信息|
|**failMsg**|String|错误描述信息|
|**dataId**|String|对应请求的dataId|
|**inBWList**|String|是否命中黑白名单，black-在黑名单中 white-在白名单中 none-不在任何名单中|
|**content**|String|对应请求的内容|
|**resourceType**|String|数据类型，ip-IP，phone-手机，addr-地址，card-身份，pin-账户，eid-设备，signup-注册，login-登录，marketing-营销，order-订单|
|**scoreDetail**|[CreditScoreDetail](#creditscoredetail)|评分数据|
### <div id="CreditScoreDetail">CreditScoreDetail</div>
|名称|类型|描述|
|---|---|---|
|**riskTag**|String|风险类型，对应riskCode的中文描述|
|**riskCode**|String|风险类型编码，对应riskCode的分类：<br/>200-208手机综合风险，包括200-黑手机、201-异常注册、202-异常登录、203-营销刷券、204-下单黄牛、205-异常支付、206-恶意售后、207-猫池小号、208-订单风险、998-未知<br/>501-507IP综合风险，包括501-普通代理、 502-秒拨代理IP、503-真人作弊、504-设备伪装、505-地址伪装、506-黑软IP、507-爬虫IP、998-未知<br/>600-604注册综合风险，包括600-其他、601-机器批量注册、602-代理IP注册、603-黑卡注册、604-垃圾小号注册、998-未知<br/>700-703登录综合风险，包括700-其他、701-机器批量登录、702-撞库登录、703-代理IP登录、998-未知<br/>800-803营销综合风险，包括800-其他、801-批量刷券、802-黑手机、803-黑设备、998-未知<br/>904-手机风险、905-设备风险、906-地址风险、907-注册风险、908-IP风险、909-业务风险、998-未知<br>详见[标签说明](https://docs.jdcloud.com/cn/risk-detection/core-concepts)|
|**riskClass**|String|风险分类，包括ip，phone，addr，login，signup，marketing，order|
|**score**|String|风险评分，1-低风险 2-中低风险 3-中风险 4-中高风险 5-高风险 0-无风险|
|**scoreDesc**|String|对应score的中文描述，1-低风险 2-中低风险 3-中风险 4-中高风险 5-高风险 0-无风险|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Bad Request|

[其他常见错误码](https://docs.jdcloud.com/cn/common-declaration/api/error-codes)

注：当请求QPS超过购买的包年不限次套餐里面限定的QPS阈值后，会提示如下：

```
{
    "requestId": "xxxxx", 
    "error": {
        "status": "CREDITSCORE_REQUEST_LIMITEXCEEDED", 
        "code": 400, 
        "message": "请求的次数超过了频率限制"
    }
}
```



## 示例代码

```
请求：
method：
  post
body：
{
    "tasks": [
        {
            "dataId": "123456789101",
            "content": "{\"member_id\" :\"245553475215388000\",\"mobile\": \"18373200413\",\"platform\": \"ios\",\"version\": \"6.25.0\",\"signup_channel\":\"APP\",\"timestamp\":\"2020-12-3  19:29:55:686\",\"device_id\":\"mfpif4a7812299sfsnc1e51QVm2VfjhK0zKSJ7a0m17c2FWiOfYcfKyNnikFugnvWc6u2E5ra4sljT4TBvo/bz0RqZAqPJjr95MSktDCON/hDjv4jk4x\",\"ip\":\"5.5.5.5\",\"receiver_phone\":\"17719766030\",\"order_at\":\"2021-3-31 16:41:18\",\"receiver_name\":\"邱|F\",\"receiver_city\":\"渭南\",\"receiver_area\":\"金城花园-西门\",\"receiver_addr\":\"部队东门\",\"shop_id\":\"9533\",\"order_id\":\"1200000450023090\",\"goods_id_list\": \"['1294265', '8775', '2214']\",\"order_amt\": 100.061 ,\"reduce_amt\":44.781,\"promotion_code\":\"DJ-MRBK-329-331-59-6\",\"activity_code\":\"DJ-MRBK-329-331\"}",
            "resourceType": "order"
        }
    ]
}

返回:
{
    "requestId": "7db31e35-631c-4eae-b93c-c82455b5247f",
    "result": {
        "data": [
            {
                "success": true,
                "failMsg": "",
                "dataId": "123456789101",
                "content": "{\"member_id\" :\"245553475215388000\",\"mobile\": \"18373200413\",\"platform\": \"ios\",\"version\": \"6.25.0\",\"signup_channel\":\"APP\",\"timestamp\":\"2020-12-3  19:29:55:686\",\"device_id\":\"mfpif4a7812299sfsnc1e51QVm2VfjhK0zKSJ7a0m17c2FWiOfYcfKyNnikFugnvWc6u2E5ra4sljT4TBvo/bz0RqZAqPJjr95MSktDCON/hDjv4jk4x\",\"ip\":\"5.5.5.5\",\"receiver_phone\":\"17719766030\",\"order_at\":\"2021-3-31 16:41:18\",\"receiver_name\":\"邱|F\",\"receiver_city\":\"渭南\",\"receiver_area\":\"金城花园-西门\",\"receiver_addr\":\"部队东门\",\"shop_id\":\"9533\",\"order_id\":\"1200000450023090\",\"goods_id_list\": \"['1294265', '8775', '2214']\",\"order_amt\": 100.061 ,\"reduce_amt\":44.781,\"promotion_code\":\"DJ-MRBK-329-331-59-6\",\"activity_code\":\"DJ-MRBK-329-331\"}",
                "resourceType": "order",
                "scoreDetail": {
                    "riskTag": "未知",
                    "riskCode": "998",
                    "riskClass": "order",
                    "score": "0",
                    "scoreDesc": "未知"
                },
                "hitCache": "miss",
                "inBWList": "none"
            }
        ]
    }
}
```
