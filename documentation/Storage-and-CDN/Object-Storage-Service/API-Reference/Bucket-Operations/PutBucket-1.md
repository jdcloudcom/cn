# PutBucket

PutBucket用于创建Bucket（不支持匿名访问）。创建的Bucket所在的Region和发送请求的Endpoint所对应的Region一致。Bucket所在的数据中心确定后，该Bucket下的所有Object将一直存放在对应的地区。

请求语法
```
PUT / HTTP/1.1
Date: GMT Date
Authorization: signatureValue
Host: BucketName.s-bj.jcloud.com 
```

细节分析

1.如果请求的Bucket已经存在，并且请求者是所有者，返回409 Conflict， 错误码：BucketAlreadyOwnedByYou

2.如果请求的Bucket已经存在，但不是请求者所拥有的，返回409 Conflict。错误码：BucketAlreadyExists。

3.如果想创建的Bucket不符合命名规范，返回400 Bad Request消息。错误码：InvalidBucketName。

4.如果PutBucket的时候发现已经超过bucket最大创建数时，每个Region默认10个，返回400 Bad Request消息。错误码：TooManyBuckets。

请求示例
```
PUT / HTTP/1.1
Date: GMT Date
Authorization: signatureValue
Host: BucketName.s-bj.jcloud.com 
```
返回示例 
```
HTTP/1.1 201   Created
Server: nginx
Date: Tue, 11 Jul 2017   07:28:28 GMT
Content-Length: 0
Connection: keep-alive
x-jss-request-id:   AC661DAB5260B409
```
