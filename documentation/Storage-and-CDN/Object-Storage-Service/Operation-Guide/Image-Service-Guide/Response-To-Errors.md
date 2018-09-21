# 错误响应

当用户访问图片处理服务出现错误的时候，图片处理服务会返回给用户相应的错误码和错误信息，以帮助用户定位与处理问题。

## 图片处理服务错误的响应格式

错误响应的消息体例子：

```
{"code":"BadRequest","message":"BadRequest","resource":"/zsytest/example.jpg","requestId":"ADDB2C69B9FB23E9"}
```

错误包含以下元素：

Code：图片处理服务返回给用户的错误码。

Message：图片处理服务给出的详细错误信息。

Resource：处理的图片文件。

requestId：用以标识错误请求的唯一UUID，在无法解决问题时候，可以使用此错误ID发送给图片处理服务的工程师去定位错误的原因。

## 图片处理服务的错误码

|错误码|Message|描述|HTTP码|
|-|-|-|-|
|BadRequest|Bad Request|请求报文格式错误|400|
|NoSuchKey|The specified key does not exist.|资源不存在|404|
|AccessDenied|Access Denied|服务器拒绝请求|403|
|MethodNotAllowed|The specified method is not allowed against this resource.|MethodNotAllowed|405|
|InternalError|We encountered an internal error. Please try again.|服务器内部错误|500|
| — |unknown error|未知错误|400|
| — |wrong request para|请求参数错误|400|
| — |wong rocessing mode|处理模式错误|400|
| — |can't decode image|无法解码图片|400|
| — |processing error|理解错误|400|
| — |can't get response json|无法得到结果json|400|
| — |can't encode image|无法编码图片|400|
| — |can't copy image|无法复制图片|400|
| — |release error|清除资源错误|400|
