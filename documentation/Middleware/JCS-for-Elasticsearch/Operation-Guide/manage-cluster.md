## 管理集群
### 集群状态
在集群列表页和集群详情页的基本信息中，均可查看到集群的状态信息。对于实例列表中的实例，可以按照“可用区”、“集群状态”和“计费信息”进行列表筛选显示。</br>
 ![查询1](https://github.com/jdcloudcom/cn/blob/Elasticsearch/image/Internet-Middleware/JCS%20for%20Elasticsearch/集群状态-01.png)
 ![查询1](https://github.com/jdcloudcom/cn/blob/Elasticsearch/image/Internet-Middleware/JCS%20for%20Elasticsearch/集群状态-02.png)
集群状态是反映集群是否在变更中或正常使用的状态，包括：运行、错误、删除中、创建中、配置变更中，具体含义如下：</br>

状态 | 含义
:---: | :---:
运行 | 集群创建完成，且没有配置变更、集群重启等动作，可以正常访问和使用的状态。 |
错误 | 集群运行过程中出现错误。 |
删除中 | 集群删除操作，需要一定的时间进行处理的状态，期间部分服务访问会受到影响，如 Kibana、数据存储和查询等。 |
创建中 | 集群创建操作，需要一定的时间进行处理的状态，期间部分服务访问会受到影响，如Kabana、数据存储和查询等。 |
配置变更中 | 集群配置变更操作，需要一定的时间进行处理的状态，期间部分服务访问会受到影响，如 Kibana、数据存储和查询等。|
</br>
其中健康状态是云搜索Elasticsearch集群非常重要的监控项，用来表征集群总体上是否工作正常。健康状态种类如下：</br>

|颜色 | 健康状态	|
|:--:|:--: |
| 绿色（green） | 所有的主分片和副本分片都已分配，集群是100%可用的。	|
| 黄色（yellow） | 所有的主分片已经分片了，但至少还有一个副本是缺失的。高可用性在某种程度上被弱化。	|
| 红色（red） | 至少有一个主分片（以及它的全部副本）都在缺失中。 |
### Kibana 访问设置
用户可以使用Kibana查询和分析存储在Elastisearch中的数据。
![查询1](https://github.com/jdcloudcom/cn/blob/Elasticsearch/image/Internet-Middleware/JCS%20for%20Elasticsearch/kibana访问设置-01.png)
