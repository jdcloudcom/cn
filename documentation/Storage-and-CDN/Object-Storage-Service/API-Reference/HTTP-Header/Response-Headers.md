# 公共响应头

下面的表格是京东云存储 API 的返回的通用响应头（HTTP Headers），这些响应头可以被所有的请求所使用，定义如下：

|名称|描述|
---|---
|Content-Length|RFC2616中定义的HTTP请求内容长度。<br>类型：字符串<br>默认值：无<br>使用场景：需要向oss提交数据的请求|
|Connection|标明客户端和oss服务器之间的链接状态。<br>类型：枚举有效值：open、close<br>默认值：无|
|Date|云存储服务器响应本次请求的GMT时间戳，例如：Mon, 23 Feb 2013 03:14:57 GMT。<br>类型：时间<br>默认值：无|
|ETag|ETag是京东云存储中Object的Hash值，其仅反映Object的数据内容，而不包括元数据(Metadata)。需要注意的是ETag并不一定是一个MD5值，当Put Object操作完成时，服务端会为收到的数据生成MD5 摘要作为其ETag。而对于Multipart Upload产生的Object， 其ETag并不是内容的ContentMD5。<br>类型：字符串<br>默认值：无|
|x-oss-request-id|本次请求的唯一标识。若有错误发生时，客户可将该ID告诉京东云存储来帮助定位问题。<br>类型：字符串<br>默认值：无|
|x-powered-by|固定值为JingdongStorageService,表示该请求是由京东云存储完成。<br>类型：字符串<br>默认值：JingdongStorageService|
