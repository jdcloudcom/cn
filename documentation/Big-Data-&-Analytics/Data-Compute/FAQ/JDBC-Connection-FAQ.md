# JDBC连接常见问题

**Q：如何通过JDBC进行数据计算服务连接？**

A：数据计算服务JDBC驱动基于presto-jdbc开发。
JDBC连接信息配置例如：</br>
String url = "jdbc:xdata://gateway.jcloud.com/instance_name"；</br>
String accessId = "xxxxxx"；</br>
String accessKey = "xxxxxxx"；</br>

其中url中的instance_name为instance名称，instance也可以通过property进行设置，如：</br>
properties.setProperty("instance", "instance_name")；</br>

目前支持华南，华北，需要在properties中增加对region的设置，华南为HN_GZ ，华北为HB_BJ</br>
properties.setProperty("region", "HB_BJ")；。</br>

点击下载新版JDBC客户端</br>
