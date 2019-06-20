# 产品规格

云物理服务器提供以下实例规格类型：标准计算型、计算效能型Ⅰ、计算效能型Ⅱ、标准存储型、计算效能型Ⅰ(二代)和标准存储型（二代）。GPU型云物理服务器目前有GPUⅠ、GPUⅡ和GPUⅢ。更多机型即将上线。

<table align="center" >
<table>
    <tr>
        <td align="center"><B>实例规格</B></td> 
        <td align="center"><B>CPU</B></td> 
		    <td align="center"><B>内存</B></td>
		    <td align="center"><B>硬盘</B></td>
		    <td align="center"><B>网卡</B></td>
	    <td align="center"><B>支持RAID模式</B></td>
    </tr>
    <tr>   
        <td align="center"><B>标准计算型<br/>（cps.c.normal）<B></td>
		    <td align="center">2*2683V4<br/>（16核 2.1G）</td>
		    <td align="center">256G（8*32G）DDR4</td>
		    <td >2*300GB（SAS）+<br/>2*800GB（SSD）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">NO RAID/RAID0/RAID1</td>
    </tr>
	  <tr>   
        <td align="center"><B>计算效能型Ⅰ<br/>（cps.c.perf1）<B></td>
		    <td align="center">2*2683V4<br/>（16核 2.1G）</td>
		    <td align="center">256G（8*32G）DDR4</td>
		    <td >2*300GB（SAS）+<br/>1*4000GB（NVME）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">NO RAID</td>
    </tr>
    <tr>   
        <td align="center"><B>计算效能型Ⅱ<br/>（cps.c.perf2）<B></td>
		    <td align="center">2*2683V4<br/>（16核 2.1G）</td>
		    <td align="center">256G（8*32G）DDR4</td>
		    <td >1*240GB（SSD）+<br/>16*960GB（SSD）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">NO RAID/RAID0/RAID1/RAID10</td>
    </tr>
    <tr>   
        <td align="center"><B>标准存储型<br/>（cps.s.normal）<B></td>
		    <td align="center">2*2650V4<br/>（12核 2.2G）</td>
		    <td align="center">256G（8*32G）DDR4</td>
		    <td >2*300GB（SAS）+<br/>12*6TB（SATA）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">NO RAID</td>
    </tr>
    <tr>   
        <td align="center"><B>计算效能型Ⅰ(二代)<br/>（cps.c2.perf1）<B></td>
		    <td align="center">2*Gold-6148<br/>（40核 2.4G）</td>
		    <td align="center">384G（12*32G）DDR4</td>
		    <td >1*240GB（SSD）+<br/>1*2TB（NVME）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">NO RAID</td>
    </tr>
    <tr>   
        <td align="center"><B>标准存储型（二代）<br/>（cps.s2.normal）<B></td>
		    <td align="center">2*Silver-4116<br/>（24核 2.1G）</td>
		    <td align="center">256G（8*32G）DDR4</td>
		    <td >2*300GB（SAS）+<br/>12*10TB（SATA）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">NO RAID/RAID0/RAID1/RAID10</td>
    </tr>
</table>

GPU型云物理服务器实例规格如下：

<table>
    <tr>
        <td align="center"><B>实例规格</B></td> 
        <td align="center"><B>CPU</B></td> 
		    <td align="center"><B>内存</B></td>
		    <td align="center"><B>硬盘</B></td>
		    <td align="center"><B>网卡</B></td>
	    	<td align="center" ><B>GPU</B></td>
	    <td align="center"><B>支持RAID模式</B></td>
    </tr>
    <tr>   
        <td align="center"><B>GPUⅠ<br/>（cps.gpu.1）<B></td>
		    <td align="center">2*2683V4<br/>（16核 2.1G）</td>
		    <td align="center">256G（8*32G）DDR4</td>
		    <td >2*300GB（SAS）+<br/>6*960GB（SSD）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">NVIDIA P40*4</td>
		<td align="center">NO RAID/RAID0/RAID10</td>
    </tr>
    <tr>   
        <td align="center"><B>GPUⅡ<br/>（cps.gpu.2）<B></td>
		    <td align="center">2*2650V4<br/>（12核 2.2G）</td>
		    <td align="center">256G（8*32G）DDR4</td>
		    <td >2*300GB（SAS）+<br/>4*4000GB（SATA）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">NVIDIA P40*4</td>
		<td align="center">NO RAID/RAID0/RAID10</td>
    </tr>
    <tr>   
        <td align="center"><B>GPUⅢ<br/>（cps.gpu.3）<B></td>
		    <td align="center">2*2650V4<br/>（12核 2.2G）</td>
		    <td align="center">256G（8*32G）DDR4</td>
		    <td >2*300GB（SAS）+<br/>6*6000GB（SATA）</td>
		    <td align="center">独立管理口1块+<br/>2*10GE网卡</td>
		<td align="center">NVIDIA V100*4</td>
		<td align="center">NO RAID/RAID0/RAID10</td>
    </tr>
</table>
