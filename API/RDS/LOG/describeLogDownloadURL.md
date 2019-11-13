# describeLogDownloadURL


## 描述
根据日志文件的下载链接过期时间，生成日志文件下载地址 仅支持 PostgreSQL, MySQL, Percona, MariaDB

## 请求方式
POST

## 请求地址
https://rds.jdcloud-api.com/v1/regions/{regionId}/instances/{instanceId}/log/{logId}:describeLogDownloadURL

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |地域代码，取值范围参见[《各地域及可用区对照表》](../Enum-Definitions/Regions-AZ.md)|
|**instanceId**|String|True| |RDS 实例ID，唯一标识一个RDS实例|
|**logId**|String|True| |日志文件ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**seconds**|Integer|False| |设置链接地址的过期时间，单位是秒，默认值是 300 秒，最长不能超过取值范围为 1 ~ 86400 秒|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](#Result)| |

### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**publicURL**|String|公网下载链接|
|**internalURL**|String|内网下载链接|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|

## 请求示例
POST
```
public void testDescribeLogDownloadURL() {
    DescribeLogDownloadURLRequest request = new DescribeLogDownloadURLRequest();
    request.setRegionId(region);
    request.instanceId("pg-xxxxxxxxxx");
    request.logId("postgresql-xxxxxxxxxxxxxxxxxxxxxxxxxxx");
    request.seconds(300);
    DescribeLogDownloadURLResponse response = rdsClient.describeLogDownloadURL(request);
    Gson gson = new GsonBuilder().create();
    System.out.println(gson.toJson(response));
}

```

## 返回示例
```
{
    "requestId": "bkut6f51mkggr76oja96kh64ehtag0mi", 
    "result": {
        "internalURL": "http://s3.cn-north-1.jcloudcs.com/jddbpgsql/pg-xxxxxxxxxx/logupload/...", 
        "publicURL": "http://s3.cn-north-1.jcloudcs.com/jddbpgsql/pg-xxxxxxxxxx/logupload/..."
    }
}
```
