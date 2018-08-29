## 2017年3月份严重漏洞

## 漏洞简介

Struts使用的Jakarta解析文件上传请求包不当，当远程攻击者构造恶意的Content-Type，可能导致远程命令执行。

实际上在default.properties文件中，struts.multipart.parser的值有两个选择，分别是jakarta和pell（另外原本其实也有第三种选择cos）。其中的jakarta解析器是Struts2框架的标准组成部分。默认情况下jakarta是启用的，所以该漏洞的严重性需要得到正视。

## 影响范围

Struts2.3.5–Struts 2.3.31

Struts2.5–Struts 2.5.10

**修复方案**

如果你正在使用基于Jakarta的文件上传Multipart解析器，请升级到Apache Struts 2.3.32或2.5.10.1版；或者也可以切换到不同的实现文件上传Multipart解析器。

Struts 2.3.32:
https://github.com/apache/struts/releases/tag/STRUTS_2_3_32
Struts 2.5.10.1:
https://github.com/apache/struts/releases/tag/STRUTS_2_5_10_1