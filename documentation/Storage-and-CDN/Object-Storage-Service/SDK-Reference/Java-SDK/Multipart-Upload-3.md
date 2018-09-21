# 分片上传

对于大文件，可以切分成片上传。用户可以在如下的应用场景中（但不仅限于此）使用分片上传(Multipart Upload)模式：

* 需要支持断点上传。

* 上传超过900MB大小的文件。

* 网络条件较差，和OSS的服务器之间的链接经常断开。

* 上传文件之前，无法确定上传文件的大小。

分片上传(Multipart Upload)分为如下3个步骤:

* 初始化一个分片上传任务（InitiateMultipartUpload）

* 逐个或并行上传分片（UploadPart）

* 完成分片上传（CompleteMultipartUpload）或取消分片上传(AbortMultipartUpload)。

## 分步完成Multipart Upload

### 初始化Multipart Upload

使用分片上传模式前，必须先初始化一个Multipart Upload事件。该操作会返回一个OSS服务器创建的Upload ID，用于标识本次Multipart Upload事件。用户可以根据这个ID来发起相关的操作，如中止Multipart Upload、查询Multipart Upload等。调用jss.bucket(bucketName).object(key).initiateMultipartUpload初始化一个分片上传事件：
```
// endpoint以华北-北京为例，其它region请按实际情况填写  
String endpoint = "oss.cn-north-1.jcloudcs.com";  
//您的AccessKey和SecretKey可以登录到对象存储的控制台，在【Access Key 管理】中查看。  
String accessKey = "<yourAccessKey>";  
String SecretKey = "<yourSecretKey>";  
String bucketName = "<yourBucketName>";  
String key = "<yourObjcetkey>";  
// 创建JingdongStorageService实例  
Credential credential = new Credential(accessKey, secreteKey);  
//默认配置文件。如用户需要个别配置，则自行配置。例:config.setMaxConnections(20);  
ClientConfig config = new ClientConfig();  
JingdongStorageService jss= new JingdongStorageService (credential, config);  
//设置Endpoint  
jss.setEndpoint(endpoint);  
String storageClass =  StorageClass.ReducedRedundancy.toString();  
    
//使用低冗余存储，则使用该句代码  
//jss.bucket(bucketName).object(key).getBuilder().getHeaders().put(JssHeaders.X_JSS_STORAGE_CLASS, StorageClass.ReducedRedundancy.toString());  
InitMultipartUploadResult initResult = jss.bucket(bucketName).object(key).initMultipartUpload();  
jss.destroy();
```
提示：

* 用InitiateMultipartUploadRequest指定上传文件的名字和所属Bucket（Bucket）；

* initiateMultipartUpload 的返回结果中含有UploadId，它是区分分片上传事件的唯一标识，在后面的操作中将用到它。

### 上传分片

初始化一个Multipart Upload之后，可以根据指定的Object名和Upload ID来分片（Part）上传数据。每一个上传的Part都有一个标识它的号码——分片号（part number，范围是1-10,000）。如果你用同一个分片号码，上传了新的数据，那么OSS上已有的这个分片的数据将被覆盖。每个分片不需要按顺序上传，甚至可以在不同进程、不同机器上上传，OSS会按照分片号排序组成大文件。调用jss.bucket(bucketName).object(key).uploadPart上传分片：
```
List<UploadPartResult> uploadPartResults= new ArrayList<UploadPartResult>();  
InputStream inputStream = new FileInputStream(new File("<localFile>"));  
// 设置分片大小  
Long partSize = 700*1024;  
// 设置分片号，范围是1~10000，  
int partNum = 1;  
// 设置文件偏移量,第一个文件偏移为 0  
int fileOffset = 0;  
ByteStreams.skipFully(inputStream, fileOffset);  
  
UploadPartResult uploadPartResult = jss.bucket(bucketName).object(key).entity(partSize, inputStream).uploadPart(initResult.getUploadId(), partNum); 
uploadPartResults.add(uploadPartResult);
```

注意：

* OSS会将服务器端收到Part数据的MD5值放在ETag头内返回给用户。

* Part号码的范围是1~10000。如果超出这个范围，将返回400 ,错误码：TooManyParts。

* 每次上传part时都要把流定位到此次上传块开头所对应的位置。

* 每次上传part之后，OSS的返回结果是一个UploadPartResult对象，他是包含上传块的ETag与块编号（PartNumber）的组合，

* 在后续完成分片上传的步骤中会用到它，因此我们需要将其保存起来。一般来讲我们将这些 UploadPartResult对象保存到List中。

### 完成上传分片

