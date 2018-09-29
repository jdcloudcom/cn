# 计费


## 简介
计费系统API接口


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**adminQueryBillStatisticsInfo**|POST|查询消费统计信息|
|**calculateCompensateFeeAndSendCoupons**|POST|计算赔偿金额并发放代金券|
|**calculateTotalPrice**|POST|查询计费价格信息|
|**getBillDetail**|GET|查询消费记录详情|
|**getExpiringOrders**|POST|查询资源单列表接口，不含已删除资源|
|**getResourceName**|GET|查询用于在账单展示的资源名称信息|
|**isArrear**|GET|查询用户是否欠费|
|**queryBillStatisticsInfo**|GET|查询资源账单，消费记录中的费用信息|
|**queryConsumeBills**|POST|查询消费记录列表|
|**queryConsumeRecords**|POST|查询资源账单详情|
|**queryConsumptionOverView**|GET|查询消费总览|
|**queryPageByCondition**|POST|查询资源单列表|
|**queryResourceBills**|POST|查询资源账单列表|
|**sendResourceOrderStatusMessage**|POST|删除资源|
