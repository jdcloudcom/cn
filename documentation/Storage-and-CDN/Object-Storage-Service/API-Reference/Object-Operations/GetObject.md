# GetObject

此操作用于获取指定的Object内容

**请求语法**

```
GET /ObjectName   HTTP/1.1
Host: BucketName. s.jcloud.com
Date: GMT   Date     
Authorization:   signatureValue#请参照“访问控制”
Range: bytes=ByteRange(可选)
```
**请求Header**


Range 指定获取的Object数据内容，如设定   bytes=0-9，表示传送第0到第9这10个字符，更多的信息可以参看《RFC2616》

细节分析
1.GetObject通过range参数可以支持断点续传，对于比较大的Object建议使用该功能。

2.如果在请求头中使用Range参数；则返回消息中会包含整个文件的长度和此次返回的范围，例如：Content-Range: bytes 0-9/44，表示整个文件长度为44。

3.如果文件不存在，返回404 Not Found错误。错误码：NoSuchKey。

4.若该Object为进行服务器加密存储的，则在GET请求时会自动解密返回给用户。

**请求示例**

```
GET /example.jpg HTTP/1.1
Host: oss-example.s-bj.jcloud.com
Date: Tue, 11 Jul 2017   07:28:01 GMT    
Authorization: jingdong qbS5QXpLORrvdrmb:Ctm+uA40JmY3T3LvCZ6CkKkANXs=
```
**返回示例**

```
HTTP/1.1 200 OK
Server: nginx
Date: Tue, 11 Jul 2017   07:28:01 GMT
Content-Type: text/plain
Content-Length: 13
Connection: keep-alive
x-jss-request-id:   95CB505F50E9341D
Cache-Control:   max-age=2592000
Content-Disposition: inline;   filename="example.jpg"
Accept-Ranges: bytes
ETag:   "6457646542258052f767868fd686d74d"
Last-Modified: Tue, 11 Jul   2017 07:27:15 GMT
x-jss-storage-class: STANDARD
X-Trace: 200-1499758081049-0-0-19-45-45
```
**Range请求示例**

```
GET example.jpg HTTP/1.1
Host: oss-example.s-bj.jcloud.com
Range: bytes=0-9   
Date: Tue, 11 Jul 2017 07:34:11   GMT    
Authorization: jingdong qbS5QXpLORrvdrmb:/Aaawoo0xVq4XVMei/yK1UqhoFc=
```
**Range返回示例**

```
HTTP/1.1 206   Partial Content
Server: nginx
Date: Tue, 11 Jul 2017   07:34:11 GMT
Content-Type: text/plain
Content-Length: 10
Connection: keep-alive
Content-Range: bytes 0-9/13
x-jss-request-id:   A0D975825710D969
Cache-Control:   max-age=2592000
Content-Disposition: inline;   filename="example.jpg"
Accept-Ranges: bytes
ETag:   "6457646542258052f767868fd686d74d"
Last-Modified: Tue, 11 Jul   2017 07:27:15 GMT
x-jss-storage-class: STANDARD
X-Trace:   206-1499758451594-0-0-20-44-44
```
