# 跨域访问最佳实践

## 同源策略

同源策略(same-origion policy)限制从一个源加载的文档或脚本与来自另一个源的资源进行交互的方式，是用于隔离潜在恶意文件的关键安全机制。同协议、同域名（或IP）、以及同端口视为同一个域，一个域内的脚本仅仅具有本域内的权限，即本域脚本只能读写本域内的资源，而无法访问其它域的资源。这种安全限制称为同源策略。

所谓同源是指域名相同、协议相同且端口相同。举例如下：

不同域名：http://www.jd.com 与http://www.jd.cn 为不同源；

不同协议：http://www.jd.com 与https://www.jd.com 为不同源；

不同端口：http://www.jd.com:80 与http://www.jd.com:81 为不同源；

其它：http://www.jd.com/a 与http://www.jd.com/b 为同源，因为域名协议和端口都相同。

## 跨域访问

跨源资源共享 CORS（Cross-Origin Resource Sharing ） 定义了在一个域中加载的客户端 Web 应用程序与另一个域中的资源交互的方式。当一个请求URL的协议、域名、端口三者之间任意一与当前页面地址不同即为跨域。

例如最常见的，在一个域名下的网页中，调用另一个域名中的资源，如JavaScript脚本、Web字体等，通常出于安全原因，浏览器限制从脚本中发起的跨域HTTP请求，默认的安全限制为同源策略。因此，W3C推荐了一种跨域的访问验证的机制，即CORS。这种机制让Web应用服务器能支持跨站访问控制，使跨站数据传输更加安全，减轻跨域HTTP请求的风险。

## CORS实战案例

以下简单示例介绍使用AJAX从OSS获取数据的配置步骤。示例中使用的存储桶名为 test-cors，存储桶访问权限为公有读私有写。

**准备条件**

1.在test-cors存储桶中上传文件cors.html，文件内容为“请求成功”。 点击“获取地址”，可以看到cors.html这个object的访问地址: http://test-cors.oss.cn-east-1.jcloudcs.com/cors.html 。

2.关闭浏览器cache功能，防止因为浏览器缓存了服务器上次返回的header内容导致和CORS的要求不匹配，影响请求结果，这里我们以chrome浏览器为例, 打开“开发者工具”，勾选“Disable cache”。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-083.jpg)

**跨域请求实践**

1.确认文件可访问

使用curl访问cors.html文件，显示文件内容“请求成功”，确定该object可正常访问。
```
curl http://test-cors.oss.cn-east-1.jcloudcs.com/cors.html
```
![](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-084.jpg)

2.使用AJAX访问文件

使用AJAX技术来直接访问该cors.html文件

首先写一个简单的HTML文件，将以下代码复制到本地保存成HTML文件，并将该网页托管在云主机上，云主机的IP地址为47.104.98.151，所以该网页地址为http://47.104.98.151/cors-test.html （测试地址不支持访问，如需访问，请自行配置）

```
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<script>
function loadXMLDoc() {
        var xmlhttp;
        if (window.XMLHttpRequest) {
                xmlhttp=new XMLHttpRequest();
        }
        else {
                xmlhttp=new ActiveXObject("Microsoft.XMLHTTP");
        }
        
        xmlhttp.onreadystatechange=function()
        if (xmlhttp.readyState==4 && xmlhttp.status==200) {
              document.getElementById("myDiv").innerHTML=xmlhttp.responseText;
        }
        
        xmlhttp.open("GET","http://test-cors.oss.cn-east-1.jcloudcs.com/cors.html",true);
        xmlhttp.setRequestHeader('test','GET');
        xmlhttp.send("");
}
</script>
</head>

<body>
<h2>Test CORS</h2>
<button type="button" onclick="loadXMLDoc()">请求数据</button>
<div id="myDiv"></div>
</body>
</html>
```

3.访问网页

在Chrome浏览器中输入“http://47.104.98.151/cors-test.html ”进入测试网页，点击“请求数据”按钮，出现以下错误。错误提示：无权限访问，原因是没有找到 Access-Control-Allow-Origin 这个 Header。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-085.jpg)

再进入Header页面检查请求，可见浏览器发送了带 Origin 的 Request，因此是一个跨域请求。所以该错误是因为服务器没有配置CORS。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-086.jpg)

4.设置CORS

登入控制台->对象存储->空间管理->进入存储桶test-cors->空间设置->跨域访问设置，点击CORS规则配置进入配置页面。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-087.jpg)

在配置页面中使用最宽松的配置：来源Origin为http://47.104.98.151 ，操作Methods为GET，Allow-Headers为*，缓存Max Age为0。如下图

![](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-088.jpg)

5.验证结果

配置完成后，重新尝试访问cors.html文件。结果如下，成功跨域访问。

![](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-089.jpg)
