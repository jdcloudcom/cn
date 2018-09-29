## 配置ES
操作步骤：</br>
1. 进入“创建集群”页面后，指定集群“地域”和“可用区”。</br>
* “地域”：目前工作区域支持“华北-北京”、“华南-广州”、“华东-上海”。</br>
* “可用区”：可用区是使用独立电源和网络资源的物理区域。通过内部网络互联，再以物理方式进行隔离，提高了应用程序的可用性。不同可用区不互通，创建后不可更改。</br> 
 ![查询1](https://github.com/jdcloudcom/cn/blob/Elasticsearch/image/Internet-Middleware/JCS%20for%20Elasticsearch/配置ES-01.png)
2. 设置集群基本信息，选择“集群版本”，并输入“集群名称”。</br>
* “集群版本”：当前版本仅支持5.6.9。</br>
* “集群名称”：自定义的集群名称，名称不可为空，只支持中文、数字、大小写字母、英文下划线“_”及中划线“-”，且不能超过32字符。</br>
 ![查询1](https://github.com/jdcloudcom/cn/blob/Elasticsearch/image/Internet-Middleware/JCS%20for%20Elasticsearch/配置ES-02.png)
3. 设置集群的主机规格相关参数。</br>
* “节点规格”：当前支持六种规格，包括：1核2G、2核4G、2核8G、4核16G、8核32G、16核64G。可以根据具体业务情况选择不同云主机规格，其中1核2G只适用于测试，不适用于生产环境。</br>
* “单点存储规格”：单点存储规格范围20-1000GB，可输入整数。</br>
* “节点数量”：单点存储规格范围1-25，默认选择3个节点，输入范围大于或小于规定范围，显示最大节点数和最小节点数。</br>
  ![查询1](https://github.com/jdcloudcom/cn/blob/Elasticsearch/image/Internet-Middleware/JCS%20for%20Elasticsearch/配置ES-031.png)
4. 指定集群的网络规格相关参数，包括“私有网络”、“子网”。</br>
* “私有网络”： 显示当前VPC列表，默认选择最新创建的VPC。单击列表后“新建私有网络”跳转至私有网络（VPC）页面。</br>
* “子网”： 显示当前子网列表，默认选择最新创建的子网。单击列表后“新建子网”跳转至私有网络-子网页面。</br>
  ![查询1](https://github.com/jdcloudcom/cn/blob/Elasticsearch/image/Internet-Middleware/JCS%20for%20Elasticsearch/配置ES-04.png)
5. 已选配置列表显示当前已选配置信息，未选项显示默认配置。单击“立即购买”，进入规格确认界面。</br>
  ![查询1](https://github.com/jdcloudcom/cn/blob/Elasticsearch/image/Internet-Middleware/JCS%20for%20Elasticsearch/配置ES-05.png)
6. 规格确认完成后，单击“立即开通”开始创建集群。</br>
  ![查询1](https://github.com/jdcloudcom/cn/blob/Elasticsearch/image/Internet-Middleware/JCS%20for%20Elasticsearch/配置ES-06.png)
7. 跳转支付确认页面成功付款后返回集群列表页面。您创建的集群将展现在集群列表中。且集群状态为“创建中”，耐心等待几分钟，创建成功后集群状态会变为“运行”。如果集群创建失败，请根据界面提示，重新创建集群。</br>
  ![查询1](https://github.com/jdcloudcom/cn/blob/Elasticsearch/image/Internet-Middleware/JCS%20for%20Elasticsearch/配置ES-07.png)
  ![查询1](https://github.com/jdcloudcom/cn/blob/Elasticsearch/image/Internet-Middleware/JCS%20for%20Elasticsearch/配置ES-08.png)
