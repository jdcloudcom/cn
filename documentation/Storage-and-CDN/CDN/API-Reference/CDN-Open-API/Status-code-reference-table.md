# **提示信息状态码参照表**

ACTIVE_EXCEPTION(-1, "接口调用异常"),

ACTIVE_SUCCESS(0, "成功"),

ACTIVE_FAILURE(1, "失败"),

ERROR_PARAMS_NOT_NULL(2, "参数不能为空"),

ERROR_USERNAME_NOT_NULL(3, "用户名不能为空"),

ERROR_SIGNATURE_NOT_NULL(4, "用户签名不能为空"),

ERROR_TYPE_NOT_NULL(5, "类型不能为空"),

ERROR_INSTANCES_NULL(6, "刷新的文件或目录列表不能为空"),

ERROR_INSTANCES_100(9, "单次刷新不能超过100个URL"),

ERROR_PUBLISH_URLS_50(10, "待预热的文件url不能超过50个"),

ERROR_SIGNATURE(7, "用户签名不正确"),

ERROR_FREEALL(8, "调用接口失败"),

 

ERROR_TASKID_NOT_NULL(11, "任务id不能为空"),

ERROR_DOMAIN_NULL(12, "待查询的域名不能为空"),

ERROR_STARTTIME_NULL(13, "开始时间不能为空"),

ERROR_DATE_FORMAT(14, "时间格式不符要求，请设置时间格式为yyyy-MM-dd HH:mm"),

ERROR_NOT_USERDOMAIN(15, "刷新的域名中有不属于您的域名"),

 

ERROR_TYPEERROR_NULL(16, "type格式错误"),

ERROR_URLHTTP_ERROR(17, "刷新或者预热的域名不合法"),

ERROR_ONLY_USERDOMAIN(18, "检测到有不属于您的域名"),

ERROR_STARTTIMELARGE(19, "开始时间不能大于结束时间 "),

ERROR_BEFOREMONTH(21, "日期必须在当前日期一个月内 "),

ERROR_USERNAME_ERROR(20, "用户名不存在"),

ERROR_QUERY_DOMAIN_50(22, "查询域名个数不能超过您加速的域名个数"),

ERROR_DOMAINTYPE(23, "加速域名type错误，必须为web，download，vod中一种"),

ERROR_DOMAIN_SOURCETYPE(24, "回源type错误，必须为ips，domain，oss中一种"),

ERROR_SOURCE(25, "回源数据必须为json数组格式"),

ERROR_DOMAINSTATUS(26, "域名操作必须选择start，stop，delete中的一种"),

ERROR_WEIGHT_NOTNULL(27, "缓存配置权重不能为空"),

ERROR_TTL_NOTNULL(28, "缓存配置缓存时间不能为空"),

ERROR_CONTENT_NOTNULL(29, "缓存配置缓存内容不能为空"),

ERROR_CONFIGID_NOTNULL(30, "缓存配置ID不能为空"),

ERROR_CACHE_STATUS(31, "缓存配置必须选择add，update，delete中的一种"),

ERROR_SOURCEHOST_NOTNULL(32, "回源host不能为空"),

ERROR_CERTIFICATE_NOTNULL(33, "通信协议是https时，证书不能为空"),

ERROR_RSAKEY_NOTNULL(34, "通信协议是https时，私钥不能为空"),

ERROR_IGNORE_NOTNULL(35, "设置忽略参数状态不能为空"),

ERROR_REFERTYPE_NOTNULL(36, "refer类型不能为空"),

ERROR_REFERLIST_NOTNULL(37, "referList不能为空"),

ERROR_ACCESSKEYTYPE_NOTNULL(38, "URL鉴权类型不能为空"),

ERROR_ACCESSKEYKEY_NOTNULL(39, "URL鉴权密码不能为空"),

ERROR_ACCESSKEYKEEP_NOTNULL(40, "URL回源鉴权"),

ERROR_FIELD_NULL(41, "待查询的字段不能为空"),

ERROR_DATE_OUT(42, "只允许查询7天的数据"),

ERROR_DATE_OUTONE(43, "只允许查询1天的数据"),

ERROR_DATE_OUT31(44, "只允许查询31天的数据"),

ERROR_DATE_OUT30(45, "只允许查询30天的数据"),

ERROR_INSTANCES_5(46, "单次刷新的目录不能超过5个"),

ERROR_NOT_REFRSHREPEAET(47, "刷新或者预热的地址有重复"),