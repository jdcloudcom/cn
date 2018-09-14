# 管理文件

在OSS中，用户可以通过一系列的接口管理存储空间(Bucket)中的文件(Object)，比如ListObjects，DeleteObject，MoveObject等。Object的名字又称为key或object key。

## 列出存储空间中的文件

获取bucket下object列表，返回结果按照key做字典排序，默认返回前1000条数据，如有更多数据数据objectList hasNext()返回true，没有返回false。

**列出全部对象**

列举出Bucket下所有的Object：
```
//您的AccessKey和SecretKey可以登录到对象存储的控制台，在【Access Key 管理】中查看。  
String accessKey =  "<yourAccessKeyId>";  
String secreteKey = "<yourSecretKey>";       
// endpoint以华北-北京为例，其它region请按实际情况填写  
String endPoint = "oss.cn-north-1.jcloudcs.com";  
String bucketName = "<yourBucketName>";  
  
//ClientConfig当前为默认配置，用户可根据需要自行配置，如设置连接超时时间等  
ClientConfig config = new ClientConfig();   
  
//构造JingdongStorageService实例  
Credential credential = new Credential(accessKey, secreteKey);  
JingdongStorageService jss = new JingdongStorageService(credential,config); 
//配置endPoint  
jss.setEndpoint(endPoint);  
          
//创建BucketService实例  
BucketService bucketService = jss.bucket(bucketName);  
//列出bucket下满足条件的文件和文件夹  
ObjectListing objectList = bucketService.listObject();  
//列出指定条件下的object名称  
for (ObjectSummary objectSummary : objectList.getObjectSummaries()) {  
    System.out.println("objectName : "+objectSummary.getKey());  
}  

//JingdongStorageService对象内部维护一组HTTP连接池，在不使用该对象之前需要调用其destroy方法关闭连接池，  
//请注意，一旦调用destroy方法，该对象就不能再次被使用，否则将会抛出异常。  
jss.destroy();
```

**指定最大返回条数**
```
//创建BucketService实例  
BucketService bucketService = jss.bucket(bucketName);  
//指定返回最大条数为10  
bucketService.maxKeys(10);  
//列出bucket下满足条件的文件和文件夹  
ObjectListing objectList = bucketService.listObject();  
//列出指定条件下的object名称  
for (ObjectSummary objectSummary : objectList.getObjectSummaries()) {  
     System.out.println("objectName : "+objectSummary.getKey());  
}
```

**返回指定前缀的Object**

```
//创建BucketService实例  
BucketService bucketService = jss.bucket(bucketName);  
//指定返回前缀  
bucketService.prefix("file");  
//列出bucket下满足条件的文件和文件夹  
ObjectListing objectList = bucketService.listObject();  
//列出指定条件下的object名称  
for (ObjectSummary objectSummary : objectList.getObjectSummaries()) {  
     System.out.println("objectName : "+objectSummary.getKey());  
}
```

**从指定Object后返回**

```
//创建BucketService实例  
BucketService bucketService = jss.bucket(bucketName);  
//返回"file"后以字典序排序的Object信息，结果中不包含"file"  
bucketService.marker("file");  
//列出bucket下满足条件的文件和文件夹  
ObjectListing objectList = bucketService.listObject();  
//列出指定条件下的object名称  
for (ObjectSummary objectSummary : objectList.getObjectSummaries()) {  
     System.out.println("objectName : "+objectSummary.getKey());  
}
```

**分页获取所有Objcet**

```
String marker = null;  
ObjectListing objectList = null;  
do {  
     System.out.println(".................page....................");  
      //创建BucketService实例  
     BucketService bucketService = jss.bucket(bucketName);  
     //返回marker后以字典序排序的Object信息，结果中不包含marker  
    bucketService.marker(marker);  
    //指定返回最大条数为5  
    bucketService.maxKeys(5);  
    //列出bucket下满足条件的文件和文件夹  
    objectList = bucketService.listObject();  
    //列出指定条件下的object名称  
    List<ObjectSummary> objectSummaries = objectList.getObjectSummaries();  
    for (ObjectSummary objectSummary : objectSummaries) {  
         System.out.println("objectName : "+objectSummary.getKey());  
    }  
    marker = objectSummaries.get(objectSummaries.size()-1).getKey();  
} while (objectList.isHasNext());
```

**分页获取所有特定Objcet后的Object**

分页获取所有特定Object后的Object，每页maxKeys条Object。

```
//分页获取"file"后以字典序排序的Object信息，结果中不包含"file"  
String marker = "file";  
ObjectListing objectList = null;  
do {  
    System.out.println(".................page....................");  
    //创建BucketService实例  
    BucketService bucketService = jss.bucket(bucketName);  
    //返回marker后以字典序排序的Object信息，结果中不包含marker  
    bucketService.marker(marker);  
    //指定返回最大条数为5  
    bucketService.maxKeys(5);  
    //列出bucket下满足条件的文件和文件夹  
    objectList = bucketService.listObject();  
    //列出指定条件下的object名称  
    List<ObjectSummary> objectSummaries = objectList.getObjectSummaries();  
    for (ObjectSummary objectSummary : objectSummaries) {  
        System.out.println("objectName : "+objectSummary.getKey());  
    }  
    marker = objectSummaries.get(objectSummaries.size()-1).getKey();  
} while (objectList.isHasNext());
```

