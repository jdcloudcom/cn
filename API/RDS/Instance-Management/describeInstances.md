# describeInstances


## 描述
获取当前账号下所有RDS实例及MySQL/PostgreSQL只读实例的概要信息，例如实例类型，版本，计费信息等

## 请求方式
GET

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**pageNumber**|Integer|False| |显示数据的页码，默认为1，取值范围：[-1,∞)。pageNumber为-1时，返回所有数据页码；超过总页数时，显示最后一页;|
|**pageSize**|Integer|False| |每页显示的数据条数，默认为10，取值范围：[10,100]，且为10的整数倍|
|**filters**|[Filter[]](#Filter)|False| |过滤参数，多个过滤参数之间的关系为“与”(and)<br>支持以下属性的过滤：<br>instanceId, 支持operator选项：eq<br>instanceName, 支持operator选项：eq, like<br>engine, 支持operator选项：eq<br>engineVersion, 支持operator选项：eq<br>instanceStatus, 支持operator选项：eq<br>vpcId, 支持operator选项：eq<br>instanceType, 支持operator选项：eq<br>internalDomainName, 支持operator选项：eq<br>publicDomainName, 支持operator选项：eq<br>|
|**tagFilters**|[TagFilter[]](#TagFilter)|False| |资源标签|

### <a name="TagFilter">TagFilter</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**key**|String|True| |Tag键|
|**values**|String[]|True| |Tag值|
### <a name="Filter">Filter</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**name**|String|True| |过滤条件的名称|
|**operator**|String|False| |过滤条件的操作符，默认eq|
|**values**|String[]|True| |过滤条件的值|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#Result)| |

### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**dbInstances**|[DBInstance[]](#DBInstance)| |
|**totalCount**|Integer| |
### <a name="DBInstance">DBInstance</a>
|名称|类型|描述|
|---|---|---|
|**instanceId**|String|实例ID|
|**instanceName**|String|实例名称，具体规则可参见帮助中心文档:[名称及密码限制](../../../documentation/Database-and-Cache-Service/RDS/Introduction/Restrictions/SQLServer-Restrictions.md)|
|**instanceType**|String|实例类别，例如主实例，只读实例等，参见[枚举参数定义](../Enum-Definitions/Enum-Definitions.md)|
|**engine**|String|实例引擎类型，如MySQL或SQL Server等，参见[枚举参数定义](../Enum-Definitions/Enum-Definitions.md)|
|**engineVersion**|String|实例引擎版本，参见[枚举参数定义](../Enum-Definitions/Enum-Definitions.md)|
|**instanceClass**|String|实例规格代码|
|**instanceStorageGB**|Integer|磁盘，单位GB|
|**instanceCPU**|Integer|CPU核数|
|**instanceMemoryMB**|Integer|内存，单位MB|
|**regionId**|String|地域ID，参见[地域及可用区对照表](../Enum-Definitions/Regions-AZ.md)|
|**azId**|String[]|可用区ID，第一个为主实例在的可用区，参见[地域及可用区对照表](../Enum-Definitions/Regions-AZ.md)|
|**vpcId**|String|VPC的ID|
|**subnetId**|String|子网的ID|
|**instanceStatus**|String|实例状态，参见[枚举参数定义](../Enum-Definitions/Enum-Definitions.md)|
|**publicDomainName**|String|实例公网域名<br>- 仅支持MySQL|
|**internalDomainName**|String|实例内网域名<br>- 仅支持MySQL|
|**createTime**|String|实例创建时间|
|**backupSynchronicity**|[BackupSynchronicityAbstract[]](#BackupSynchronicityAbstract)|实例跨地域备份服务开启相关信息|
|**charge**|[Charge](#Charge)|计费配置|
|**tags**|[Tag[]](#Tag)|标签信息|
|**sourceInstanceId**|String|MySQL、PostgreSQL只读实例对应的主实例ID|
### <a name="Tag">Tag</a>
|名称|类型|描述|
|---|---|---|
|**key**|String|标签键|
|**value**|String|标签值|
### <a name="Charge">Charge</a>
|名称|类型|描述|
|---|---|---|
|**chargeMode**|String|支付模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration|
|**chargeStatus**|String|费用支付状态，取值为：normal、overdue、arrear，normal表示正常，overdue表示已到期，arrear表示欠费|
|**chargeStartTime**|String|计费开始时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
|**chargeExpiredTime**|String|过期时间，预付费资源的到期时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ，后付费资源此字段内容为空|
|**chargeRetireTime**|String|预期释放时间，资源的预期释放时间，预付费/后付费资源均有此值，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
### <a name="BackupSynchronicityAbstract">BackupSynchronicityAbstract</a>
|名称|类型|描述|
|---|---|---|
|**serviceId**|String|跨地域备份同步服务ID|
|**destRegion**|String|备份同步的目标地域|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|

## 请求示例
GET
```
public void testDescribeInstances() {
    DescribeInstancesRequest request = new DescribeInstancesRequest();
    Filter filter = new Filter();
    filter.setName("instanceId");
    filter.addValue("mysql-axntjxvdix");
    request.addFilter(filter);
    request.setRegionId(region);
    DescribeInstancesResponse response = rdsClient.describeInstances(request);
    Gson gson = new GsonBuilder().create();
    System.out.println(gson.toJson(response));
}

```

## 返回示例
```
{
    "requestId": "bkut9ianrmv9g78aubw44j50i6mtjm0k", 
    "result": {
        "dbInstances": [
            {
                "azId": [
                    "cn-north-1a", 
                    "cn-north-1b"
                ], 
                "backupSynchronicity": [], 
                "charge": {
                    "chargeMode": "postpaid_by_duration", 
                    "chargeStartTime": "2019-09-04T13:50:51Z", 
                    "chargeStatus": "normal"
                }, 
                "createTime": "2019-09-04T21:51:06", 
                "engine": "MySQL", 
                "engineVersion": "8.0", 
                "instanceCPU": 1, 
                "instanceClass": "db.mysql.s1.micro", 
                "instanceId": "mysql-axntjxvdix", 
                "instanceMemoryMB": 1024, 
                "instanceName": "根据备份创建ms80", 
                "instanceStatus": "RUNNING", 
                "instanceStorageGB": 40, 
                "instanceStorageType": "LOCAL_SSD", 
                "instanceType": "cluster", 
                "regionId": "cn-north-1", 
                "subnetId": "subnet-v9o64tph5i", 
                "vpcId": "vpc-da6rpb8uk9"
            }
        ], 
        "totalCount": 1
    }
}
```
