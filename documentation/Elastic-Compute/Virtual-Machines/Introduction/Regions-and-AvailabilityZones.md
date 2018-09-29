# 地域及可用区
京东云云主机机房分布在全球多个位置，这些位置成为地域。每个地域（region）都是一个独立的地理区域，每个地域都是完全独立的。

京东云支持您在不同地域部署云业务，同时为了避免单地域部署可能带来的单点风险，建议在部署方案设计阶段考虑多地域多可用区部署。实例创建后，不支持更换地域或更换可用区。

可用区（Availability Zone）是电力及网络之间互相独立的物理区域，相同可用区内的实例之间较之同地域不同可用区内实例之间的网络延时更小。同地域内不同可用区之间提供内网互通环境，可用区之间可做到故障隔离。

* 若您的业务要求有较高容灾能力，建议将实例部署在同一地域不同可用区内；
* 若您的业务要求有较低网络时延，建议将实例部署在同一可用区内。


## 京东云地域及可用区分布
<table>
	<thead>
	<tr>
		<th colspan="2">地域名称及编码</th>
      	<th>可用区名称及编码</th>
      	<th>所在城市</th>
   	</tr>
		</thead>
	<tbody>
   	<tr>
      	<td rowspan="6">中国大陆地域</td>
      	<td rowspan="2">华北-北京<br>cn-north-1</td>
     	<td> 可用区A<br>cn-north-1a</td>
	   	<td> 北京</td>
   </tr>
		
   <tr>
     	<td> 可用区B<br>cn-north-1b</td>
	   	<td> 北京</td>
   </tr>
   <tr>
     	<td>华东-宿迁<br>cn-east-1</td>
     	<td>可用区A<br>cn-east-1a</td>
	   	<td>宿迁</td>
   </tr>
   </tr>
    	<tr>
     	<td rowspan="2">华东-上海<br>cn-east-2</td>
     	<td>可用区A<br>cn-east-2a</td>
	   	<td>上海</td>
   </tr>
      </tr>
    	<tr>
     	<td>可用区B<br>cn-east-2b</td>
	   	<td>上海</td>
   </tr>
  <tr>
     	<td>华南-广州<br>cn-south-1</td>
     	<td>可用区A<br>cn-south-1a</td>
	   	<td>广州</td>
   </tr>
   </tbody>
</table>

![](../../../../image/vm/region-and-az.png)
