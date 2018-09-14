# 京东云VPC


## 简介
VPC相关API


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**addNetworkAclRules**|POST|添加networkAcl规则接口|
|**addNetworkSecurityGroupRules**|POST|添加安全组规则|
|**addRouteTableRules**|POST|添加路由表规则|
|**assignSecondaryIps**|POST|给网卡分配secondaryIp接口|
|**associateElasticIp**|POST|给网卡绑定弹性Ip接口|
|**associateNetworkAcl**|POST|给子网绑定networkAcl接口|
|**associateRouteTable**|POST|路由表绑定子网接口|
|**createElasticIps**|POST|创建一个或者多个弹性Ip|
|**createNetworkAcl**|POST|创建networkAcl接口|
|**createNetworkInterface**|POST|创建网卡接口，只能创建辅助网卡|
|**createNetworkSecurityGroup**|POST|创建安全组|
|**createRouteTable**|POST|创建路由表|
|**createSubnet**|POST|创建子网|
|**createVpc**|POST|创建私有网络|
|**createVpcPeering**|POST|创建VpcPeering接口|
|**deleteElasticIp**|DELETE|删除弹性Ip|
|**deleteNetworkAcl**|DELETE|删除networkAcl接口|
|**deleteNetworkInterface**|DELETE|删除弹性网卡接口|
|**deleteNetworkSecurityGroup**|DELETE|删除安全组|
|**deleteRouteTable**|DELETE|删除路由表|
|**deleteSubnet**|DELETE|删除子网|
|**deleteVpc**|DELETE|删除私有网络|
|**deleteVpcPeering**|DELETE|删除VpcPeering接口|
|**describeElasticIp**|GET|ElasticIp资源信息详情|
|**describeElasticIps**|GET|查询弹性ip列表|
|**describeNetworkAcl**|GET|查询networkAcl资源详情|
|**describeNetworkAcls**|GET|查询Acl列表|
|**describeNetworkInterface**|GET|查询弹性网卡信息详情|
|**describeNetworkInterfaces**|GET|查询弹性网卡列表|
|**describeNetworkSecurityGroup**|GET|查询安全组信息详情|
|**describeNetworkSecurityGroups**|GET|查询安全组列表|
|**describeQuota**|GET|查询配额信息|
|**describeRouteTable**|GET|查询路由表信息详情|
|**describeRouteTables**|GET|查询路由表列表|
|**describeSubnet**|GET|查询子网信息详情|
|**describeSubnets**|GET|查询子网列表|
|**describeVpc**|GET|查询Vpc信息详情|
|**describeVpcPeering**|GET|查询VpcPeering资源详情|
|**describeVpcPeerings**|GET|查询VpcPeering资源列表|
|**describeVpcs**|GET|查询私有网络列表|
|**disassociateElasticIp**|POST|给网卡解绑弹性Ip接口|
|**disassociateNetworkAcl**|POST|给子网解绑NetworkAcl接口|
|**disassociateRouteTable**|POST|给路由表解绑子网接口|
|**modifyNetworkAcl**|PATCH|修改networkAcl接口|
|**modifyNetworkAclRules**|POST|修改networkAcl接口|
|**modifyNetworkInterface**|PATCH|修改弹性网卡接口|
|**modifyNetworkSecurityGroup**|PATCH|修改安全组属性|
|**modifyNetworkSecurityGroupRules**|POST|修改安全组规则|
|**modifyRouteTable**|PATCH|修改路由表属性|
|**modifyRouteTableRules**|POST|修改路由表规则|
|**modifySubnet**|PATCH|修改子网接口|
|**modifyVpc**|PATCH|修改私有网络接口|
|**modifyVpcPeering**|PUT|修改VpcPeering接口|
|**removeNetworkAclRules**|POST|移除networkAcl规则|
|**removeNetworkSecurityGroupRules**|POST|移除安全组规则|
|**removeRouteTableRules**|POST|移除路由表规则|
|**unassignSecondaryIps**|POST|给网卡删除secondaryIp接口|
