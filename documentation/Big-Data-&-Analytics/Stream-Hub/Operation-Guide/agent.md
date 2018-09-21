## Agent介绍<br>
数据总线支持以Agent方式进行数据写入，具体使用方法如下：<br><br>
1. **下载地址**<br>
https://xdata.jdcloud.com/map/spsdownload/downLoadAgent.action<br><br>
2. **配置说明**<br>
将下载的Agent压缩包，解压到/home/flumedir路径下，在conf文件夹下添加properties文件，例如test.properties，具体配置文件详细说明如下：<br><br>
3. **定义Source**<br>
    <table>
        <tr>
            <th width="300">属性名称</th>
            <th width="300">默认值</th>
            <th width="600">描述</th>
        </tr>
         <tr>
            <td>Type</td>
            <td></td>
            <td>source组件名称</td>
        </tr>
        <tr>
            <td>filegroups</td>
            <td></td>
            <td>文件组名称，空格分隔文件组列表</td>
        </tr>
        <tr>
            <td>filegroups.</td>
            <td></td>
            <td>指定filegroupName对应的文件路径</td>
        </tr>
        <tr>
            <td>positionFile</td>
            <td>~/.flume/taildir_position.json</td>
            <td>记录当前文件访问的位置，生成json记录放在该文件中</td>
        </tr>
        <tr>
            <td>headers..</td>
            <td></td>
            <td>头信息，用于区分不同文件中传入的数据</td>
        </tr>
        <tr>
            <td>byteOffsetHeader</td>
            <td>false</td>
            <td>是否需要添加字节偏移量</td>
        </tr>
        <tr>
            <td>skipToEnd</td>
            <td>false</td>
            <td>如果没有记录读取位置时，是否跳过文件结尾</td>
        </tr>
        <tr>
            <td>fileHeader</td>
            <td>false</td>
            <td>Event header中是否添加headerKey</td>
        </tr>
        <tr>
            <td>fileHeaderKey</td>
            <td>file</td>
            <td>文件路径信息，在event header中对应的key值</td>
        </tr>
    </table>
   <br>
    配置示例:<br>
    
    **定义sources名称**<br>
    `streaming.sources=tailDirSrc`<br><br>
     **定义Sourceype:**<br>
    TAILDIR类型: 该类型可以读取文件夹里的日志，使用时指定一个文件夹，可以读取该文件夹中的所有文件<br>
    `streaming.sources.tailDirSrc.type=TAILDIR`<br><br>
    exec类型: Exec Source在启动时运行给定的Unix命令，并期望进程在标准输出上产生连续的数据<br>
    `streaming.sources.tailDirSrc.type=exec`<br>
    `streaming.sources.tailDirSrc.command = tail -F /var/log/secure`<br>    
    **定义文件读取位置存储位置**
    `streaming.sources.tailDirSrc.positionFile=/home/flumedir/flumeplugin/data/taildir_position.json`<br><br>
    **定义上传文件组**<br>
    `streaming.sources.tailDirSrc.filegroups=one two`<br><br>
    **分别定义文件信息**<br>
    `streaming.sources.tailDirSrc.filegroups.one=/home/flumedir/flumeplugin/data/test.txt`<br>
    `streaming.sources.tailDirSrc.headers.one.headerKey=one`<br><br>
    `streaming.sources.tailDirSrc.filegroups.two=/home/flumedir/flumeplugin/data/test2.txt`<br>
    `streaming.sources.tailDirSrc.headers.two.headerKey=two1`<br><br>
    **headerkeyheader**<br>
    `streaming.sources.tailDirSrc.fileHeader=true`<br><br>
    **header eventkey**<br>
    `streaming.sources.tailDirSrc.fileHeaderKey=file`<br><br>
