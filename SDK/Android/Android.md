
# 简介 #

京东云开发者Java工具套件（Java SDK）同样适用于Android开发及运行环境。使用京东云Java SDK，您无需复杂编程就可以访问京东云提供的各种服务。 

为了方便您理解SDK中的一些概念和参数的含义，使用SDK前建议您先查看OpenAPI使用入门文档。要了解每个API的具体参数和含义，请参考程序注释或参考OpenAPI&SDK下具体产品线的API文档。


# 环境准备 #

1. 京东云Java SDK适用于jdk7及以上版本，以及Android 5.0及以上版本。

2. 在开始调用京东云open API之前，需提前在京东云用户中心账户管理下的AccessKey管理页面申请accesskey和secretKey密钥对（简称AK/SK）。AK/SK信息请妥善保管，如果遗失可能会造成非法用户使用此信息操作您在云上的资源，给你造成数据和财产损失。



# SDK使用方法 #

如果您使用Gradle来管理项目，只需在项目的build.gradle文件加入相应的依赖项即可，如下所示：

    //对应产品线的SDK
    implementation 'com.jdcloud.sdk:vm:1.0.3'

您还可以下载SDK源代码自行使用，源代码地址为：[Java SDK](https://github.com/jdcloud-api/jdcloud-sdk-java)。

SDK使用中的任何问题，欢迎您在Github项目[SDK使用问题反馈页面](https://github.com/jdcloud-api/jdcloud-sdk-java/issues)交流。

注意：京东云并没有提供其他下载方式，请务必使用上述官方下载方式！

 

# 调用SDK #

Java SDK的调用主要分为4步：

- STEP1：设置accessKey和secretKey

- STEP2：创建Client

- STEP3：设置请求参数

- STEP4：执行请求得到响应

以下是查询单个云主机实例详情的调用示例

    private static CredentialsProvider credentialsProvider = new StaticCredentialsProvider("ak", "sk");

    VmClient vmClient = VmClient.builder()
                .credentialsProvider(credentialsProvider)
                .httpRequestConfig(new HttpRequestConfig.Builder().build())
                .build();
                
    DescribeInstanceRequest instanceRequest = new DescribeInstanceRequest();
    instanceRequest.setRegionId("cn-north-1");
    instanceRequest.setInstanceId("i-274krai3dw");
    DescribeInstanceTask describeInstanceTask = new DescribeInstanceTask();
    describeInstanceTask.execute(instanceRequest);
        
    
    class DescribeInstanceTask extends  AsyncTask<DescribeInstanceRequest, Integer, DescribeInstanceResponse>{

        @Override
        protected DescribeInstanceResponse doInBackground(DescribeInstanceRequest... describeInstanceRequests) {
            try {
                return vmClient.describeInstance(describeInstanceRequests[0]);
            }catch (Exception e) {
                e.printStackTrace();
            }
            return null;
        }

        @Override
        protected void onPostExecute(DescribeInstanceResponse result) {
            if(result != null) {
                String json = new Gson().toJson(result);
                textView.setText(json);
            }
        }

    }

如果需要设置额外的header，例如要调用开启了MFA操作保护的接口，需要传递x-jdcloud-security-token，则按照如下方式：

	vmClient.setCustomHeader("x-jdcloud-security-token", "xxxx");
