# 使用 MongoDB 的固定集合

MongoDB固定集合(Capped collections)是固定大小的循环集合，遵循插入顺序以支持创建，读取和删除操作的高性能。 通过循环，当分配给集合的固定大小被耗尽时，它将开始删除集合中最旧的文档，而不用提供任何明确的命令。

固定集合按照磁盘存储的顺序存储文档，因此可确保文档大小不会超过磁盘上分配的空间。固定集合比较适合存储日志信息，缓存数据或其他高容量数据。

## 创建固定集合

要创建一个固定集合，可使用 createCollection 命令，指定capped选项的值为true，以及以字节为单位的最大集合大小。

>db.createCollection( "log", { capped: true, size: 100000 } )

除了指定集合大小，还可以使用max参数限制集合中的文档数量。

>db.createCollection("log", { capped : true, size : 5242880, max : 5000 } )

如果要查看集合是否固定，请使用以下isCapped命令。

>db.cappedLogCollection.isCapped()

如果想要将一个集合转换为有上限的集合，则可以使用以下代码进行操作。

>db.runCommand({"convertToCapped": "mycoll", size: 100000});

此代码将现有的post转换为固定集合。

## 查询固定集合
默认情况下，在固定集合上查询将以插入顺序显示结果。 但是，如果要以相反的顺序检索文档，请使用sort命令：
 
db.cappedCollection.find().sort( { $natural: -1 } )

使用固定集合需要关注以下几点 ：

- 无法从固定集合中删除文档。
- 固定集合中没有默认索引。
- 在插入新文档时，MongoDB不需要在磁盘上实际寻找一个容纳新文档的位置。它可以随便地将新文档插入集合的尾部。这样就使得在固定集合中的插入操作非常快。
- 在读取文档的同时，MongoDB按照磁盘上存储的顺序返回文档。这样使读取操作非常快。



详细说明，请参见"[MongoDB官方文档](https://docs.mongodb.com/v3.2/core/capped-collections/)"。