所有分片上传完成后，需要调用Complete Multipart Upload来完成整个文件的Multipart Upload。在执行该操作时，需要提供所有有效的分片列表（包括分片号和分片ETAG）；OSS收到提交的分片列表后，会逐一验证每个分片的有效性。当所有的数据Part验证通过后，OSS将把这些分片组合成一个完整的Object。调用jss.bucket(bucketName).object(key).completeMultipartUpload完成分片上传：
```
Collections.sort(uploadPartResults, new Comparator<UploadPartResult>() {  
    @Override  
    public int compare(UploadPartResult p1, UploadPartResult p2) {  
        return p1.getPartNumber() - p2.getPartNumber();  
    }  
});  
String eTag = jss.bucket(bucketName).object(key).completeMultipartUpload(initResult.getUploadId(), uploadPartResults);
```
注意：

* 上面代码中的 uploadPartResults就是进行分片上传中保存的uploadPartResult的列表，它必须是按分片号升序排序；

* 分片可以是不连续的。

### 取消分片上传事件

您可以根据Upload ID中止对应的Multipart Upload事件。当一个Multipart Upload事件被中止后，就不能再使用这个Upload ID做任何操作，已经上传的Part数据也会被删除。调用jss.bucket(bucketName).object(key).abortMultipartUpload取消分片上传事件：
```
// endpoint以华北为例，其它region请按实际情况填写  
String endpoint = "s-bj.jcloud.com";  
//您的AccessKey和SecretKey可以登录到京东云存储的控制台，在【Access Key 管理】中查看。  
String accessKey = "<yourAccessKey>";  
String SecretKey = "<yourSecretKey>";  
String bucketName = "<your bucketName>";  
String key = "<your objcetkey>";  
 
// 创建JingdongStorageService实例  
Credential credential = new Credential(accessKey, secreteKey);  
//默认配置文件。如用户需要个别配置，则自行配置。例:config.setMaxConnections(20);  
ClientConfig config = new ClientConfig();  
JingdongStorageService jss= new JingdongStorageService (credential, config);
//设置Endpoint  
jss.setEndpoint(endpoint);  
 
// 取消分片上传，其中uploadId来自于initiateMultipartUpload  
jss.bucket(bucketName).object(key).abortMultipartUpload("<uploadId>");  
jss.destroy();
```

## 获取已上传的分片

列举指定的Upload ID所属的所有已经成功上传的分片，注意：如果一个分步上传事件已完成或取消，是无法列举出它的已上传的分片的。
```
// endpoint以华北-北京为例，其它region请按实际情况填写  
String endpoint = "oss.cn-north-1.jcloudcs.com";  
// 您的AccessKey和SecretKey可以登录到对象存储的控制台，在【Access Key 管理】中查看。  
String accessKey = "<your accessKey>";  
String secretKey = "<your secretKey>";  
String bucketName = "<your bucketName>";  
String key = “<you objectKey>”;  
       
// 创建JingdongStorageService实例  
Credential credential = new Credential(accessKey, secreteKey);  
//默认配置文件。如用户需要个别配置，则自行配置。例:config.setMaxConnections(20);  
ClientConfig config = new ClientConfig();  
JingdongStorageService jss= new JingdongStorageService (credential, config);
//设置Endpoint  
jss.setEndpoint(endpoint);  
  
// 获取已上传分片，其中initResult来自于initiateMultipartUpload  
ListPartsResult partList = jss.bucket(bucketName).object(key).listParts(initResult.getUploadId());  
for (PartSummary part : partListing.getParts()) {  
 // 分片号，上传的时候指定  
    part.getPartNumber();  
    // 分片数据大小  
    part.getSize();  
    // Part的ETag  
    part.getETag();  
    // Part的最后修改上传  
    part.getLastModified();  
}  
// 关闭client  
jss.destroy();
```

## 获取Bucket内所有分片上传事件

列举一个Bucket空间下的所有分步上传事件，注意：如果一个分步上传事件已完成或取消，是无法列举出该事件的。
```
// endpoint以华北为例，其它region请按实际情况填写  
String endpoint = "oss.cn-north-1.jcloudcs.com";  
// 您的AccessKey和SecretKey可以登录到对象存储的控制台，在【Access Key 管理】中查看。  
String accessKey = "<your accessKey>";  
String secretKey = "<your secretKey>";  
String bucketName = "<your bucketName>";  
      
// 创建JingdongStorageService实例  
Credential credential = new Credential(accessKey, secreteKey);  
//默认配置文件。如用户需要个别配置，则自行配置。例:config.setMaxConnections(20);  
ClientConfig config = new ClientConfig();  
JingdongStorageService jss= new JingdongStorageService (credential, config);
//设置Endpoint  
jss.setEndpoint(endpoint);  
// 列举分片上传事件  
BucketService bucketService = jss.bucket(bucketName);  
//增加前缀匹配  
//bucketService.prefix("<your perfix>");  
MultipartUploadListing multipartUploadListing = bucketService.listMultipartUploads();

for (Upload upload : multipartUploadListing.getUploads()) {  
        //Upload Id  
        upload.getUploadId();  
        //key  
        upload.getKey();  
        //date of initiate multipart ipload  
        upload.getInitiated();  
}  
// 关闭client  
jss.destroy();
```
