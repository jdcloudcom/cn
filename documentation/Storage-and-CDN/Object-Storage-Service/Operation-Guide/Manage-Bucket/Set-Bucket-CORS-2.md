# 跨域访问设置

跨源资源共享 CORS（Cross-Origin Resource Sharing ） 定义了在一个域中加载的客户端 Web 应用程序与另一个域中的资源交互的方式。当一个请求URL的协议、域名、端口三者之间任意一与当前页面地址不同即为跨域，例如最常见的，在一个域名下的网页中，调用另一个域名中的资源，如JavaScript脚本、Web字体等，通常出于安全原因，浏览器限制从脚本中发起的跨域HTTP请求，默认的安全限制为同源策略。因此，W3C推荐了一种跨域的访问验证的机制，即CORS。这种机制让Web应用服务器能支持跨站访问控制，使跨站数据传输更加安全，减轻跨域HTTP请求的风险。具体的CORS规则可以参考[W3C CORS规范](https://www.w3.org/TR/cors/)。

跨域资源资源共享常见使用场景：

1.调用XMLHttpRequest或FetchAPI通过跨站点方式访问资源；

2.Web字体，通过CSS使用@font-face 跨域调用字体（OSS托管Web字体，在浏览器加载时要求预检）；

3.通过canvas标签，绘制图表和视频；

## 跨域资源共享的实现

跨域资源共享（Cross-Origin Resource Sharing），简称CORS，是HTML5提供的标准跨域解决方案，服务端对于跨域请求的处理流程如下：

1.CORS通过HTTP请求中附带Origin的Header来表明自己来源域，服务器端接收到这个请求之后，首先检查HTTP头部有无Origin字段，如果HTTP头部没有Origin，或者不允许，直接当成普通请求处理，处理结束。

2.如果HTTP头有Origin并且是允许的，服务器在返回的响应中会附带上Access-Control-Allow-Origin这个Header。

3.浏览器根据是否返回了对应的Header来决定该跨域请求是否成功，如果没有附加对应的Header，浏览器将会拦截该请求；此外，还要判断该请求是一个简单请求还是一个预请求（Preflighted Request），如果不是简单请求，浏览器并不会立即执行对应的请求代码，而是会先发送Preflighted Request（预先验证请求），Preflighted Request是一个OPTION请求，用于询问要被跨域访问的服务器，是否允许当前域名下的页面发送跨域的请求。OPTIONS请求头部中会包含以下头部：Origin、Access-Control-Request-Method、Access-Control-Request-Headers。服务器收到OPTIONS请求后，设置Access-Control-Allow-Origin、Access-Control-Allow-Method、Access-Control-Allow-Headers头部与浏览器沟通来判断是否允许这个请求。如果Preflighted Request验证通过，浏览器才会发送真正的跨域请求。否则，浏览器会拦截接下来的请求。

4.如果服务器允许所有的跨域请求，将Access-Control-Allow-Origin的Header设置为*即可，但不推荐。

5.CORS规则匹配成功必须满足三个条件，首先，请求的Origin必须匹配一项AllowedOrigin项，其次，请求的方法（如GET，PUT等）或者OPTIONS请求的Access-Control-Request-Method头对应的方法必须匹配一项AllowedMethod项，最后，OPTIONS请求的Access-Control-Request-Headers头包含的每个Header都必须匹配一项AllowedHeader项。

## 细节分析：

1.CORS规则的配置是作用在Bucket级别的，默认Bucket不开启CORS规则，所有的跨域请求的Origin都不被允许；每个Bucket的CORS设定是由多条CORS规则指定的，每个Bucket最多允许10条规则，若是通过自定义XML的方式添加CORS规则，则XML文档最多允许16KB大小。

2.CORS相关的Header附加等都是浏览器自动完成的，用户不需要有任何额外的操作，CORS请求与对象存储的身份验证是完全独立的，即CORS规则仅仅是用来决定是否附加CORS相关的Header的一个规则，是否拦截该请求完全由浏览器决定。

3.使用跨域请求的时候需要关注浏览器是否开启了Cache功能。当运行在同一个浏览器上分别来源于www.example1.com和www.example2.com 的两个页面都同时请求同一个跨域资源的时候，如果www.example1.com 的请求先到达服务器，服务器将资源带上Access-Control-Allow-Origin的Header为www.example1.com 返回给用户。这个时候www.example2.com 又发起了请求，浏览器会将Cache的上一次请求返回给用户，此时Header的内容和CORS的要求不匹配，就会导致后面的请求失败。

## 在控制台中设置过程如下：

1.登入控制台->对象存储->空间管理->进入某个Bucket->空间设置，命名为“跨域访问设置”：

![跨域访问设置](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-037.png)

2.点击“跨域访问设置”Tab签之后，下方是CORS规则列表，默认每个Bucket最多支持10条规则。规则列表的各字段说明如下：

a.来源Allowed Origin：允许跨域请求的来源，可以同时指定多个。配置时需带上完整的域信息，例如http://10.100.100.100:8001 或https://www.jcloud.com 。注意， 不要遗漏了协议名http或https，如果端口不是默认的80，还需要带上端口。如果不能确定的域名，可以打开浏览器的调试功能，查看header中的Origin。域名支持通配符*，每个域名中允许最多使用一个*，例如https://*.jcloud.com 。如果来源指定为*，则表示允许所有来源的跨域请求。

b.Allowed Method：按照需求开通对应的方法即可，如GET、PUT、POST、HEAD、DELETE，可以全选。

c.Allowed Headers：允许的跨域请求header，可以配置多条匹配规则，以回车间隔。在Access-Control-Request-Headers中指定的每个header，都必须在Allowed Header中有对应项。Header容易遗漏，没有特殊需求的情况下，建议设置为*，表示允许所有。大小写不敏感；当CORS规则列表页中同一个规则内当有多条记录时换行展示时，不做缩略处理，每行记录如果超出列宽限制，后缀以...展示。

d.Exposed Headers：暴露给浏览器的header列表，即用户从应用程序中访问的响应头（例如一个Javascript的XMLHttpRequest对象）。不允许使用通配符。具体的配置需要根据应用的需求确定，只暴露需要使用的header。如果不需要暴露可以不填。大小写不敏感，该项是可选配置项；当CORS规则列表页中同一个规则内有多条记录时换行展示时，不做缩略处理，每行记录如果超出列宽限制，后缀以...展示。

e.缓存Max Age：浏览器对特定资源的预取请求（OPTIONS请求）返回结果的缓存时间，单位为秒。如果没有特殊情况可以稍大一点，比如60秒。该项是可选配置项。

3.添加CORS规则：在跨域访问CORS规则列表上方，可通过点击“CORS规则设置”按钮来添加CORS规则，效果如下：

![添加CORS规则](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-038.png)

细节说明：

a. 来源Allowed Origin、Allowed Headers、Exposed Headers为多行文本框，来源Allowed Origin的输入规则请参见上一段文档中的说明，每行以换行符来间隔。

b. 缓存Max Age只允许输入大于等于0的正整数，范围为0-999999999。

c. 对于在多行文本框中，若输入了两行完全一样的内容，如在Allow Headers文本框中输入了“www.jcloud.com” 之后，换行再次输入“www.jcloud.com” ，提交规则后只保留一条“www.jcloud.com” 记录。

d. 域名格式的通配符只支持http://*.example.com ，不支持http://www.abc.*.com 这种格式；对于IP，要支持CIDR格式，支持http://10.110.120.*:8080 ，不支持http://10.110.*.*:8080 这种格式

4.还可以通过点击“CORS规则编辑器”来自定义CORS规则，效果如下：

![CORS规则编辑器](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-039.png)

细节说明：

a. CORS规则编辑器中会展示出当前全部已添加的CORS规则。

b. 编辑器中无法使用代码注释，并且总大小不得超过16KB。

