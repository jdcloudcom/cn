## ALB（应用负载均衡）访问日志
### 简介
目前接入日志服务的ALB日志类型为**应用负载均衡访问日志**。当前仅支持检索应用负载均衡7层日志。

### 字段说明
日志字段(7层) | 字段描述 | 字段类型 | 字段值说明
-- | -- | -- | --
timestamp  | 时间戳 | time | 精确到毫秒，eg：2018-12-20T02:59:40.001
alb_id | 负载均衡ID | string | alb-[0-9][a-z]{10} , eg: alb-gmjnqw8bnh
client_ip | 客户端ip | string | eg：192.168.10.1
client_port | 客户端端口 | int | 1-65535，eg：50398
lb_vip | 负载均衡虚ip（vip） | string | eg：192.168.10.2
lb_vport | 负载均衡监听端口（vport） | int | 1-65535，eg：8080
backend_server_ip_port | 后端服务器的ip和端口 | string | eg：192.168.10.1:8080
request_time | 请求时间 | float | >0，eg：0.006 单位为秒
backend_connect_time | 连接建立时间 | float | >0，eg：0.001 单位为秒
backend_response_time | 响应时间 | float | >0，eg：0.006 单位为秒
status | 状态码 | int | 类似于http code； eg: 200, 404, 503 ....
backend_server_status | 后端服务器返回状态码 | int | 类似于http code；eg: 200, 404, 503 ....
request_length | 请求数据长度 | int | >0，eg：80
bytes_sent | 已发送的数据 | int | >0，eg：197 单位为字节
scheme | scheme | string | uri scheme 或者 stream 协议；eg: http， https， tcp, udp
request_method | http method | string | GET, POST, DELETE, PUT , OPTION....
host | http host | string | 请求行中的host或请求头中的host或者一条与请求匹配的servername，eg: 192.168.2.3
request_uri | 完整的原始请求的URI | string | eg : / ; /pan/beta/test1?fid=3
server_protocol | 请求使用的协议 | string | 通常是HTTP/1.0或HTTP/1.1
http_user_agent | 用户代理 | string | 客户端代理，eg: curl , chrome
ssl_cipher | ssl cipher | string | eg：EECDH+AESGCM
ssl_protocol | ssl 协议 | string | eg：SSLv2 ，TLSv1 
