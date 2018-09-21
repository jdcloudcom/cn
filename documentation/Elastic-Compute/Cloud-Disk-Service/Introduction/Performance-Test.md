# 性能测试

**fio 主要参数说明**

fio作者Jens Axboe是linux内核IO部分的maintainer，支持Linux下所有的IO协议栈。

----------


<table class="confluenceTable tablesorter tablesorter-default" style="color: rgb(51, 51, 51); margin: 0px; overflow-x: auto;" width="718"><thead><tr class="tablesorter-headerRow firstRow"><th class="confluenceTh sortableHeader" style="border: 1px solid rgb(221, 221, 221); padding: 7px 15px 7px 10px; vertical-align: top; text-align: left; background: right center no-repeat rgb(240, 240, 240); color: rgb(0, 0, 0); cursor: pointer; user-select: none;"><p>参数</p></th><th class="confluenceTh sortableHeader" style="border: 1px solid rgb(221, 221, 221); padding: 7px 15px 7px 10px; vertical-align: top; text-align: left; background: right center no-repeat rgb(240, 240, 240); color: rgb(0, 0, 0); cursor: pointer; user-select: none;"><p>说明</p></th></tr></thead><tbody><tr><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top; word-break: break-all;" width="66"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">--bs</span></td><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top;" width="332"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">Block size for I/O units.</span></td></tr><tr><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top;" width="66"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">--direct</span></td><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top;" width="332"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">no buffered IO</span></td></tr><tr><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top;" width="66"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">--iodepth</span></td><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top;" width="332"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">异步IO模式中一次提交一批请求的队列长度</span></td></tr><tr><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top;" width="66"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">--ioengine</span></td><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top;" width="332"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">IO模式支持libaio、sync、psync、vsync等</span></td></tr><tr><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top;" width="66"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">--norandommap</span></td><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top;" width="332"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">一般情况下，fio在做随机IO时，将会覆盖文件的每一个block.如果这个选项设置的话，fio将只是获取一个新的随机offset,而不会查询过去的历史。这意味着一些块可能没有读或写，一些块可能要读/写很多次。</span></td></tr><tr><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top;" width="66"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">--numjobs</span></td><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top;" width="332"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">并发进程/线程数</span></td></tr><tr><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top;" width="66"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">--runtime</span></td><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top;" width="332"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">执行时间</span></td></tr><tr><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top;" width="66"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">--rw</span></td><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top;" width="332"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">读写模式</span></td></tr><tr><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top;" width="66"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">--size</span></td><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top; word-break: break-all;" width="332"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">IO测试文件大小</span></td></tr></tbody></table>

----------

## 磁盘性能测试方法

- 随机写

```
fio -ioengine=libaio -numjobs=64 -bs=4k -direct=1 -rw=randwrite -size=20G -filename=/root/randwrite_20G -name=test -iodepth=32 -runtime=120 --group_reporting --output=/root/fio_test/hdd_randwrite_4k
```

- 随机读


```
fio -ioengine=libaio -numjobs=64 -bs=4k -direct=1 -rw=randread -size=20G -filename=/root/randread_20G -name=test -iodepth=32 -runtime=120 --group_reporting --output=/root/fio_test/hdd_randread_4k
```

- 顺序读


```
fio -ioengine=libaio -numjobs=64 -bs=1M -direct=1 -rw=read -size=10G -filename=/root/read_10G -name=test -iodepth=32 -runtime=120 --group_reporting --output=/root/fio_test/read_1M
```

- 顺序写


```
fio -ioengine=libaio -numjobs=64 -bs=1M -direct=1 -rw=write -size=10G -filename=/root/write_10G -name=test -iodepth=32 -runtime=120 --group_reporting --output=/root/fio_test/write_1
```



生成的group_report数据项说明：


----------


<table class="confluenceTable tablesorter tablesorter-default" style="color: rgb(51, 51, 51); margin: 0px 0px 0px 60px; overflow-x: auto;"><thead style="margin-left: 60px;"><tr class="tablesorter-headerRow firstRow" style="margin-left: 60px;"><th class="confluenceTh sortableHeader" style="border: 1px solid rgb(221, 221, 221); padding: 7px 15px 7px 10px; vertical-align: top; text-align: left; background: right center no-repeat rgb(240, 240, 240); color: rgb(0, 0, 0); cursor: pointer; margin-left: 60px; user-select: none; word-break: break-all;"><p><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">数据项</span></p></th><th class="confluenceTh sortableHeader" style="border: 1px solid rgb(221, 221, 221); padding: 7px 15px 7px 10px; vertical-align: top; text-align: left; background: right center no-repeat rgb(240, 240, 240); color: rgb(0, 0, 0); cursor: pointer; margin-left: 60px; user-select: none;"><p><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">说明</span></p></th></tr></thead><tbody style="margin-left: 60px;"><tr style="margin-left: 60px;"><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top; margin-left: 60px; word-break: break-all;"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">io</span></td><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top; margin-left: 60px;"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">执行了多少M的IO</span></td></tr><tr style="margin-left: 60px;"><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top; margin-left: 60px;"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">bw</span></td><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top; margin-left: 60px;"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">平均IO带宽</span></td></tr><tr style="margin-left: 60px;"><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top; margin-left: 60px;"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">iops</span></td><td class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top; margin-left: 60px;"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">IOPS</span></td></tr><tr style="margin-left: 60px;"><td colspan="1" class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top; margin-left: 60px;"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">runt</span></td><td colspan="1" class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top; margin-left: 60px;"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">运行时间</span></td></tr><tr style="margin-left: 60px;"><td colspan="1" class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top; margin-left: 60px;"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">slat</span></td><td colspan="1" class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top; margin-left: 60px;"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">提交延迟</span></td></tr><tr style="margin-left: 60px;"><td colspan="1" class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top; margin-left: 60px;"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">clat</span></td><td colspan="1" class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top; margin-left: 60px;"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">完成延迟</span></td></tr><tr style="margin-left: 60px;"><td colspan="1" class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top; margin-left: 60px;"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">lat</span></td><td colspan="1" class="confluenceTd" style="border: 1px solid rgb(221, 221, 221); padding: 7px 10px; vertical-align: top; margin-left: 60px;"><span style="font-family: 微软雅黑, &quot;Microsoft YaHei&quot;; font-size: 14px;">响应时间</span></td></tr></tbody></table>





