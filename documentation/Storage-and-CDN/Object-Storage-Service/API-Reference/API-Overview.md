# API概览

## 关于Service的操作
|API|描述|
|-|-|
|GetService|得到该账户下所有Bucket|

## 关于Bucket的操作
|API|描述|
|-|-|
|Put Bucket|创建Bucket|
|Put Bucket Referer|设置Bucket的防盗链规则|
|Get Bucket Referer|查看Bucket的防盗链规则|
|Delete Bucket|删除Bucket|
|Get Bucket(List Object)|获得Bucket中所有Object的信息|

## 关于Object的操作
|API|描述|
|-|-|
|PutObject|上传object|
|GetObject|获取Object|
|DeleteObject|删除Object|

## 关于Multipart Upload的操作
|API|描述|
|-|-|
|Initiate Multipart Uploade|初始化MultipartUpload事件|
|Upload Part|分块上传文件|
|Complete Multipart Upload|完成整个文件的Multipart  Upload上传|
|Abort Multipart Upload|取消Multipart  Upload事件|
|List Multipart Uploads|罗列出所有执行中的Multipart  Upload事件|
|List Parts|罗列出指定Upload ID所属的所有已经上传成功Part|
