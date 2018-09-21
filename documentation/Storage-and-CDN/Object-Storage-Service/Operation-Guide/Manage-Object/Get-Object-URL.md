# 获取外链

您已经将文件上传到存储空间中，您可以随时通过获取已上传文件的外链地址进行文件的分享和下载，操作过程如下：

1.进入对象存储控制台，进入空间管理，在空间列表中单击您要访问的存储空间，进入后点击Object管理页签：

2.找到需要获取外链的文件，点击“获取外链”按钮：

![获取外链](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-047.png)

3.若当前存储空间的访问权限为“公有读私有写”，则获取外链弹窗如下所示，直接点击外链文本右侧的复制按钮可以将文件外链地址复制到剪贴板中，此外链地址可以随时对外提供服务，无有效时间限制：

![复制外链](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-048.png)

4.若当前存储空间的访问权限为“私有读写”，则获取外链弹窗如下所示，外链地址需要设置有效时间，输入有效时间后点击“获取外链”按钮，则可获取到该文件的外链：

![外链有效期](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-049.png)

![获取外链](https://github.com/jdcloudcom/cn/blob/edit/image/Object-Storage-Service/OSS-050.png)

注意：

1.当存储空间访问权限为“私有读写”时，给该存储空间下的文件设置外链有效期，外链地址在设置的有效时间范围内可以随意访问，若超出有效时间范围，则外链地址无法访问；

2.存储空间为私有权限时获得的地址是通过URL签名方式生成的。