4. **定义channel**<br>
配置示例如下：<br>
**定义channel名称**<br>
`streaming.channels=memoryChannel`<br><br>
**定义channel类型, channel的类型可以配置为memory, file, 此处用memory**<br>
`streaming.channels.memoryChannel.type=memory`<br><br>
**定义memory channel容量大小**<br>
`streaming.channels.memoryChannel.capacity=1000`<br><br>
**定义transactionCapacity大小, source的ChannelProcessor一次可以向channel中写入的最大event数量，该组件负责在一个事务中移动source中的event到channel中**<br>
`streaming.channels.memoryChannel.transactionCapacity =1000`<br><br>
5. **定义sink**<br>
StreamingSink参数说明：<br>
    <table>
        <tr>
            <th width="150">属性名称</th>
            <th width="100">是否必须</th>
            <th width="600">描述</th>
        </tr>
         <tr>
            <td>Type</td>
            <td>是</td>
            <td>sinktype名称：com.jcloud.flume.plugin.sink.streaming.StreamingSink</td>
        </tr>
        <tr>
            <td>uploadType</td>
            <td>是</td>
            <td>标识为true:上传给有schema的数据流;false：上传给没有schema的数据流</td>
        </tr>
        <tr>
            <td>appKey</td>
            <td>是</td>
            <td>您的京东账号app key</td>
        </tr>
        <tr>
            <td>appSecret</td>
            <td>是</td>
            <td>您的京东账号app secret</td>
        </tr>
        <tr>
            <td>streamingName</td>
            <td>是</td>
            <td>上传数据对应的topic name</td>
        </tr>
        <tr>
            <td>batchSize</td>
            <td>是</td>
            <td>批量提交信息数量</td>
        </tr>
        <tr>
            <td>serverUrl</td>
            <td>否</td>
            <td>上传数据对应的服务器地址</td>
        </tr>
    <table>
                                
    **sink对应名称**<br>
    `streaming.sinks=streamingSink`<br><br>
    **定义sink类型**<br>
    `streaming.sinks.streamingSink.type=com.jcloud.flume.plugin.sink.streaming.StreamingSink`<br><br>
    **定义上传数据流是否存在scheam**<br>
    `streaming.sinks.streamingSink.uploadType=false`<br><br>
    **定义用户身份标识**<br>
    `streaming.sinks.streamingSink.appKey=＜your app key＞`<br>
    `streaming.sinks.streamingSink.appSecret=＜your app secret key＞`<br>
    `streaming.sinks.streamingSink.streamingName=＜流总线topic名称＞`<br>
    `streaming.sinks.streamingSink.batchSize=100`<br>
    `streaming.sinks.streamingSink.serverUrl=http://streamhub-gw.jcloud.com`<br><br>    
    (1)	公网地址：<br>
    华南: http://streamhub-gw.jcloud.com<br>
    华北: http://hb-streamhub-gw.jcloud.com<br><br>	
    (2)	内网地址：<br>
    华南: streamhub-gw-inner.jcloud.com<br>
    华北: hb-streamhub-gw-inner.jcloud.com<br><br>
6. **定义source对应channel**<br>
**sourcechannel**<br>
`streaming.sources.tailDirSrc.channels=memoryChannel`<br><br>
7. **定义sink对应channel**<br>
**sinkchannel**<br>
`streaming.sinks.streamingSink.channel=memoryChannel`<br><br>
8. **启动Agent**<br>
注：启动Agent之前请确认已正确安装JDK并配置环境变量。<br>
在bin目录下执行如下命令：<br>
`./flume-ng agent -nstreaming -c conf -f ../conf/test.properties -Dflume.root.logger=INFO,LOGFILE,console`<br><br>

**Tips: 常见的内存OOM问题解决方案**<br>
首先限制JVM的内存使用，在flume的flume-env.sh配置文件中配置JVM参数<br>
`JAVA_OPTS="-Xms1000m -Xmx1000m"`<br>
这里的例子是配置1000M，可以根据对应的机器内存进行灵活配置，同时配合修改channel的capacity和transactionCapacity，如果自己的内存比较小，这里的参数也应设置的比较小，在配置完JVM的参数以后，启动agent时应加上-c conf 选项，否则配置不会生效。例如：<br>
`bin/flume-ng agent -n streaming -c conf -f conf/flume-conf.properties -Dflume.root.logger=INFO,LOGFILE,console > faoling.log`<br>
另一种方案是channel的类型不使用内存，使用文件，使用文件的时候要比使用内存效率低，可以根据实际情况灵活使用，如果本机配置不高或者日志生成速度比较慢可以考虑使用。<br>