# 发消息

- 请求行

```http
POST {Http接入点}/v1/messages HTTP/1.1
```

- Request Body

  Request Body为JSON格式，其中包含的字段如下：

|  字段名  |    字段类型     | 是否必填 | 说明                       |
| :------: | :-------------: | :------: | :------------------------- |
|  topic   |     string      | Required |                            |
|   type   |     string      | Required | NORMAL, ORDER, TRANSACTION |
| messages | list of Message | Required | 1 <= 消息条数 <= 32        |

  其中Message为Map类型，包含的字段如下：

|    字段名    |      字段类型       | 是否必填 | 说明                       |
| :----------: | :-----------------: | :------: | -------------------------- |
|     body     |       string        | Required | 消息长度不超过256K         |
| delaySeconds |        int32        | Optional | 0 <= delaySeconds <= 86400 |
|     tag      |       string        | Optional | 仅支持单Tag                |
|  properties  | map<string, string> | Optional | 用户自定义键值对           |

- Response Body

  1. 请求成功

  |  字段名   | 字段类型 | 说明                                                        |
  | :-------: | :------: | :---------------------------------------------------------- |
  | requestId |  string  | 本次请求的requestId，用于搜索调用链                         |
  |  result   |   map    | 返回格式为：`{"messageIds":["messageId_1", "messageId_2"]}` |

  2. 请求失败

  | 字段名    | 字段类型 | 说明                                                         |
  | --------- | -------- | ------------------------------------------------------------ |
  | requestId | string   | 本次请求的requestId，用于搜索调用链                          |
  | error     | map      | 返回格式为：`{"code":403,"message":"Authentication failed","status":"PERMISSION_DENIED"}` |
