# JMR API


## 简介
提供大数据基础服务中JMR操作的相关接口


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**calculateClusterPrice**|POST|计算对应规格属性的集群价格|
|**calculateExpansionPrice**|POST|计算集群扩容数量的价格|
|**clusterExpansion**|POST|对指定集群扩容指定数量的实例|
|**createAndExcuteJob**|POST|在集群下创建作业并执行|
|**createClusterInNewNetwork**|POST|创建新集群|
|**createCronJob**|POST|新建或更新调度配置|
|**createJob**|POST|按照传入的参数信息创建作业|
|**deleteCluster**|POST|对指定集群执行逻辑删除|
|**deleteCronJob**|POST|删除作业的某一定时任务|
|**deleteHdfsFile**|POST|删除指定集群的对应路径下的hdfs文件|
|**deleteJob**|POST|删除jobId指定作业|
|**deleteWorkFlow**|POST|删除指定工作流|
|**deleteWorkFlowTracker**|POST|删除指定工作流对应的运行记录|
|**executeJob**|POST|执行指定作业|
|**getAccessKeys**|GET|根据userpin获取accessKey和accessKeySecret|
|**getAvaliableNum**|GET|获取当前用户剩余可创建资源数|
|**getClusterCronJobCount**|POST|获取集群的部署作业数|
|**getClusterDetailInfo**|POST|集群扩容时，显示集群详情|
|**getClusterJobCount**|POST|获取集群的作业数|
|**getCronJobDetail**|POST|获取定时任务详情|
|**getCronJobList**|POST|获取执行计划列表|
|**getCronJobTaskList**|POST|获取作业的某一定时任务的运行记录|
|**getCronJobTaskListByJobId**|POST|查询某一执行计划的某一个job的运行记录|
|**getFirstServerVncUrl**|GET|通过clusterId得到远程连接集群主节点的VNC URL|
|**getHardwareStack**|GET|硬件配置信息列表|
|**getInstanceList**|GET|获取主机规格列表(过滤掉低内存的规格, 低于4核全部去掉。)|
|**getJmrVersionList**|GET|返回目前的JMR版本列表|
|**getJobList**|POST|获取指定集群下的作业列表|
|**getJobTypeList**|POST|获取指定集群下的作业类型列表|
|**getKey**|GET|获取用户appKey和secretKey|
|**getLastCronJobTask**|POST|获取定时任务的某个作业的最后一次运行记录|
|**getPropertyValue**|GET|软件配置信息列表|
|**getSoftwareAndVersionInfo**|POST|获取指定JMR版本对应软件清单以及版本信息|
|**getSoftwareInfo**|POST|获取对应版本的软件清单信息|
|**getTaskList**|POST|获取某一作业的运行记录|
|**getWorkFlowList**|POST|获取工作流列表|
|**getWorkFlowTrackerList**|POST|获取工作流运行记录列表|
|**idataCluster**|GET|查询用户指定clusterId对应的集群列表及相关服务的一些信息|
|**isValidJobName**|POST|校验作业名称是否有效|
|**isValidPlanName**|POST|校验执行计划名称是否可用|
|**modifyCronJob**|POST|修改部署作业的执行计划|
|**modifyJob**|POST|按照传入的参数信息修改对应作业信息|
|**monitorDetails**|POST|服务存活状态监控明细数据|
|**monitorServiceList**|POST|当前监控的集群下对应的所有服务列表|
|**pauseCronJob**|POST|暂停作业的某一定时任务|
|**queryExecutingJobList**|GET|获取计划中的任务(已经添加到quartz调度器的任务)|
|**queryFloatingIp**|POST|查询集群随机码（八位）|
|**queryServerQuota**|GET|查询server的剩余配额|
|**queryVpcSubnets**|POST|查询Vpc子网集合|
|**queryVpcs**|POST|获取vpc集合|
|**releaseCluster**|POST|释放指定clusterId对应集群|
|**renewBillingOrder**|POST|对指定集群按照指定的续费方式进行续费|
|**resumeCronJob**|POST|恢复作业的某一定时任务|
|**runCronJobOnce**|POST|立即执行某一定时任务|
|**runWorkFlow**|POST|运行指定工作流|
|**saveWorkFlow**|POST|保存工作流的信息|
|**showClusterDetails**|GET|根据clusterId查询对应集群详情|
|**showJobDetails**|POST|查看指定jobId对应的作业明细|
|**validateName**|POST|验证输入的集群名称是否重复|
|**validateUser**|GET|对登陆的用户名进行校验|
|**wfInstanceDetail**|POST|查看指定工作流详情信息|
