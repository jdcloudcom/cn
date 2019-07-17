# 使用临时秘钥访问OSS

## 应用场景
对于客户端应用，把访问密钥放到客户端代码中，这既容易泄露您的密钥信息，也不便于控制用户访问权限。类似这种需临时访问的场景可以使用STS来完成。STS可以指定复杂的策略来进行限制，仅提供最小的权限。

京东云STS服务提供了一种临时访问授权。通过STS可以获取临时的AccessKey、secretKey及Token，在有效期内，该临时秘钥可以用来访问OSS。

相关术语：
- STS：安全凭证服务（Security Token Service），提供临时访问授权，请求STS可以获取临时秘钥。
- 角色：表示某种操作权限的虚拟概念，没有独立的登录密码和AccessKey。
- 临时秘钥：请求STS返回一组临时的AccessKey、secretKey及Token，即为临时秘钥。

## 使用流程
主账号A（AccountID：111111111111）有一个名为test-app的存储桶，并希望其APP用户可以在该存储桶下保存数据。该场景可通过使用临时秘钥访问OSS来实现。具体流程如下：

**1.创建角色**

A账号创建角色test-role，指定A账号可以代入该角色；创建完成后为test-role附加IAM Policy，该Policy允许访问test-app存储桶；详见[角色说明](https://docs.jdcloud.com/cn/iam/role)。

Policy示例如下，允许该角色上传Object至test-app存储桶中。
```
{
	"Version": 3,
	"Statement": [
		{
			"Effect": "Allow",
			"Action": [
				"oss:PutObject"
			],
			"Resource": [
				"jrn:oss:*:111111111111:test-app/*"
			]
		}
	]
}
```
**2.创建子用户**

A账号创建IAM子用户test-iam，并对该用户附加IAM Policy，该Policy允许代入角色test-role；详见[子用户说明](https://docs.jdcloud.com/cn/iam/sub-user);

Policy示例如下，允许该用户扮演test-role角色。
```
{
	"Version": 3,
	"Statement": [
		{
			"Effect": "Allow",
			"Action": [
				"sts:assumeRole"
			],
			"Resource": [
				"jrn:iam::111111111111:role/test-role"
			]
		}
	]
}
```
**3.获取临时秘钥**

使用test-iam用户代入test-role角色，获取临时秘钥，并指定有效期；详见[角色-用户角色扮演和切换](https://docs.jdcloud.com/cn/iam/role);

**4.访问OSS**

使用临时秘钥访问OSS，该临时秘钥拥有test-role角色的权限，在秘钥有效期内可以正常访问test-app存储桶。

## 访问示例
以下以Java SDK为例，说明如何使用临时秘钥访问OSS。
- 获取临时秘钥：调用STS服务AssumeRole接口获取临时AccessKey、secretKey及Token；该示例使用[jdcloud-sdk-java](https://docs.jdcloud.com/cn/sdk/java)初始化stsClient获取临时秘钥。
- 使用临时秘钥访问OSS：该示例使用临时秘钥初始化s3Client，并上传Object。

```Java
import com.amazonaws.ClientConfiguration;
import com.amazonaws.auth.AWSCredentialsProvider;
import com.amazonaws.auth.AWSStaticCredentialsProvider;
import com.amazonaws.auth.BasicSessionCredentials;
import com.amazonaws.client.builder.AwsClientBuilder;
import com.amazonaws.services.s3.AmazonS3;
import com.amazonaws.services.s3.AmazonS3Client;
import com.jdcloud.sdk.auth.CredentialsProvider;
import com.jdcloud.sdk.auth.StaticCredentialsProvider;
import com.jdcloud.sdk.http.HttpRequestConfig;
import com.jdcloud.sdk.http.Protocol;
import com.jdcloud.sdk.service.sts.client.StsClient;
import com.jdcloud.sdk.service.sts.model.AssumeRoleInfo;
import com.jdcloud.sdk.service.sts.model.AssumeRoleRequest;
import com.jdcloud.sdk.service.sts.model.AssumeRoleResponse;
import com.jdcloud.sdk.service.sts.model.Credentials;

public class TokenExample {

    public static Credentials getToken() {
        //使用子用户test-iam的AK/SK初始化stsClient
        String accessKey = "your-ak";
        String secretKey = "your-sk";
        CredentialsProvider credentialsProvider = new StaticCredentialsProvider(accessKey, secretKey);
        StsClient stsClient = StsClient.builder()
                .credentialsProvider(credentialsProvider)
                .httpRequestConfig(new HttpRequestConfig.Builder().protocol(Protocol.HTTPS).build())
                .build();
        //调用AssumeRole API代入角色
        AssumeRoleInfo assumeRoleInfo = new AssumeRoleInfo()
                .roleJrn("your-roleJrn")
                .roleSessionName("your-session-name");
        AssumeRoleRequest assumeRoleRequest = new AssumeRoleRequest();
        assumeRoleRequest.setAssumeRoleInfo(assumeRoleInfo);
        AssumeRoleResponse response = stsClient.assumeRole(assumeRoleRequest);
        Credentials credentials = response.getResult().getCredentials();
        //返回代入角色后的临时秘钥
        return credentials;
    }

    public static void main(String [ ]str) {
        //获取临时秘钥
        Credentials credentials = getToken();
        //使用临时秘钥初始化s3Client
        BasicSessionCredentials basicSessionCredentials = new BasicSessionCredentials(
                credentials.getAccessKey(), credentials.getSecretKey(),
                credentials.getSessionToken());

        String endpoint = "https://s3.<REGION>.jdcloud-oss.com";
        ClientConfiguration config = new ClientConfiguration();
        AwsClientBuilder.EndpointConfiguration endpointConfig =
                new AwsClientBuilder.EndpointConfiguration(endpoint, "<REGION>");

        AWSCredentialsProvider awsCredentialsProvider = new AWSStaticCredentialsProvider(basicSessionCredentials);

        AmazonS3 s3Client = AmazonS3Client.builder()
                .withEndpointConfiguration(endpointConfig)
                .withClientConfiguration(config)
                .withCredentials(awsCredentialsProvider)
                .disableChunkedEncoding()
                .withPathStyleAccessEnabled(true)
                .build();
        //使用s3Client上传Object
        s3Client.putObject("your-bucket","your-key","this is test");
    }
}
```
