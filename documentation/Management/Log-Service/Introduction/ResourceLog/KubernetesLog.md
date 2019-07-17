## kubernetes集群 系统日志
### 简介
目前接入日志服务的kubernetes集群日志类型为**系统日志**。

Kubernetes集群的系统日志在全文检索模块中仅支持对originalMsg（日志原文）中的内容进行全文检索，键值检索模块中支持对所有字段进行键值检索。

### 字段说明
日志字段 | 字段描述 | 字段类型 
-- | -- | -- 
cluster_id  | 集群id | string 
region_id  | 地域 | string 
source  | 日志文件名称/来源标识 | string 
stream  | 输出设备 | string 
severity  | 日志级别 | string 
time  | 日志时间, 此字段作为后端存储的时间字段 | string 
file  | 采集日志的模块名称，例如etcd kube-controller | string 
originalMsg  | 日志原文 | string 
appName  | 应用标识 | string 
container_image  | 容器镜像 | string 
container_name  | 容器名称 | string 
host  | 主机名 | string 
namespace_name  | 命名空间名称 | string 
pod_id  | pod id| string 
pod_name  | pod名称 | string 

