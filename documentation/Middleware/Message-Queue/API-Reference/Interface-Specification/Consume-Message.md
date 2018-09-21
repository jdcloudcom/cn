# 收消息

- 请求行

```http
GET {Http接入点}/v1/messages HTTP/1.1
```

- Request Parameters

| 字段名               | 字段类型   | 必填         | 说明                                                        |
| -------------------- | ---------- | ------------ | ----------------------------------------------------------- |
| topic                | string     | Required     |                                                             |
| consumerGroupId      | string     | Required     |                                                             |
| size                 | int32      | Optional     | 一次**最多**拉取消息条数，0 < size <=32，defaultValue = 32  |
| ~~consumerId~~       | ~~string~~ | ~~Optional~~ | ~~defaultValue = httpProxyId（传什么都没用）~~              |
| consumeFromWhere     | string     | Optional     | 默认的起始消费位置，可选值：HEAD、TAIL，defaultValue = HEAD |
| filterExpressionType | string     | Optional     | 消息过滤表达式类型，目前可选值只有TAG                       |
| filterExpression     | string     | Optional     | 消息过滤表达式，默认没有过滤                                |
| ack                  | bool       | Optional     | 拉消息时是否由服务端自动ACK，defaultValue = false           |

- Response Body

  1. 请求成功

  |  字段名   | 字段类型 | 说明                                                         |
  | :-------: | :------: | :----------------------------------------------------------- |
  | requestId |  string  | 本次请求的requestId，用于搜索调用链                          |
  |  result   |   map    | 返回格式为：`{"topicName":"lizhijian-041","ackIndex":31,"messages":[{"messageId":"messageId_1","messageBody":"test-0","properties":{"TAGS":"world"}},{"messageId":"messageId_2","messageBody":"test-2","properties":{"TAGS":"world"}}]}` |

  2. 请求失败

  |  字段名   | 字段类型 | 说明                                                         |
  | :-------: | :------: | ------------------------------------------------------------ |
  | requestId |  string  | 本次请求的requestId，用于搜索调用链                          |
  |   error   |   map    | 返回格式为：`{"code":500,"message":"Topic information query failure","status":"INTERNAL"}` |