**分页获取所有指定前缀的Object**

分页获取所有指定前缀的Object，每页maxKeys条Object。

```
String marker = null;  
ObjectListing objectList = null;  
do {  
    System.out.println(".................page....................");  
    //创建BucketService实例  
    BucketService bucketService = jss.bucket(bucketName);  
    //指定返回前缀的object  
    bucketService.prefix("file");  
    //返回marker后以字典序排序的Object信息，结果中不包含marker  
    bucketService.marker(marker);  
    //指定返回最大条数为5  
    bucketService.maxKeys(5);  
    //列出bucket下满足条件的文件和文件夹  
    objectList = bucketService.listObject();  
    //列出指定条件下的object名称  
    List<ObjectSummary> objectSummaries = objectList.getObjectSummaries();  
    for (ObjectSummary objectSummary : objectSummaries) {  
        System.out.println("objectName : "+objectSummary.getKey());  
    }  
    marker = objectSummaries.get(objectSummaries.size()-1).getKey();  
} while (objectList.isHasNext());
```

## 模拟文件夹功能

您可以通过 Delimiter 和 Prefix 参数的配合模拟出文件夹功能。Delimiter 和 Prefix 的组合效果是这样的：

如果把 Prefix 设为某个文件夹名，就可以罗列以此 Prefix 开头的文件，即该文件夹下递归的所有的文件和子文件夹（目录）。

如果再把 Delimiter 设置为 “/” 时，返回值就只罗列该文件夹下的文件和子文件夹（目录），该文件夹下的子文件名（目录）返回在 CommonPrefixes 部分，子文件夹下递归的文件和文件夹不被显示。

提示：假设Bucket中有4个文件： oss.jpg， jingdong/file， jingdong/dir/file1， jingdong/dir/file2 ， “/” 作为文件夹的分隔符。下面的示例展示了如何模拟文件夹功能。

**列出存储空间内所有文件**

当我们需要获取存储空间下的所有文件时，可以这样写：

```
//创建BucketService实例  
BucketService bucketService = jss.bucket(bucketName);  
//列出bucket下满足条件的文件和文件夹  
ObjectListing objectList = bucketService.listObject();  
//列出指定条件下的object名称  
System.out.println("objectName : ");  
for (ObjectSummary objectSummary : objectList.getObjectSummaries()) {  
    System.out.println(objectSummary.getKey());  
}  
//列出指定条件下的文件夹  
System.out.println("\nCommonPrefixes : ");  
for (String commonPrefixes : objectList.getCommonPrefixes()) {  
    System.out.println(commonPrefixes);  
}
```
输出：

```
objectName :   
jingdong/dir/file1  
jingdong/dir/file2  
jingdong/file  
oss.jpg  
  
CommonPrefixes :
```

**递归列出目录下所有文件**

我们可以通过设置 Prefix 参数来获取某个目录（jingdong/）下所有的文件：

```
//创建BucketService实例  
BucketService bucketService = jss.bucket(bucketName);  
//获取"jingdong/"下所有的文件  
bucketService.prefix("jingdong/");  
//列出bucket下满足条件的文件和文件夹  
ObjectListing objectList = bucketService.listObject();  
//列出指定条件下的object名称  
System.out.println("objectName : ");  
for (ObjectSummary objectSummary : objectList.getObjectSummaries()) {  
    System.out.println(objectSummary.getKey());  
}  
//列出指定条件下的文件夹  
System.out.println("\nCommonPrefixes : ");  
for (String commonPrefixes : objectList.getCommonPrefixes()) {  
    System.out.println(commonPrefixes);  
}
```

输出：

```
objectName :   
jingdong/dir/file1  
jingdong/dir/file2  
jingdong/file  
  
CommonPrefixes :
```

**列出目录下的文件和子目录**

在 Prefix 和 Delimiter 结合的情况下，可以列出目录（jingdong/）下的文件和子目录。需要注意的是， HasCommonPrefix必须为true才生效：

```
//创建BucketService实例  
BucketService bucketService = jss.bucket(bucketName);  
//列出"jingdong/"下的文件和子目录,需要注意的是hasCommonPrefix必须为true才生效
bucketService.prefix("jingdong/").delimiter("/").hasCommonPrefix(true);  
//列出bucket下满足条件的文件和文件夹  
ObjectListing objectList = bucketService.listObject();  
//列出指定条件下的object名称  
System.out.println("objectName : ");  
for (ObjectSummary objectSummary : objectList.getObjectSummaries()) {  
     System.out.println(objectSummary.getKey());  
}  
//列出指定条件下的文件夹  
System.out.println("\nCommonPrefixes : ");  
for (String commonPrefixes : objectList.getCommonPrefixes()) {  
    System.out.println(commonPrefixes);  
}
```

输出：

```
objectName :   
jingdong/file  
 
CommonPrefixes :   
jingdong/dir
```

提示：

* 返回的结果中，ObjectSummaries 的列表中给出的是jingdong目录下的文件。

* 而 CommonPrefixs 的列表中给出的是jingdong目录下的所有子文件夹。可以看出 jingdong/dir/file1，jingdong/dir/file2两个文件并没有被列出来，因为它们属于jingdong文件夹下的dir目录。
