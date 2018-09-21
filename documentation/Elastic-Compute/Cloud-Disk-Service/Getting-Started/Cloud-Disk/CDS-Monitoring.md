# 云硬盘监控

<br>

京东云为已挂载到云主机上的云硬盘提供了长达30天的监控数据，让您实时掌握云硬盘运行情况及性能监控指标。目前云硬盘提供了如下监控指标：

<table class="confluenceTable tablesorter tablesorter-default">
    <thead>
        <tr class="tablesorter-headerRow firstRow">
            <th style="background: no-repeat right rgb(240, 240, 240); text-align: left; color: rgb(0, 0, 0); padding-top: 7px; padding-right: 15px; padding-bottom: 7px; vertical-align: top; border-top-color: rgb(221, 221, 221); cursor: pointer; user-select: none;" class="confluenceTh sortableHeader">
                <p>
                    <span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">监控项</span>
                </p>
            </th>
            <th style="background: no-repeat right rgb(240, 240, 240); text-align: left; color: rgb(0, 0, 0); padding-top: 7px; padding-right: 15px; padding-bottom: 7px; vertical-align: top; border-top-color: rgb(221, 221, 221); cursor: pointer; user-select: none;" class="confluenceTh sortableHeader">
                <p>
                    <span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">含义</span>
                </p>
            </th>
            <th style="background: no-repeat right rgb(240, 240, 240); text-align: left; color: rgb(0, 0, 0); padding-top: 7px; padding-right: 15px; padding-bottom: 7px; vertical-align: top; border-top-color: rgb(221, 221, 221); cursor: pointer; user-select: none;" class="confluenceTh sortableHeader" colspan="1">
                <p>
                    <span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">单位</span>
                </p>
            </th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top;" class="confluenceTd">
                <span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">磁盘读取带宽</span>
            </td>
            <td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top;" class="confluenceTd">
                <span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">平均每秒把数据从磁盘读到内存的数据量</span>
            </td>
            <td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top;" class="confluenceTd" colspan="1">
                <span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">bps</span>
            </td>
        </tr>
        <tr>
            <td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top;" class="confluenceTd" colspan="1">
                <span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">磁盘写入带宽</span>
            </td>
            <td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top;" class="confluenceTd" colspan="1">
                <span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">平均每秒把数据从内存写到磁盘的数据量</span>
            </td>
            <td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top;" class="confluenceTd" colspan="1">
                <span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">bps</span>
            </td>
        </tr>
        <tr>
            <td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top;" class="confluenceTd" colspan="1">
                <span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">磁盘读取IOPS</span>
            </td>
            <td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top;" class="confluenceTd" colspan="1">
                <span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">平均每秒读数据操作请求个数</span>
            </td>
            <td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top;" class="confluenceTd" colspan="1">
                <span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">个/秒</span>
            </td>
        </tr>
        <tr>
            <td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top;" class="confluenceTd">
                <span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">磁盘写入IOPS</span>
            </td>
            <td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top;" class="confluenceTd">
                <span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">平均每秒写数据操作请求个数</span>
            </td>
            <td style="padding-top: 7px; padding-bottom: 7px; vertical-align: top;" class="confluenceTd" colspan="1">
                <span style="color: rgb(0, 0, 0); font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">个/秒</span>
            </td>
        </tr>
    </tbody>
</table>


查看某一云硬盘的监控请参考如下步骤：

1、打开[京东云控制台](https://console.jdcloud.com/)，选择【弹性计算】-【云主机】-【云硬盘】；

2、进入云硬盘列表页后找到需要查看的云硬盘，点击云硬盘列表中对应云硬盘名称跳转到其详情页面；

3、选择"监控"Tab页查看云硬盘的监控项；

**注**：

1）仅状态为"已绑定"的云硬盘有监控数据；

2）可在云硬盘详情页左上角查看云硬盘名称、状态；


<br>
<br>

![](https://github.com/jdcloudcom/cn/blob/edit/image/Elastic-Compute/CloudDisk/cloud-disk/cloud-disk-019.png)

<br>

4、监控图：目前提供折线图展示，可查看最近30天内的监控数据，采样数据最小周期为1分钟。

更多详情，请参考[云监控](https://www.jdcloud.com/help/detail/94/isCatalog/1)帮助中心。
