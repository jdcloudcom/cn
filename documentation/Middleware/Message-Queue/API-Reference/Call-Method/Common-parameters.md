# 公共参数

## 公共请求头

| 头部字段名 | 字段类型 | 是否必填 | 说明                                                         |
| ---------- | -------- | -------- | ------------------------------------------------------------ |
| accessKey  | string   | Required | 用户申请的accessKey                                          |
| signature  | string   | Required | 使用secretKey对signSource进行**hmac-sha1**加密得到的字符串，signSource生成规则在下面 |
| dateTime   | string   | Required | 本次http请求发出的UTC时间，格式为ISO-8601:2004，示例：2018-08-14T03:37Z |
