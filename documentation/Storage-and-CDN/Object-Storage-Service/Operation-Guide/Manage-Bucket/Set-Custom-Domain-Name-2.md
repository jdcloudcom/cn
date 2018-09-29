# 自定义域名服务

您可以将自定义的域名访问绑定在属于自己的Bucket上面，即CNAME。并且按照中国《互联网管理条例》的要求，用户如需开通这项功能，必须提供工信部备案号，域名持有者身份证等有效资料，经由京东云审批通过后才可以使用。在您开通CNAME功能后，OSS将自动处理对该域名的访问请求。 
应用场景
例如，当用户需要将网站中的文件迁移到OSS，并且不想修改网页的代码，即保持网站的链接不变，CNAME功能特别适合这种场景。
例如用户A的网站域名为www.example.com，网站文件为abc.html，网站链接为：http://www.example.com/abc.html。
流程如下：

 1.在OSS上创建一个Bucket，命名为example，并上传abc.html网站文件到该存储空间中。
 
 2.OSS控制台，将www.example.com这个自定义的域名绑定在已创建存储空间上。
 
 3.在域名服务器上，添加CNAME规则，将www.example.com映射成存储空间域名。
 
 4.http://www.example.com/abc.html请求到达OSS后，OSS会找到www.example.com和存储空间域名（example.oss.cn-north-1.jcloudcs.com）的映射，转换变成访问桶的abc.html文件。即对http://www.example.com/abc.html的访问，经过OSS处理后，实际上访问的是http:// example.oss.cn-north-1.jcloudcs.com /abc.html。
## 控制台：自定义域名 
在OSS Bucket上传对象后，可获取对象的地址，包含两个部分：OSS域名地址+对象文件名，格式为：<BucketName>.<Endpoint>。除了在迁移到OSS中，较少的改动代码之外，还可以避免业务中可能涉及的跨域或者安全问题，建议您将自定义的域名访问绑定在属于自己的Bucket上面。域名绑定成功后，为了使用域名正常访问OSS，还需要添加CNAME记录指向存储空间对应的外网域名。
 说明
*  同一个域名只能与相同地域中唯一Bucket绑定，每个Bucket最多绑定20个域名。
*  您绑定的域名需在工信部备案，否则域名访问将会受到影响。

自定义域名绑定成功后，OSS中存储文件的访问地址可使用自定义域名。例如，您的存储空间example位于华北-北京，对象文件名称为test.jpg，绑定的自定义域名为hello-world.com，则该对象访问地址为：

* 未绑定之前：example.oss.cn-north-1.jcloudcs.com /test.jpg
* 绑定成功后：hello-world.com/test.jpg
  您可以通过控制台将自定义域名绑定到OSS外网域名上实现自定义域名访问存储空间下的文件，也可同时配置京东云CDN实现加速功能。参见[外网域名- endpoint ](../../API-Reference-S3-Compatible/Regions-And-Endpoints.md)

## 绑定域名操作步骤
1.登入控制台->对象存储->空间管理->进入某个Bucket->空间设置，点击“自定义域名”。

2.单击添加域名按钮，打开绑定用户域名页面，如下图所示：

![图片](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-094.jpg)
 
3.绑定域名
    在用户域名框中，输入要绑定的域名名称。
    如果需要CDN加速，通过单击自定义域名tab 也的提示文案，前往京东云CDN控制台开通CDN加速。

4.单击提交。

说明
* 设置提交完成后需要用户手动到域名解析商处添加 CNAME 记录。
* 如果您的用户域名需要通过HTTPS的方式访问OSS服务，必须购买相应的数字证书。并通过工单提交您的证书，并通过京东云OSS托管您的证书。
* 如果您输入的域名已经被其他用户恶意绑定，系统将提示域名被绑定。您可以单击提交工单的方式，按照OSS的验证方案，完成验证域名所有权，如果通过域名所有权验证，即可绑定域名，同时解除此域名与之前存储空间的绑定关系。
* 目前仅支持使用自定义域名下载文件，如您需上传文件或对Bucket进行各种操作请使用京东云对象存储域名。

## 域名解析操作步骤（以京东云云解析为例）
登录京东云云解析DNS 控制台进入域名解析列表页面。
单击目标域名或右侧的解析按钮进入域名解析页面。
单击添加解析后，打开添加解析页面。
在记录类型下拉列表中，选择CNAME；在记录值框中，填写对应的存储空间外网域名（即Bucket域名，如BucketName.oss.cn-north-1.jcloudcs.com）。
单击确认，域名解析完成。
具体参考[京东云云解析DNS-添加解析记录](../../../../Domain-Name-and-Website/JD-Cloud-DNS/Introduction/What-Is-DNS.md)

