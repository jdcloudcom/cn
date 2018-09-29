# 生成预签名URL

## 实现方式

1.配置依赖

在pom.xml中配置依赖的sdk,如下：
```
<dependency>
<groupId>com.amazonaws</groupId>
<artifactId>aws-java-sdk</artifactId>
<version>1.11.136</version>
</dependency>
```

2.示例代码

生成带有签名的URL示例代码如下：
```
import java.net.URL;
import com.amazonaws.ClientConfiguration;
import com.amazonaws.Protocol;
import com.amazonaws.SDKGlobalConfiguration;
import com.amazonaws.auth.AWSCredentials;
import com.amazonaws.auth.BasicAWSCredentials;
import com.amazonaws.services.s3.AmazonS3;
import com.amazonaws.services.s3.AmazonS3Client;
import com.amazonaws.services.s3.S3ClientOptions;
import com.amazonaws.services.s3.model.GeneratePresignedUrlRequest;
 
public class GeneratePresignUrl {   
   static AmazonS3 createS3Client(String accessKey, String secretKey, String endpoint) {
      System.setProperty(SDKGlobalConfiguration.ENABLE_S3_SIGV4_SYSTEM_PROPERTY, "true");
      AWSCredentials awsCredentials = new BasicAWSCredentials(accessKey,secretKey);
      ClientConfiguration config = new ClientConfiguration();
      config.setProtocol(Protocol.HTTP);
      AmazonS3 s3 = new AmazonS3Client(awsCredentials,config);
      s3.setEndpoint(endpoint);
      S3ClientOptions options = new S3ClientOptions();
      options.withChunkedEncodingDisabled(true); // Must have
      s3.setS3ClientOptions(options);
      return s3;
   }
   static public URL generatePresignUrl(String accessKey, String secretKey, String endpoint,String bucketName,String keyName) {
      AmazonS3 s3 = createS3Client(accessKey,secretKey,endpoint);
      GeneratePresignedUrlRequest request = new GeneratePresignedUrlRequest(bucketName, keyName);
      return s3.generatePresignedUrl(request);
   }
   static public void main(String []str) {
      final String accessKey = "<your accessKey>";
      final String secretKey = "<your secretKey>";
      final String endpoint = "<your endpoint>";
      final String bucketName = "<your bucketname>";
      final String keyName = "<your keyname>";
      System.out.println(generatePresignUrl(accessKey, secretKey, endpoint, bucketName, keyName));
   }  
}
```
