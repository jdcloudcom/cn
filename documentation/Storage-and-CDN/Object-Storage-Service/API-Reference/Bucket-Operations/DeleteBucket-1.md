# DeleteBucket

Delete Bucket用于删除某个Bucket。 

**请求语法**
```
DELETE / HTTP/1.1
Host: BucketName. s-bj.jcloud.com
Date: GMT Date
Authorization: signatureValue
```
细节分析 

1.如果Bucket不存在，返回404  错误。错误码：NoSuchBucket。

2.为了防止误删除的发生，OSS不允许用户删除一个非空的Bucket。

3.如果试图删除一个不为空的Bucket，返回409 Conflict错误，错误码：BucketNotEmpty。

4.只有Bucket的拥有者才能删除这个Bucket。如果试图删除一个没有对应权限的Bucket，返回403 Forbidden错误。错误码：AccessDenied。

**请求示例**
```
DELETE / HTTP/1.1
Date: Tue, 11 Jul 2017   07:01:25 GMT
Authorization: jingdong   qbS5QXpLORrvdrmb:he65YAWaAh7cV1D2RmaKABAu9dk=
Host: oss-test.s-bj.jcloud.com
Connection: Keep-Alive
```

**返回示例** 
```
HTTP/1.1 204 No   Content
Server: nginx
Date: Tue, 11 Jul 2017   07:01:24 GMT
Connection: keep-alive
x-jss-request-id:   8DFE3EA7D288983C
```
