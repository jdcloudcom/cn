
# 使用示例

## 使用JSON方式创建容器

	jdc nc create-containers --input-json \
    '{
        "maxCount": 1, 
        "regionId": "cn-north-1",
        "containerSpec": 
        {
            "instanceType": "g.s1.micro", 
            "az": "cn-north-1b",  
            "name": "cli-test",
            "image": "library/httpd",
            "command": ["/bin/bash"],
            "tty": true,
            "rootVolume": 
            {
                "category": "cloud", 
                "cloudDiskSpec": 
                {
                    "az": "cn-north-1b", 
                    "name": "testaa", 
                    "diskType": "ssd", 
                    "diskSizeGB": 20
                }
            }, 
            "primaryNetworkInterface": 
            {
                "networkInterface": 
                {
                    "subnetId": "subnet-ejs1bir2b2", 
                    "az": "cn-north-1b"
                }
            }
        }
    }'
   

## 使用File方式创建容器

将上节中的json串存储在某目录的container-spec.json中，则可以使用以下命令创建容器。

Linux & macOS：

	jdc nc create-containers --input-json 'file:///tmp/container-spec.json'
   

Windows：

	jdc nc create-containers --input-json  'file://c:/container-spec.json'
   

## 启动容器

	jdc nc start-container --container-id c-igz8rekh5q
返回：

	{
	    "error": null,
	    "result": null,
	    "request_id": "bcajj7uhqf35o1cajrbu9umfuwe5uruu"
	}
   

## 查询容器

	jdc nc describe-container --container-id c-igz8rekh5q
返回： 

	{
    "error": null,
    "result": {
        "container": {
            "tty": false,
            "vpcId": "vpc-0bf7bkl91s",
            "image": "nginx:latest",
            "elasticIpAddress": "",
            "subnetId": "subnet-84ahj1qekm",
            "az": "cn-north-1a",
            "instanceType": "g.n2.medium",
            "description": "",
            "envs": null,
            "hostAliases": null,
            "hostname": "c-igz8rekh5q",
            "workingDir": "",
            "charge": {
                "chargeRetireTime": "",
                "chargeStartTime": "2018-05-28T16:31:37Z",
                "chargeExpiredTime": "",
                "chargeStatus": "normal",
                "chargeMode": "postpaid_by_duration"
            },
            "secret": "",
            "rootVolume": {
                "category": "cloud",
                "mountPath": "/",
                "autoDelete": true,
                "fsType": "xfs",
                "cloudDisk": {
                    "status": "in-use",
                    "name": "test",
                    "diskType": "ssd",
                    "diskSize": 10,
                    "az": "cn-north-1a",
                    "createTime": "2018-05-28 16:31:38",
                    "diskId": "vol-wi2e13nhdv",
                    "description": ""
                },
                "readOnly": false
            },
            "launchTime": "2018-05-28 16:32:13",
            "privateIpAddress": "10.0.0.18",
            "status": "running",
            "containerId": "c-igz8rekh5q",
            "elasticIpId": "",
            "args": null,
            "logConfiguration": null,
            "reason": "taskCompleted",
            "dataVolumes": null,
            "name": "test",
            "primaryNetworkInterface": {
                "deviceIndex": 1,
                "networkInterface": {
                    "macAddress": "fa:16:3e:81:55:37",
                    "vpcId": "vpc-0bf7bkl91s",
                    "description": "",
                    "networkInterfaceId": "port-0pvhhh2mdy",
                    "secondaryIps": null,
                    "sanityCheck": false,
                    "securityGroups": [
                        {
                            "groupName": "默认安全组开放全部端口",
                            "groupId": "sg-iuqpipzp30"
                        }
                    ],
                    "subnetId": "subnet-84ahj1qekm",
                    "primaryIp": {
                        "elasticIpAddress": "",
                        "elasticIpId": "",
                        "privateIpAddress": "10.0.0.18"
                    }
                },
                "attachTime": "",
                "autoDelete": true,
                "attachStatus": ""
            },
            "command": null
        }
    },
    "request_id": "bcajk4jk2vh52d5u8tgejwpjubqhc68s"
	}
	
	
## 使用filters参数查询容器

 	jdc nc describe-containers --filters '[{"name":"name", "operator":"eq", "values":["container-name"]}]'
  

## 删除容器

	jdc nc delete-container --container-id c-igz8rekh5q
返回： 

	{
	    "error": null,
	    "result": null,
	    "request_id": "bcajksbtncchv08qwaimfip2mjurupm0"
	}
