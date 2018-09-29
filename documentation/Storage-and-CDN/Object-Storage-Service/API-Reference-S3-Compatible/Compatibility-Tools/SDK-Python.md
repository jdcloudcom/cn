# SDK-Python

## 概述

若您需要使用Python来访问京东云的对象存储服务，我们可以使用第三方的boto3接口。它可以看作是符合AWS S3 API标准的Python SDK。关于如何使用boto3，请参考https://boto3.readthedocs.io/en/latest/

## 安装pip和boto3

pip的安装：https://pip.pypa.io/en/stable/installing/
使用aws sdk-python前，您需要先安装boto3包，命令如下（请确定pip已经安装）：
```
pip install boto3
```

## 创建client

下面我们给出了一个创建client的例子，更多信息请参考：http://boto3.readthedocs.io/en/latest/reference/services/s3.html
```

import boto3  
        
ACCESS_KEY =‘your accesskey’  
SECRET_KEY = ‘your secretkey’  
s3 = boto3.client(  
    's3',  
    aws_access_key_id=ACCESS_KEY,  
    aws_secret_access_key=SECRET_KEY,  
    #下面给出一个endpoint_url的例子  
    endpoint_url='http://s3.cn-north-1.jcloudcs.com'  
    )  
#use s3 client to create bucket、put object....
```
