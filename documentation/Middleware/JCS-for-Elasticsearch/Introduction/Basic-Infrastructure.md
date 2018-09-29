## 基础架构
京东云Elasticsearch提供Elasticsearch + kibana的托管服务，支持用户方便地扩容Elasticsearch集群、集群的监控报警。
![查询1](https://github.com/jdcloudcom/cn/blob/Elasticsearch/image/Internet-Middleware/JCS%20for%20Elasticsearch/ES基础架构-01.png)

| 概念 | 解释 |
| :- | :- |
| ES节点 | 一个运行中的 Elasticsearch 实例称为一个节点，集群内的节点共同承担数据的存储和查询请求。 |	
| 负载均衡 | 提供集群访问的负载均衡功能，在VPC内向用户提供唯一的访问入口，对用户屏蔽掉集群节点。 |
| Kibana | 结合Elasticsearch的数据可视化平台，用于搜索、查看存放在Elasticsearch索引里的数据，提供数据的多维度展示。 |
