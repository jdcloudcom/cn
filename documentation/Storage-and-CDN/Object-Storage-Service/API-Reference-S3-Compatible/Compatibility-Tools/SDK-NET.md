# SDK-.NET

## 概述

本文档基于[AWS .NET SDK](https://aws.amazon.com/cn/sdk-for-net/)编写。京东云对象存储支持AWS S3接口，具体兼容的接口可在
[兼容接口](../Compatibility-API/Compatibility-API-Overview.md)查看。

## 环境准备

请使用 .NET Framework 3.5 或更高版本的平台进行开发。

## 安装方式

安装AWS SDK for .NET，请参考安装[AWS-SDK程序集](https://docs.aws.amazon.com/zh_cn/sdk-for-net/v3/developer-guide/net-dg-install-assemblies.html?shortFooter=true)。

## 初始化Client

您可以创建S3Client，用于管理存储空间和文件等OSS资源。使用.NET SDK发起OSS请求，您需要使用您的AccessKey和SecretKey初始化一个S3Client，并根据需要修改Config的默认配置项。

以下为创建client的示例，更多.NET SDK示例请访问[S3 .NET Example Code](https://docs.aws.amazon.com/zh_cn/sdk-for-net/v3/developer-guide/s3-apis-intro.html?shortFooter=true)。

```C#
using Amazon.S3;

namespace Amazon.Samples.S3
{
    public class Test
    {
        const string accessKeyId = "<yourAccessKeyId>";
        const string accessKeySecret = "<yourAccessKeySecret>";
        const string endpoint = "s3.cn-north-1.jdcloud-oss.com";
        
        private static IAmazonS3 s3Client;
        
        public static void Main()
        {
            var s3ClientConfig = new AmazonS3Config
            {
                ServiceURL = endpoint,
                SignatureVersion = "4",
                UseHttp = true,
            };
            s3Client = new AmazonS3Client(accessKeyId, accessKeySecret, s3ClientConfig);
           
            //use s3 client to create bucket、put object....
        }
    }
}
```

## 上传文件
使用.NET s3Client上传文件。
```C#
// Create a PutObject request
PutObjectRequest request = new PutObjectRequest
{
    BucketName = "SampleBucket",
    Key = "Item1",
    ContentBody = "This is sample content...",
    UseChunkEncoding = false
};
 
// Put object
PutObjectResponse response = s3Client.PutObject(request);
```

注：需设置UseChunkEncoding为false，禁用Chunked-Encoding编码
