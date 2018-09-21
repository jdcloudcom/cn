

# 简介

&emsp;&emsp;欢迎使用京东云开发者 .NET 工具套件（.NET SDK）。使用京东云 .NET SDK，您无需复杂编程就可以访问京东云提供的各种服务。    
&emsp;&emsp;为了方便您理解SDK中的一些概念和参数的含义，使用SDK前建议您先查看OpenAPI使用入门。要了解每个API的具体参数和含义，请参考程序注释或参考[OpenAPI&SDK](https://www.jdcloud.com/help/faq?act=3)下具体产品线的API文档。

# 环境准备 & 编译

* 此项目使用visual studio 2017 开发，如果需要进行代码编辑、调试，推荐使用visual studio 2017 以上版本打开。

* 本项目使用最新的 dotnet standard 多目标框架的方法进行编译，项目使用了 .NET 3.5 、 .NET 4.0 、 .NET 4.5 和 .net standard 2.0 版本进行编译。在编译前需要安装 .NET Framework 3.5 、4.0 、4.5 的开发sdk和dotnet core 2.0 以上版本的sdk，在windows 10 操作系统下 .NET Framework 3.5 请在 `启用和关闭windows功能` 的控制面板勾选应用以后再安装visual studio 2017 和 .net framework 4.7 ，.dotnet core 的安装方法请查看[微软官网文档](https://www.microsoft.com/net/learn/get-started/windows)。其它目标框架请在安装visual studio时候勾选或微软官方网站下载。

* 本项目支持在linux 下编译dotnet standard 2.0 版本的sdk，编译的脚本为项目下的`linux-bulid.sh`,需要拷贝到sdk目录下运行。输出目录请查看脚本自行修改。

* 因目前Http调用工具类使用`HttpClient`，如果使用`.Net Framework 4.5` 需要引用框架包`System.Net.Http`。因`HttpClient`不支持`.Net Framework 3.5`且对`.NetFramework 4.0` 的异步支持不是很完善，所以在项目中使用了`HttpWebRequest`进行了替换。

* 因项目使用了`Newtonsoft.Json` 作为Json 对象转换的工具包，因此也需要引用`Newtonsoft.Json`，请在使用的时候选择与您使用的框架对应的版本引用。

* 如果需要使用其他版本的SDK，请在项目中增加编译版本，同时修改编译判断条件 ，具体编译目标框架编译条件信息参见[微软官网文档（Target frameworks页面）](https://docs.microsoft.com/en-us/dotnet/standard/frameworks)。

* 在开始调用京东云open API之前，需提前在京东云用户中心账户管理下的AccessKey管理页面申请accesskey和secretKey密钥对（简称AK/SK）。AK/SK信息请妥善保管，如果遗失可能会造成非法用户使用此信息操作您在云上的资源，给你造成数据和财产损失。

# SDK使用方法

&emsp;&emsp;在您的项目中引用需要调用的相关模块的dll 与 此dll所依赖的相关类库文件。然后按照下方调用sdk的Demo使用。    
&emsp;&emsp;京东云 .NET SDK可以使用Nuget进行包管理，使用方法如下:

在visual studio Nuget包浏览器查找JDCloudSDK 或者使用包管理控制台输入命令

```powershell
Install-Package JDCloudSDK.Vm -Version 0.7.4.1
```

或者使用 .NET CLI 安装

```powershell
dotnet add package JDCloudSDK.Vm --version 0.7.4.1
```

请选择自己需要使用的模块安装。

SDK使用中的任何问题，欢迎您在Github项目[SDK使用问题反馈页面](https://github.com/jdcloud-api/jdcloud-sdk-net/issues)交流。

# 调用SDK

.NET SDK的调用主要分为4步：

    1. 设置accessKey和secretKey
    2. 创建Client
    3. 设置请求参数
    4. 执行请求得到响应
以下是查询单个云主机实例详情的调用示例

```csharp
using JDCloudSDK.Core.Auth;
using JDCloudSDK.Core.Client;
using JDCloudSDK.Core.Http;
using Newtonsoft.Json;
using System;
using JDCloudSDK.Vm.Model;
using JDCloudSDK.Vm.Apis;
using JDCloudSDK.Vm.Client;
namespace JDCloudSDK.ConsoleTest
{
    class Program
    {
        static void Main(string[] args)
        {
            //1. 设置accessKey和secretKey
            string accessKeyId = "{accessKey}";
            string secretAccessKey = "{secretKey}";
            CredentialsProvider credentialsProvider = new StaticCredentialsProvider(accessKeyId, secretAccessKey);
            //2. 创建XXXClient
            VmClient vmClient = new VmClient.DefaultBuilder()
                     .CredentialsProvider(credentialsProvider)
                     .HttpRequestConfig(new HttpRequestConfig(Protocol.HTTP,10))
                     .Build();

            //3. 设置请求参数
            DescribeInstanceRequest request = new DescribeInstanceRequest();
            request.RegionId="cn-north-1";
            request.InstanceId="i-c0se9uju";
            //4. 执行请求
            var response = vmClient.DescribeInstance(request).Result;
            Console.WriteLine(JsonConvert.SerializeObject(response))
            Console.ReadLine();
        }
    }
}
```

如果需要设置额外的header，例如要调用开启了MFA操作保护的接口，需要传递x-jdcloud-security-token，则按照如下方式：

```csharp
vmClient.SetCustomHeader("x-jdcloud-security-token","xxx");
```
