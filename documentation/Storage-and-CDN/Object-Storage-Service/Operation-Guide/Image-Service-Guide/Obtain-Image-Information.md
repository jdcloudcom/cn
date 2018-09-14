# 获取图片信息

获取图片基本信息及exif信息

参数：

|操作方式|指令含义|参数格式|参数说明|结果说明|
|-|-|-|-|-|
|保留jpg，webp，tiff图片meta信息|Not strip|ns|默认去除所有格式图片meta信息<br>指定ns后，保留||
|获取图片基本信息|Image information|imginfo|可选参数|返回json格式结果，包含：<br>format图片格式<br>width宽<br>height高<br>fileSize文件字节数<br>imgType文件类型，取值范围[0 UndefinedType,<br>1 BilevelType,<br>2 GrayscaleType,<br>3 GrayscaleMatteType,<br>4 PaletteType,<br>5 PaletteMatteType,<br>6 TrueColorType,<br>7 TrueColorMatteType,<br>8 ColorSeparationType,<br>9 ColorSeparationMatteType,<br>10 OptimizeType]<br>orientation原始EXIF方向，取值范围[<br>0 UndefinedOrientation,<br>1 TopLeftOrientation,<br>2 TopRightOrientation,<br>3  BottomRightOrientation,<br>4 BottomLeftOrientation,<br>5 LeftTopOrientation,<br>6 RightTopOrientation,<br>7 RightBottomOrientation,<br>8 LeftBottomOrientation]|
|获取图片EXIF信息|Image EXIF|Imgexif|可选参数|支持jpg，tiff格式图片| 

示例：

获取图片基本信息：

http://oss.cn-north-1.jcloudcs.com/downloads/example.jpg?x-oss-process=imginfo/ns

返回结果：

{"format":"JPEG","width":350,"height":236,"fileSize":38539,"imgType":6,"orientation":1}

获取图片EXIF信息：

http://oss.cn-north-1.jcloudcs.com/downloads/example.jpg?x-oss-process=imgexif

返回结果：
```
{"FileType":"JPEG","FileSize":"38539","ImageWidth":"350","ImageHeight":"236","Make":"Canon","Model":"Canon EOS 1100D","Software":"www.meitu.com","ExposureTime":"1/200","ExifOffset":"118","ExposureTime":"1/200","FNumber":"5/1","ISOSpeedRatings":"160, 0","DateTimeOriginal":"2013:05:17 16:21:36","Flash":"16, 0","FocalLength":"140/1","LensModel":"EF75-300mm f/4-5.6"}
```
