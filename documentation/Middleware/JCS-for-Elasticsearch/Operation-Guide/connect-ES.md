## 访问集群
### 基于云服务器访问前提
京东云搜索Elasticsearch与依赖的云主机必须处于同一个VPC下，因此要先创建相同私有网络和子网的云主机，从该云主机下获取到“公网IP”，才能访问云搜索Elasticsearch服务。
### curl测试
通过Linux环境下的curl命令访问云搜索Elasticsearch实例的9200端口。
指定账号密码访问示例格式为curl –XGET [公网域名]，公网域名为云搜索Elasticsearch中基本信息界面的 **内网访问域名** ，指令示例如下：
```
curl -XGET es-nlb-es-kgqo8zmgcv.jvessel-open-hb.jdcloud.com:9200
```
响应如下代表访问成功：
```
{
  =^.^=
/_cat/allocation
/_cat/shards
/_cat/shards/{index}
/_cat/master
/_cat/nodes
/_cat/tasks
/_cat/indices
/_cat/indices/{index}
/_cat/segments
/_cat/segments/{index}
/_cat/count
/_cat/count/{index}
/_cat/recovery
/_cat/recovery/{index}

```
