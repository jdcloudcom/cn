# xDatacmd

xDatacmd工具以客户端命令行的形式实现数据的批量上传下载处理，支持命令行交互模式和批处理模式；对于批处理模式提供多种可选择的格式样式输出。目前支持本地文件上载、数据库（mysql、oracle、sql server、DB2等）的上载、数据仓库表下载。

**如何下载** **xDatacmd**

下载地址如下：<https://xdata.jcloud.com/map/spsdownload/downLoadClient.action>

**运行环境要求**

JDK1.7及以上

**如何配置？**

使用命令行时，需要配置xdata_config.ini。下载xDatacmd客户端文件后，进行解压缩。进入conf文件，找到xdata_config.ini文件进行配置，添加用户默认数据库以及用户认证信息。