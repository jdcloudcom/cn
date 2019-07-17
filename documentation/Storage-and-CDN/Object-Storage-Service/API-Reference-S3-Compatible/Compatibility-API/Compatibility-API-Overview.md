# 兼容接口列表

京东云OSS兼容 AWS S3的接口及说明如下：
# 关于 Service 操作
|对象存储支持的api|api简介|JD Cloud S3 API参考| AWS S3 API参考 |
|-|-|-|-|
|GET Service（List Bucket）|获取一个User下的所有Bucket|兼容[GET Service](./Service-Related/Get-Service-2.md)| [GET Service](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTServiceGET.html)|

# 关于 Bucket 操作

|对象存储支持的api|api简介|JD Cloud S3 API参考| AWS S3 API参考 |
|-|-|-|-|
|PUT Bucket|新建一个Bucket，默认的权限为Private|兼容[PUT Bucket](./Operations-On-Bucket/Put-Bucket-2.md)| [PUT Bucket](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketPUT.html)|
|HEAD Bucket|确定一个Bucket是否存在且有权利访问<br>如果Bucket存在且有权利访问，则返回200 OK。如果指定的bucket不存在，则返回404 Not Found|兼容[HEAD Bucket](./Operations-On-Bucket/Head-Bucket-2.md)| [HEAD Bucket](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketHEAD.html)|
|GET Bucket（List Object）|获取某个Bucket下的部分或者全部Object信息（兼容Version2）|兼容[GET Bucket](./Operations-On-Bucket/Get-Bucket-2.md)| [GET Bucket](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/v2-RESTBucketGET.html)|
|DELETE Bucket|删除指定的Bucket|兼容[DELETE Bucket](./Operations-On-Bucket/Delete-Bucket-2-Compatibility-API.md)| [DELETE Bucket](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketDELETE.html)|
|List MultiPart Uploads|获取一个Bucket下面正在进行的分块上传任务|兼容[List MultiPart Uploads](./Operations-On-Bucket/List-Multipart-Uploads-2.md)| [List MultiPart Uploads](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/mpUploadListMPUpload.html)|
|GET Bucket policy|获取指定的Bucket上的policy|兼容[GET Bucket policy](./Operations-On-Bucket/Get-Bucket-Policy-2.md)| [GET Bucket policy](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketGETpolicy.html)|
|PUT Bucket policy|为指定的Bucket上添加或编辑policy|兼容[PUT Bucket policy](./Operations-On-Bucket/Put-Bucket-Policy-2.md)| [PUT Bucket policy](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketPUTpolicy.html)|
|DELETE Bucket policy|删除指定的Bucket上的policy|兼容[DELETE Bucket policy](./Operations-On-Bucket/Delete-Bucket-Policy-2.md)| [DELETE Bucket policy](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketDELETEpolicy.html)|
|PUT Bucket acl|在指定的Bucket上设置acl|兼容[PUT Bucket acl](./Operations-On-Bucket/Put-Bukcet-acl-2.md)| [PUT Bucket acl](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketPUTacl.html)|
|GET Bucket acl|获取指定的Bucket的acl|兼容[GET Bucket acl](./Operations-On-Bucket/GET-Bucket-Acl-2.md)| [GET Bucket acl](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketGETacl.html)|
|PUT Bucket cors|为指定的Bucket添加CORS规则|兼容[PUT Bucket cors](./Operations-On-Bucket/Put-Bucket-Cors-2.md)| [PUT Bucket cors](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketPUTcors.html)|
|GET Bucket cors|获取指定的Bucket的CORS规则|兼容[GET Bucket cors](./Operations-On-Bucket/Get-Bucket-Cors-2.md)| [GET Bucket cors](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketGETcors.html)|
|DELETE Bucket cors|删除指定的Bucket的CORS规则|兼容[DELETE Bucket cors](./Operations-On-Bucket/Delete-Bucket-Cors-2.md)| [DELETE Bucket cors](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketDELETEcors.html)|
|PUT Bucket website|为指定的Bucket添加静态网站托管规则（注：接口兼容，但规则细节与S3有出入）|兼容[PUT Bucket website](./Operations-On-Bucket/Put-Bucket-Website-2.md)| [PUT Bucket website](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketDELETEcors.html)|
|GET Bucket website|获取指定的Bucket的静态网站托管规则（注：接口兼容，但规则细节与S3有出入）|兼容[GET Bucket website](./Operations-On-Bucket/Get-Bucket-Website-2.md)| [GET Bucket website](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketDELETEcors.html)|
|DELETE Bucket website|删除指定的Bucket的静态网站托管规则（注：接口兼容，但规则细节与S3有出入）|兼容[DELETE Bucket website](./Operations-On-Bucket/Delete-Bucket-Website-2.md)| [DELETE Bucket website](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketDELETEcors.html)|
|PUT Bucket Replication|创建、修改跨区域复制配置|未支持：Account，Role，Owner AccessControlTranslation SourceSelectionCriteria<br>兼容[PUT Bucket Replication](./Operations-On-Bucket/Put-Bucket-Replication-2.md)|[PUT Bucket Replication](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketPUTreplication.html)|
|GET Bucket Replication|返回设置在Bucket上的跨区域复制配置|兼容[GET Bucket replication](./Operations-On-Bucket/Get-Bucket-Replication-2.md)|[GET Bucket replication](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketGETreplication.html)|
|DELETE Bucket Replication|删除已开启的跨区域复制配置，删除后目标Bucket和objcet依然存在|兼容[Delete Bucket replication](./Operations-On-Bucket/Delete-Bucket-Replication-2.md)|[Delete Bucket replication](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketDELETEreplication.html)|
|PUT Bucket notification|指定Bucket添加回调通知配置|未支持：CloudFunction，Queue<br>仅支持：Topic <br>详见 [回调通知](../../Operation-Guide/Manage-Bucket/Callback-Notification-2.md) <br>兼容[PUT Bucket notification](./Operations-On-Bucket/PUT-Bucket-Notification-2.md)|[PUT Bucket notification](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketPUTnotification.html)|
|GET Bucket notification|返回设置在Bucket上的回调通知配置|兼容[GET Bucket notification](./Operations-On-Bucket/GET-Bucket-Notification-2.md)|[GET Bucket notification](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketGETnotification.html)|
|GET Bucket encryption|返回用户对于OSS存储空间的默认加密配置|兼容[GET Bucket encryption](./Operations-On-Bucket/Get-Bucket-Encryption-2.md)|[GET Bucket encryption](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketGETencryption.html)|
|PUT Bucket encryption|用于设定bucket默认加密方式置|兼容[PUT Bucket encryption](./Operations-On-Bucket/Put-Bucket-Encryption-2.md)|[PUT Bucket encryption](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketPUTencryption.html)|
|DELETE Bucket encryption|删除OSS存储空间的默认加密配置|兼容[DELETE Bucket encryption](./Operations-On-Bucket/Delete-Bucket-Encryption-2.md)|[DELETE Bucket encryption](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketDELETEencryption.html)|
|PUT Bucket lifecycle|设置Bucket的生命周期规则|未支持：Transition、AbortIncompleteMultipartUpload<br>兼容：[PUT Bucket lifecycle](./Operations-On-Bucket/Put-Bucket-Lifecycle.md)|[PUT Bucket lifecycle](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketPUTlifecycle.html)|
|GET Bucket lifecycle|设置Bucket的生命周期规则|兼容：[GET Bucket lifecycle](./Operations-On-Bucket/Get-Bucket-Lifecycle.md)|[GET Bucket lifecycle](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketGETlifecycle.html)|
|DELETE Bucket lifecycle|删除Bucket的生命周期规则|兼容：[DELETE Bucket lifecycle](./Operations-On-Bucket/Delete-Bucket-Lifecycle.md)|[DELETE Bucket lifecycle](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTBucketDELETElifecycle.html)|

