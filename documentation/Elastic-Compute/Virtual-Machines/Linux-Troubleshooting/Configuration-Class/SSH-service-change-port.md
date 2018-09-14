# SSH服务更改端口



ssh登录到服务器内部，执行命令


*vi /etc/ssh/sshd_config*

找到以下配置信息：


*#Port 22*

*#AddressFamily any*

*#ListenAddress 0.0.0.0*

*#ListenAddress ::*

将Port 后面添加更改的ssh服务端口，前面的#去掉使其生效。例如


*Port 2203*

保存文件，重启sshd服务生效，执行


*service sshd restart*


如无法解决您的问题，请向我们提工单。
