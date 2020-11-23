# certificateTemplate


## 描述
域名信息模板实名认证

## 请求方式
POST

## 请求地址
https://domain.jdcloud-api.com/v1/regions/{regionId}/template/{templateId}/certificate

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True| |实例所属的地域ID|
|**templateId**|Long|True| |模板ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**identityNo**|String|True| |所有人证件号码|
|**identityType**|String|True| |注册人证件类型<br>1.个人<br>  (1)身份证 SFZ<br>2.企业<br>  (1)组织机构代码证 ORG<br>  (2)工商营业执照 YYZZ<br>  (3)统一社会信用代码证书 TYDMZ<br>  (4)部队代号 BDDH<br>  (5)军队单位对外有偿服务许可证 JDXKZ<br>  (6)事业单位法人证书 SYZS<br>  (7)社会团体法人登记证书 STDJZ<br>  (8)宗教活动场所登记证 ZJDJZ<br>  (9)民办非企业单位登记证书 MBDJZ<br>  (10)基金会法人登记证书 JJDJZ<br>  (11)律师事务所执业许可证 LSXKZ<br>  (12)登记证 GWLYDJZ<br>  (13)司法鉴定许可证 SFXKZ<br>  (14)社会服务机构登记证书 SHFWJGZ<br>  (15)民办学校办学许可证 MBXXXKZ<br>  (16)医疗机构执业许可证 YLJGXKZ<br>|
|**file**|String|True| |所有人证件，jpg 图片的 base64 编码，必填（大小 55KB~1MB）|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|[Result](certificateTemplate#result)| |
|**requestId**|String|此次请求的ID|

### <div id="Result">Result</div>
|名称|类型|描述|
|---|---|---|
|**templateId**|Long|模板Id|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|BAD_REQUEST|
