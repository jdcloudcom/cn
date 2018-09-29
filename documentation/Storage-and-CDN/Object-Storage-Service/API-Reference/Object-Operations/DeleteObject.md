# DeleteObject

此操作用于删除某个Object。

**请求语法**

```
DELETE  /ObjectName HTTP/1.1
Host: BucketName. s.jcloud.com
Date: GMT  Date     
Authorization:   signatureValue#请参照“访问控制”
```

细节分析

1.如果要删除的Object不存在，OSS也返回状态码404 Not Found(NoSuchKey)。

2.如果Bucket不存在，返回404 Not Found(NoSuchBucket)。

**请求示例**

```
DELETE /example.jpg HTTP/1.1
Host: oss-example.s-bj.jcloud.com
Date: Tue, 11 Jul 2017 07:37:23   GMT    
Authorization: jingdong   qbS5QXpLORrvdrmb:Qt+ThnjyLwBb9xMZ8PZG3wsj3qU=
```

**返回示例**

```
HTTP/1.1 204 No   Content
Server: nginx
Date: Tue, 11 Jul 2017   07:37:23 GMT
Connection: keep-alive
x-jss-request-id:   80EC9E2F4D29D732
X-Trace:   204-1499758643347-0-0-19-50-5
```
