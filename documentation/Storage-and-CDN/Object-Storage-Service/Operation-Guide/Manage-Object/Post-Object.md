# 表单上传
## 应用场景

 表单上传指用户使用OSS API中的Post Object请求来完成文件的上传，非常适合嵌入在HTML网页中来上传文件，比较常见的应用场景是网站应用，以社交网站为例子：



<table>
    <thead>
        <tr class="firstRow">
            <td valign="top" style="border:solid #DDDDDD 1px;background:#F0F0F0;padding:7px 15px 7px 10px"></td>
            <td valign="top" style="border:solid #DDDDDD 1px;border-left:none;background:#F0F0F0;padding:7px 15px 7px 10px">
                <p>
                    <strong><span style="font-family:宋体;color:black">不使用表单上传</span></strong>
                </p>
            </td>
            <td valign="top" style="border:solid #DDDDDD 1px;border-left:none;background:#F0F0F0;padding:7px 15px 7px 10px">
                <p>
                    <strong><span style="font-family:宋体;color:black">表单上传</span></strong>
                </p>
            </td>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td valign="top" style="border:solid #DDDDDD 1px;border-top:none;padding:7px 10px 7px 10px">
                <p>
                    <span style="font-family:宋体;color:#333333">流程对比</span>
                </p>
            </td>
            <td valign="top" style="border-top: none; border-left: none; border-bottom: 1px solid rgb(221, 221, 221); border-right: 1px solid rgb(221, 221, 221); padding: 7px 10px; word-break: break-all;">
                <p>
                    1.&nbsp;网站用户上传图片
                </p>
                <p>
                    2.&nbsp;网站服务器回应上传页面
                </p>
                <p>
                    3.&nbsp;图片被上传到网站服务器
                </p>
                <p>
                    4. 网站服务器再将图片上传到OSS
                </p>
            </td>
            <td valign="top" style="border-top: none; border-left: none; border-bottom: 1px solid rgb(221, 221, 221); border-right: 1px solid rgb(221, 221, 221); padding: 7px 10px; word-break: break-all;">
                <p>
                    1.&nbsp;网站用户上传图片
                </p>
                <p>
                    2. 图片上传到OSS
                </p>
            </td>
        </tr>
    </tbody>
</table>

 

使用表单上传的优势

+ 从流程上，少了一步转发，可以降低上传到OSS的延时。

+ 从架构上来说，原来的上传都统一走网站服务器，上传量过大时，瓶颈在网站服务器，可能需要扩容网站服务器。采用表单上传后，上传都是直接从客户端发送到OSS。上传量过大时，压力都在OSS上，由OSS来保障服务的质量。

上传限制

1. 大小限制：使用表单上传时，Object不能超过5GB。

   表单数据和边界 (不包括文件的内容) 不得超过 20 KB。
2. 命名限制

   + 使用UTF-8编码

   + 长度必须在1-1022字节之间

   + 不能以正斜线（/）或者反斜线（\）字符开头

 

安全及授权

为了防止第三方未经授权向开发者的Bucket上传Object，OSS除了提供存储空间（Bucket）级别的访问权限控制，您也可以对文件和目录级别进行灵活的权限访问配置，详情请参见[访问权限设置](../../Operation-Guide/Manage-Bucket/Set-Bucket-Policy.md)。

为了授权给第三方上传，您可以使用PostPolicy方法，详情请参见[PostObject](../../API-Reference-S3-Compatible/Compatibility-API/Post-Object.md)。

 

使用表单上传的基本步骤

1. 构建一个Post Policy。

Post请求的Policy表单域用于验证请求的合法性。例如可以指定上传的Object前缀名，可以指定上传的大小，上传成功后客户端需要跳转到的URL，上传成功后客户端收到的状态码等。Policy是json格式的字符串,例如如下Policy，网站用户能上传的过期时间是2018-12-01T12:00:00.000Z，能上传的文件的前缀必须匹配” user/yuyu/”,上传的目标bucket名称必须是” myBucketName”。
```
 { "expiration": "2018-12-01T12:00:00.000Z",
  "conditions": [
    {"bucket": "myBucketName" },
    ["starts-with", "$key", "user/yuyu/"],
  ]
}
```
2. 将Policy字符串进行base64编码。

3. 用OSS的AccessKeySecret对base64编码后的Policy进行签名。

4. 构建上传的HTML页面。

5. 打开HTML页面，选择文件上传。



功能使用参考

API：[PostObject](../../API-Reference-S3-Compatible/Compatibility-API/Post-Object.md)

