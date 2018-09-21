# 数据迁移工具

## 概述

京东云对象存储数据迁移工具支持从AW S3、阿里云、腾讯云、百度云、七牛云等服务迁移文件到京东云OSS；同时也支持本地文件列表迁移。迁移工具是一个简单的分布式系统，采用python rpc实现，拥有一个Master，一个或多个Worker，您可以将其运行在单台或多台机器上。

工具特点如下：

1.支持丰富的数据源，包括本地数据及第三方数据

2.支持断点续传

3.支持增量迁移，且支持迁移指定时间后的文件

4.支持并行数据传输

工具下载：[osstransfer](http://downloads.oss.cn-north-1.jcloudcs.com/tools/osstransfer.zip)

## 运行环境

Linux及Window

软件依赖：python版本2.7.X

迁移工具是使用python实现的，在使用前，需要安装一些依赖包，您可以使用下面的命令进行安装（确保pip已经安装了）
```
pip install requests
pip install qiniu
pip install boto3
pip install -U cos-python-sdk-v5
pip install oss2
```

## 配置Worker

Worker配置文件是config-worker（路径：osstransfer/src/worker/config-worker）

配置内容如下
```
#port: 指定该worker使用的端口号，默认值是6262;
#is-continue: True/False,是否继续上次未完成的任务，默认只为True。
port=1234
is-continue=True
```
配置完成后直接运行osstransfer/src/worker 目录下的worker.py，建议您在后台运行worker，启动Worker命令如下：
```
nohup python worker.py &
```
worker启动后，它在等待master的调用，有关worker的运行记录，您可以在log-worker.txt文件（目录：osstransfer/logs）中查看。

注意：worker目前只支持被一个master调用，请确保您的worker不会同时为多个master服务。



## 配置Master

Master的配置文件是config-master（路径osstransfer/src/master/config-master）

配置参数如下

|配置项|说明|
|-|-|
|master|指定master所在机器的ip以及使用的port；必配项|
|worker|指定可用的worker,您需要指定该worker的ip以及您为该worker配置的port；必配项|
|Job-ID|为这次任务指定一个名字，如果您自己指定的话，需要保证同一个bucket下的job-ID是不同的；您也可以不指定，我们会使用时间戳作为job-ID；选配项|
|Job-type|job的类型只有两种，transfer(迁移job)、check(验证job)；必配项|
|src-filetype|指定源数据的文件类型，可选的有，s3file、diskfile、qiniufile、aliyunfile、notencentfile、baidufile；必配项|
|src-absolutepath|仅当配置filetype为diskfile时使用，用来指定源数据的绝对路径（路径必须以'/'结尾），该路径下的所有文件都会被迁移；必配项|
|src-accesskey|指定源数据的accesskey；迁移第三方数据源必配|
|src-secretkey|指定源数据的secretkey；迁移第三方数据源必配|
|src-endpoint|指定源数据的endpoint；迁移第三方数据源必配|
|src-bucketName|指定源数据所在的bucket；迁移第三方数据源必配|
|src-key|指定迁移的目录（必须以'/'结尾），如果您不指定，将会把bucket下的数据全部迁移；选配项|
|src-file-list|您可以指定一个文件，把需要迁移或验证的文件列表保存在该文件中，文件格式如下：filepath\tfilesize；选配项<br>注意：如果指定了src-file-list，我们只会迁移您在该文件中指定的文件列表,src-key配置项将失效（对于文件系统，您可以使用src-key指定前缀，在文件列表中保存相对路径）|
|des-accesskey|京东云对象存储的accesskey；必配项|
|des-secretkey|京东云对象存储的secretkey；必配项|
|des-endpoint|京东云对象存储的endpoint；必配项|
|des-bucketName|京东云对象存储的bucket名；必配项|
|des-key|京东云对象存储的目录，您可以通过指定目录（目录必须以'/'结尾），把数据迁移到该目录下；选配项|
|sync-enable-increment|是否开启增量同步，可选的参数有True（开启增量同步）、 False（全量同步）；选配项，未配时默认为增量同步，当为False时,transfer-is-continue和check-is-continue无论如何配置,均为False<br>注：当您设置为True时，你必须为job-ID指定一个值，不可以为空。|
|sync-lastmodify|设定一个时间，只会迁移最后更改时间在该时间之后的文件,时间格式为：YYYY-MM-DD HH:MM:SS,默认值为1970-01-01   00:00:00；选配项<br>注：虽然您设置了lastmodify,但我们可能会迁移该lastmodify之前的一些文件，也就是说该时间只是一个大概值，并不是十分精确。|
|task-size|指定每个task迁移数据的最大值（以MB为单位），默认5GB,在验证时也会使用；选配项|
|task-filenumbers|指定每个task迁移文件数量的最大值，默认5w（建议不要超过20w),在验证时也会使用；选配项|
|round|指定轮数，默认2轮，在验证时也会使用该轮数；选配项|
|transfer-is-continue|True/False,是否继续上次未完成的job，默认为True；选配项|
|transfer-error-output|指定一个文件名，用来保存迁移失败的文件（您可以通过该文件查看失败原因），默认文件名是："[job-ID]-transfer-error-list.txt"；选配项|
|check-time|指定验证的时间，可选的参数有now(迁移完成后立即校验)、future(迁移完成后先不校验，我们会在目的bucket中保存校验所需要的信息)、never(不校验)，默认值是future；选配项|
|check-mode|指定验证模式，可选的有head(只查看该文件是在存在）、md5(比较源数据和目的数据的md5），默认值为head；选配项|
|check-is-continue|是否从上次继续验证，True/False,默认为True；选配项|
|check-error-output|指定一个文件名，用来保存验证存在问题的文件，默认文件名是："[job-ID]-check-error-list.txt"；选配项|
|check-md5-output|验证完成后，我们会保存所有文件的md5,请指定一个文件来保存它，默认文件名是："[job-ID]-check-md5-list.txt"；选配项|

## 运行Master

config-master文件为master指定了一个job，master在运行时会读取这个文件，完成指定的任务。

使用场景：

（1）冷数据迁移

当您配置好config-master后，直接运行osstransfer/src/master 目录下的master.py，我们建议您在后台运行：
```
nohup python master.py  &
```
（2）热数据迁移

如果您准备迁移热数据，我们建议您使用定时任务，在linux下您可以使用crontab去设置一个定时任务，在windows下有图形界面的计划任务。

linux下使用crobtab如下：

命令crontab -e，然后添加定时任务，每隔一天执行一次：

![](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-090.jpg)

注意：如果上一个定时任务没有完成，新的迁移任务是不会启动的，这样做是为了保证迁移过程中数据一致。

master的运行信息可以通过osstransfer/logs目录下的log-master.txt查看。

## 监控状态

为了能够获取master和worker的运行状态，我们开发了一个单独的程序，该程序目录为：osstransfer/src/probe/probe.py，我们介绍该程序的使用：

（1）显示帮助文档

```
python probe.py -h
```

（2）查看某个worker或master
```
python probe.py -ip_port ip:port
```

（3）查看所有的worker和master的状态
```
python probe.py -f config-master
```
