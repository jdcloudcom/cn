# 直播转码

京东云提供的直播转码功能为您默认开启京享超清模式转码，以更低的码率消耗实现更高质量的高性能直播转码模式。转码配置完成后，当推流开始时，转码操作自动启动。   
客户使用转码后的播放地址可观看转码后的视频流，转码播放地址有一定规则拼接，拼接规则为：  
rtmp://域名/{AppName}/{StreamName}_码率标识  
http://域名/{AppName}/{StreamName}_码率标识.flv  
http://域名/{AppName}/{StreamName}_码率标识.m3u8。  
其中“码率标识”为创建转码模板时您填入的拉取转码流标识字段。  

直播转码的配置分为两个步骤：1.创建转码模板；2.添加转码配置。   
系统为您预设了标准质量模板，如果不能满足您的转码需求，请先新建转码模板后再添加域名转码配置，转码配置完成后，对于新推上来的直播流生效。转码配置可绑定域名、APP、流三个级别，配置按最小粒度生效，举例：对于域名rtmp://abc.com/live/123，可在APP“live”级绑定转码模板A，在流“123”级绑定转码模板B，那么A模板对于APP“live”下除“123”外的其他所有流都生效，B模板对于流“123”生效。  
  
## 直播转码参数建议  

<table>
<tr>
    <td>分辨率<br/>
    <td>推荐视频码率(bps)</td>
    <td>推荐帧率(fps)</td>
    <td>推荐音频码率(bps)</td>
</tr>
<tr>
    <td>240p(426×240)<br/>
    <td>200,000~300,000</td>
    <td>15</td>
    <td>48,000</td>
</tr>
<tr>
    <td>360p(640×360)<br/>
    <td>300,000~600,000</td>
    <td>15</td>
    <td>48,000</td>
</tr>
<tr>
    <td>480p(854×480)<br/>
    <td>600,000~1000,000</td>
    <td>25</td>
    <td>64,000</td>
<tr>
    <td>720p(1280×720)<br/>
    <td>1000,000~1500,000</td>
    <td>25</td>
    <td>64,000</td>
</tr> 
<tr>
    <td>1080p(1920×1080)<br/>
    <td>1500,000~3000,000</td>
    <td>30</td>
    <td>128,000</td>
</tr>
<tr>
    <td>2k(2560×1440)<br/>
    <td>3000,000~7000,000</td>
    <td>30</td>
    <td>192,000</td>
</tr>
<tr>
    <td>4k(3840×2160)<br/>
    <td>7000,000~15000,000</td>
    <td>30</td>
    <td>256,000</td>
</tr>  
</table>
  
## 步骤1.新建模板

登录直播控制台，进入“模板管理”-“转码模板管理”页面，查看“通用转码模板”，查看以下系统预制转码模板是否符合您的转码需求，如果满足，则无需再创建新模板，在转码配置中直接调用相应模板即可。   
![](https://github.com/jdcloudcom/cn/blob/cn-Live-Video/image/live-video/9%E6%96%B0%E5%BB%BA%E8%BD%AC%E7%A0%81%E6%A8%A1%E6%9D%BF%E9%9C%80%E4%BF%AE%E6%94%B9.png)  
如果预制转码模板不能满足您的转码需求，请进入“自定义转码模板”页面添加自定义转码模板。
![](https://github.com/jdcloudcom/cn/blob/cn-Live-Video/image/live-video/10%E6%96%B0%E5%BB%BA%E8%BD%AC%E7%A0%81%E6%A8%A1%E6%9D%BF.png)
点击“添加转码模板”，按照您的实际转码输出需求，填写相应的转码视频、音频参数，点击“立即创建”即可成功创建转码模板。创建成功的转码模板会展示在转码模板列表当中。  
![](https://github.com/jdcloudcom/cn/blob/cn-Live-Video/image/live-video/11%E6%96%B0%E5%BB%BA%E8%BD%AC%E7%A0%81%E6%A8%A1%E6%9D%BF.png) 

## 步骤2.新建转码配置  

在控制台左侧菜单栏点击“域名管理”，找到需要做转码配置的直播域名组，点击“管理”，进入“转码配置”页面。
![](https://github.com/jdcloudcom/cn/blob/cn-Live-Video/image/live-video/12%E6%96%B0%E5%BB%BA%E8%BD%AC%E7%A0%81%E9%85%8D%E7%BD%AE.png)
在转码配置页面，点击“新建转码配置”，进入转码配置页面：
![](https://github.com/jdcloudcom/cn/blob/cn-Live-Video/image/live-video/13%E6%96%B0%E5%BB%BA%E8%BD%AC%E7%A0%81%E9%85%8D%E7%BD%AE.png)  
选择“全部AppName”则配置对于所有APP也就是对于整个域名生效，如果自定义指定AppName，则需要填入需要配置转码的APP名称，并可以继续选择生效范围为“全部StreamName”或自定义指定StreamName，如果自定义指定StreamName，则需要填入需要配置转码的StreamName名称。然后选择相应的转码模板，转码模板可以单选、多选。点击“立即创建”，即可完成转码配置。转码配置创建完成后，在转码配置列表即可看到刚才创建的转码规则。此条配置对于新推的直播流生效。
![](https://github.com/jdcloudcom/cn/blob/cn-Live-Video/image/live-video/14%E6%96%B0%E5%BB%BA%E8%BD%AC%E7%A0%81%E9%85%8D%E7%BD%AE.png) 
在转码配置列表中，AppName列的ALL表示刚刚创建的转码配置对于所有AppName生效即对于域名级别生效，StreamName列的ALL表示刚刚创建的转码配置对于所有StreamName生效，即对于APP级别生效。
![](https://github.com/jdcloudcom/cn/blob/cn-Live-Video/image/live-video/15%E6%96%B0%E5%BB%BA%E8%BD%AC%E7%A0%81%E9%85%8D%E7%BD%AE.png) 
