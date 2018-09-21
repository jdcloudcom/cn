# 如何将不带www的根域名跳转到带www的主域名上

1、将jdcloud.com解析到与www.jdcloud.com相同的ip；

2、新建.htaccess 文件，加入如下代码，保存后上传到网站上面；

代码:

RewriteEngine On

RewriteCond %{HTTP_HOST} ^blog.jdcloud.com [NC]

RewriteRule ^(.*)$ http://www.jdcloud.com/$1 [L,R=301]

在浏览器中输入jdcloud.com，立刻跳转到www.jdcloud.com，成功！

你的网站在做域名解析时，有没有设置不带www的域名？应该设置一个不带www的域名。这样，当用户使用不带www的域名时，可以正常访问你的网站。

但是我们经常碰到这样的情况，其他网站链接你的站点时，会用下面的链接：

www.jdcloud.com

jdcloud.com/

www.example.om/index.html

jdcloud.com/index.html

而这样导致：你站点主域名的pr值分散到其他几个URLs了。因为在搜索引擎看来，带www和不带www的URL是不同的两个URL，当它们指向同一个网站时，会让搜索引擎不懂应该选择哪一个URL作为主要的。

如果你用301重定向把其他几个URL如jdcloud.com转到www.jdcloud.com，PR也就集中在主域名：www.jdcloud.com 了。

虽然在google网站管理员中心中，可以google设定首选域名，而这个设置就是为一些人设置不了301的问题而准备的，设定首选域名和301是一样的效果，不过这仅仅对google有效。该设置301还是要设置的，毕竟是要对所有搜索引擎的。

Url转发与301重定向的区别

经过测试以后，发现URL转发、域名绑定、301永久重定向、302暂时性定向、meta 转发之间有不同的概念。

URL转发：分显性转发，隐性转发，如果做SEO，后者直接K掉。下面的URL转发一般指显性转发。

有一点说法是：URL转发不利于SEO，对PR没有传递，301对SEO很友好，可以传递PR 。但是有的URL转发测试返回的代码是301。下面会提到。

URL转发对已经存在网址统一重新转向新域名。而301重定向如果使用代码一般只针对首页有效，虽然htaccess可以达到目标，但win不支持。最好的方法是有IIS控制台里的重定向（效果如何没测试），或者htaccess支持（使用正则表达式达到各路径的对应重定向，相当于替换域名）

至于301与302转向的区别

实施301后，新网址完全继承旧网址，旧网址的排名等完全清零。

实施302后，对旧网址没有影响，但新网址不会有排名。

302即使网站客观上不是spam，也很容易被搜寻引擎容易误判为spam而遭到惩罚。

meta fresh：其具体是通过网页中的meta指令，在特定时间后重定向到新的网页，如果延迟的时间太短(约5秒之內)，会被判断为spam。

301重定向具体办法

1，设置.htaccess文件（只适用于linux系统，并需要虚拟主机支持。）

使访问jdcloud.com/的时候就会自动转到www.jdcloud.com

在.htaccess文件里写上以下代码即可。

RewriteEngine on

RewriteCond %{http_host}^jdcloud.com [NC]

RewriteRule ^(.*)$http://www.jdcloud.com/$1 [L,R=301]

注意：URL标准化的301重定向（以上代码）需要写在其他URL-rewrite代码之前。

2，适用于使用Unix系统的用户

通过此指令通知搜索引擎的spider你的站点文件不在此地址下。这是较为常用的办法。

形如：Redirect 301 / http://www.jdcloud.com

3，适用于使用Windows系统的用户

在域名管理后台设置url转发，前面写上jdcloud.com 不带www的，后面框里写上www.jdcloud.com这种带www的域名，设置成显式转发。显式转发相当于301，隐式转发相当于302，比较危险。

不过值得一提的是，因为URL转发和301概念不同，所以并不是所有的显式转发都是301的（听说万网提供的url转发是302的），可以使用http://tool.alimama.com/tools.php 提供的网站Header信息查询工具查询jdcloud.com，如果返回代码有“HTTP/1.1 301Moved Permanently”。恭喜，那就是301的。我的是新网，新网(xinnet)提供url显式转发是301的，我就使用了此方法。

如果你是万网，又是windows主机，那就用DNS别名解析吧。

4，用ASP/PHP实现301重定向：

ASP：

Response.Status=”301 MovedPermanently”

Response.AddHeader”Location”,”http://www.jdcloud.com/”

Response.End

PHP：

header(“HTTP/1.1 301 MovedPermanently”)；

header(“Location：http://www.jdcloud.com/”)；

exit()；

1.重定向jdcloud.com到www.jdcloud.com

这种重定向旨在使域名唯一，是网站SEO必须要做的，后面重定向www.jdcloud.com到jdcloud.com也是出于同样的原因，只是形式不同。

打开.htaccess文件，加入以下规则。(下面的规则是针对主域名的，子域名要修改)

RewriteEngine On

RewriteCond %{HTTP_HOST} !^www.jdcloud.com$[NC]

RewriteRule ^(.*)$ http://www.jdcloud.com/$1[L,R=301]

2.重定向www.jdcloud.com到jdcloud.com

RewriteEngine On RewriteCond %{HTTP_HOST} !^jdcloud.com$[NC] RewriteRule ^(.*)$ http://jdcloud.com/$1[L,R=301]

3.重定向oldjdcloud.com到www.newjdcloud.com

RewriteEngine On RewriteCond %{HTTP_HOST} !oldjdcloud.com$[NC] RewriteRule ^(.*)$ http://www.newjdcloud.com/$1[L,R=301]

4.重定向oldjdcloud.com to newjdcloud.com

RewriteEngine On RewriteBase / RewriteCond %{HTTP_HOST} !oldjdcloud.com$[NC] RewriteRule ^(.*)$ http://newjdcloud.com/$1[L,R=301]

5.重定向jdcloud.com/file/file.php 到 otherjdcloud.com/otherfile/other.php

RewriteCond %{HTTP_HOST} ^www.jdcloud.com$ RewriteRule ^file/file.php$http://www.otherjdcloud.com/otherfile/other.php [R=301,L]

如果你用301重定向把其他几个URL如jdcloud.com转到

www.jdcloud.com

PR也就集中在主域名：www.jdcloud.com 了。

虽然在google网站管理员中心中，可以google设定首选域名，而这个设置就是为一些人设置不了301的问题而准备的，设定首选域名和301是一样的效果，不过这仅仅对google有效。该设置301还是要设置的，毕竟是要对所有搜索引擎的。


