# 搜索文件

京东云对象存储支持按照文件名前缀匹配的方式在存储空间中搜索文件或文件夹，按名称前缀进行搜索时，搜索字符串将区分大小写，并且不能包含正斜杠“/”字符。搜索的范围限定为当前存储空间的根级别或当前文件夹中的对象（不包括子文件夹及其所包含的对象）。

### 搜索操作步骤如下：

1.登录京东云对象存储控制台，并进入某一空间的空间管理->Object管理页，在右侧的搜索框中输入待搜索的内容，输入完成后点击回车键或搜索按钮：

![搜索](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-045.png)

2.搜索后返回符合查询条件的文件列表：
![结果](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-046.png)