# 关于 Object 操作 

|对象存储支持的api|api简介|JD Cloud S3 API参考| AWS S3 API参考 |
|-|-|-|-|
|PUT Object|上传一个Object到OSS|兼容[PUT Object](./Operations-On-Objects/Put-Object-2.md)| [PUT Object](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTObjectPUT.html)
|GET Object|获取一个Object的Meta及数据，可以获取全部数据或者使用Range指定获取部分数据|兼容[GET Object](./Operations-On-Objects/Get-Object-2.md)| [GET Object](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTObjectGET.html)|
|HEAD Object|获取一个Object的Meta|兼容[HEAD Object](./Operations-On-Objects/Head-Object-2.md)| [HEAD Object](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTObjectHEAD.html)|
|DELETE Object|删除一个Object|兼容[DELETE Object](./Operations-On-Objects/Delete-Object-2.md)| [DELETE Object](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTObjectDELETE.html)|
|Delete Multiple Objects|支持用户通过一个HTTP请求删除同一个Bucket中的多个Object|未支持：version<br>兼容[Delete Multiple Objects](./Operations-On-Objects/Delete-Multiple-Objects-2.md)|[Delete Multiple Objects](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/multiobjectdeleteapi.html)|
|Initiate MultiPart Upload|初始化一个多步上传的任务|兼容[Initiate Mutipart Upload](./Operations-On-Objects/Initiate-Multipart-Upload-2.md)| [Initiate MultiPart Upload](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/mpUploadInitiate.html)|
|Upload Part|上传一个Part到OSS|兼容[Upload Part](./Operations-On-Objects/Upload-Part-2.md)| [Upload Part](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/mpUploadUploadPart.html)|
|Complete MultiPart Upload|把上传的多个part合并成一个Object|兼容[Complete Multipart Upload](./Operations-On-Objects/Complete-Multipart-Upload-2.md)| [Complete MultiPart Upload](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/mpUploadComplete.html)|
|Abort MultiPart Upload|终止一个分块上传任务并删除已上传的块|兼容[Abort MultiPart Upload](./Operations-On-Objects/Abort-Multipart-Upload-2.md)| [Abort MultiPart Upload](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/mpUploadAbort.html)|
|List Parts|获取特定分块上传操作中的已上传的块|兼容[List Parts](./Operations-On-Objects/List-Parts-2.md)| [List Parts](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/mpUploadListParts.html)|
|POST Object|通过表单上传文件到OSS|兼容[POST Object](./Operations-On-Objects/Post-Object-2.md)|[POST Object](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTObjectPOST.html)|
|Put Object Copy|拷贝一个在OSS上已经存在的object成另外一个object|未支持：x-amz-copy-source-if-match，<br>x-amz-copy-source-if-none-match，<br>x-amz-copy-source-if-unmodified-since，<br>x-amz-copy-source-if-modified-since，<br>x-amz-tagging-directive<br>x-amz-storage-class<br>支持STANDARD和REDUCED_REDUNDANCY<br>兼容[PUT Object - Copy](./Operations-On-Objects/Put-Object-Copy-2.md)|[PUT Object - Copy](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTObjectCOPY.html)|
|Upload Part Copy|通过从一个已存在的Object中拷贝数据来上传一个Part。|未支持：x-amz-copy-source-if-match，<br>x-amz-copy-source-if-none-match，<br>x-amz-copy-source-if-unmodified-since，<br>x-amz-copy-source-if-modified-since<br>兼容[Upload Part - Copy](./Operations-On-Objects/Upload-Part-Copy-2.md)|[Upload Part - Copy](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/mpUploadUploadPartCopy.html)|
|POST Object restore|恢复归档存储对象得到临时副本|未支持:Select <br>兼容[POST Object restore](./Operations-On-Objects/Post-Object-Restore.md)|[POST Object restore](https://docs.aws.amazon.com/zh_cn/AmazonS3/latest/API/RESTObjectPOSTrestore.html)|
