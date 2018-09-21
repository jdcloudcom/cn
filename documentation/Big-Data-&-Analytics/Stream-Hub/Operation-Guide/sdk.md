## SDK介绍<br>
流数据总线支持用户通过SDK的方式进行数据的写入与读取，暂时仅支持JAVA语言SDK，具体使用方法如下：<br><br>
1. **下载SDK**<br>
https://xdata.jdcloud.com/map/spsdownload/downLoadJavaSDK.action<br><br>
2. **安装SDK**<br>
请将下载的压缩文件解压，然后将jar包引入项目中，参照如下的DEMO程序进行开发。<br><br>
3. **数据写入**<br>
（1）StreamHubUpload<br>
创建StreamHubUpload有两种方式，异步调用方式和自定义调用方式。<br><br>
**异步调用方式**<br>
参数说明：<br>
accessKey : your access key<br>
secretKey: your secret key<br>
topicName: 上传数据对应的主题名称<br>
StreamHubUpload(String accessKey, StringsecretKey, String topicName)<br><br>
**自定义调用方式**<br>
参数说明：<br>
accessKey : your access key<br>
secretKey: your secret key<br>
topicName: 上传数据对应的主题名称<br>
asynchronousfalse : true :<br>
StreamHubUpload(String accessKey, StringsecretKey, String topicName, Boolean asynchronous )<br><br>
代码样例：<br>
    ```
    String endpoint = "http://streamhub-gw.jcloud.com";
    String accessKey = "Your AccessKey";
    String accessScrect = "Your AccessScrect";
    String topicName = " Your TopicName";
    StreamHubUpload  streamingHubUpload = new StreamHubUpload(accessKey,  accessScrect, topicName, endpoint);
    ```
    （2）创建上传数据对象<br>
    ```
    String msg = "单条消息";
    Entity entity = new Entity();
    entity.setKey("KEY：");
    entity.setValue("VALUE：" + msg);
    ```
    （3）调用上传方法<br>
    流式处理提供单条上传和多条上传两种数据写入方式。<br><br>
    **单条上传**<br>
    单独的记录写入数据流有两个方法:<br>
    指定分区上传方法 :putStreamRecord( Entity, Partition)<br>
    未指定分区上传方法 :putStreamRecoredNoPartiton(Entity)<br><br>
    **多条上传**<br>
    批量记录写入数据流有两个方法:<br>
    指定分区上传方法 :putStreamRecords(List, Partition )<br>
    未指定分区上传方法 :putStreamRecordsNoPartiton(List)<br><br>
    ```
    String msg = "单条消息";
    Entity entity = new Entity();
    entity.setKey("KEY：");
    entity.setValue("VALUE：" + msg);
    String recordId =  streamingHubUpload.putStreamRecord(entity, 1);
    System.out.println("upload data result : " +  recordId);
    List entities = new ArrayList();
    Entity entity1 = null;
    for (int i  = 0; i < 10; i++) {
    entity1 = new Entity();
    entity1.setKey("批量消息KEY:" + i);
    entity1.setValue("批量消息VALUE:" + i);
    entities.add(entity1);
    }
    String recordIds =  streamingHubUpload.putStreamRecords(entities, 1);
    System.out.println("upload data result : " +  recordIds);
    ```
    （4）返回结果说明<br>
    <table>
        <tr>
         <th width="300">参数</th>
         <th width="300">参数说明</th>
        </tr>
        <tr>
         <td>result</td>
         <td>true : 上传成功 |  false : 上传失败</td>
        </tr>
        <tr>
         <td>message</td>
         <td>上传返回信息</td>
        </tr>
        <tr>
         <td>code</td>
         <td>上传信息码</td>
        </tr>
    </table>
4. **数据读取**<br>
（1）创建StreamHubFetch<br>
参数说明：<br>
accessKey : your access key<br>
secretKey: your secret key<br>
topicName: 写入数据对应的主题名称<br>
StreamHubFetch(String accessKey,String secretKey, String topicName)<br><br>
代码样例：<br>
    ```
    String endpoint = "http://streamhub-gw.jcloud.com";
    String accessKey = "Your AccessKey";
    String accessScrect = "Your AccessScrect";
    String topicName = " Your TopicName";
    StreamHubFetch streamHubFetch = new StreamHubFetch(accessKey,  accessScrect, topicNam
    ```
    <br>
    （2）调用读取方法<br>
    参数说明：<br>
    partition : 分区值，用于说明从指定的分区读取数据<br>
    offset: 偏移量，用于说明读取的起始位置<br>
    数据读取方法 :fetchStreamRecord( partition, offset)<br>
        
    ```
    StreamHubFetch streamHubFetch = new StreamHubFetch(accessKey,  accessScrect, topicName, endpoint);
    String result =  streamHubFetch.fetchStreamRecord(1, 1);
    System.out.println("fetch result = ");
    System.out.println(result);
    ```
    （3）返回结果说明<br>
    <table>
        <tr>
         <th width="300">参数</th>
         <th width="500">参数说明</th>
        </tr>
        <tr>
         <td>Result</td>
         <td>true : 读取成功 | false : 读取失败</td>
        </tr>
        <tr>
         <td>message</td>
         <td>读取数据返回的提示信息</td>
        </tr>
        <tr>
         <td>code data</td>
         <td>系统返回状态码，详细情况见状态码说明部分<br>其中有两个字段，total字段表示此次读取操作获取的数据条数，<br>data字段对应的为一个JsonArray，顺序存储了读取出的数据</td>
        </tr>
    </table>
