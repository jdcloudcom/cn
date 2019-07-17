
# 创建原生容器Pod  
**前提条件**  
在创建原生容器Pod前，您需要完成以下步骤  
1.注册京东云账号并激活、认证账号，可分别访问[注册京东云](https://accounts.jdcloud.com/p/regPage?source=jdcloud%26ReturnUrl=%2f%2fuc.jdcloud.com%2fpassport%2fcomplete%3freturnUrl%3d//www.jdcloud.com/)、[登录京东云](https://console.jdcloud.com/overview)、[实名认证](https://uc.jdcloud.com/account/verify)进行操作；  
2.若您需要创建按配置计费实例，您需要保证您的余额不低于50元，若当前余额不足请进行充值；  
3.您必选先创建私有网络、子网；  
4.若您需要使用安全组进行实例的安全访问控制，您可预先创建安全组或重新配置安全组出站规则、入站规则。  
**操作步骤**  
 1. 打开控制台，选择[弹性计算>>原生容器>>Pod](https://cns-console.jdcloud.com/host/pod/list)；  
 2. 选择创建原生容器Pod所属地域，点击“创建”按钮，进入原生容器Pod购买页面，建议您根据业务情况选择实例所在地域及可用区；      
 3. 选择计费模式：包年包月和按配置计费，包年包月按月付费购买资源，按配置计费按实际使用的时长（精确至秒）进行计费。关于两种计费方式的区别，请查阅[计费规则][2]；   
 4. 地域与可用区选择：在此步骤仍可以选择Pod对应的地域及可用区，请注意“不同地域资源内网不互通，创建之后不可更改”，如果所选地域限额已满，可以通过提交工单提升限额；  
 ![](https://github.com/jdcloudcom/cn/blob/edit/image/Native-Container/podregion.png)  
 5. 选择规格  
	* 京东云原生容器Pod的配置支持用户自定义选择：提供通用型、计算优化型、内存优化型、高频计算型四种类型，用户可以根据不同业务场景选择实例规格及相应配置，详细请查阅[实例配置推荐][3]；  
![](https://github.com/jdcloudcom/cn/blob/edit/image/Native-Container/Podtype.png) 
 6. 选择网络
 
	* 选择“私有网络”及“子网”，选择子网后，可以判断该子网下，还有可以创建的云主机数量，如果暂时没有子网，可以通过快速入口新建子网，并在“云主机网络”进行选择，详细请查阅[私有网络][4]和[子网][5]。  
	* 内网IP：有两种模式自动分配和自定义。默认为自动分配，将由系统为容器自动分配内网IP，且不可修改；可选择自定义，需要输入内网IP，在您子网CIDR指定内网IP范围内的IP地址，若选择自定义内网IP，暂不支持批量创建Pod。  
	*  选择对应的已创建的安全组，安全组为必选项，安全组也可以通过快速入口创建，详细请查阅[创建安全组][6]，完成创建后，重新打开Pod创建页面，在下拉列表中选择最新创建的。  
	![](https://github.com/jdcloudcom/cn/blob/edit/image/Native-Container/PodVPC.png)   
	
 7. 带宽  
 
	* 京东云提供的弹性公网IP带宽类型为按固定带宽计费及按使用流量计费，按固定带宽计费按购买时设置的带宽上限值计费，而与您实例当前实时访问公网带宽无关，按使用流量计费则根据您实时访问公网的实际流量计费。详情参考弹性公网IP[计费规则][7]。  
	* 带宽范围为：1Mbps ~ 200Mbps；  
	*  在创建Pod过程中可以暂不购买弹性公网IP，完成Pod创建后，再进行绑定。  
	*  弹性公网IP带宽费用与实例费用独立。具体价格信息请查阅[弹性公网IP价格][8]。  
![](https://github.com/jdcloudcom/cn/blob/edit/image/Native-Container/Podelasticip.png)   

 8. 存储：  
 京东云提供云硬盘作为Pod的存储，云硬盘是采用一盘多备的分布式存储方式，数据可靠性高  
 
	* 选择新建云盘、使用已有云硬盘或使用快照创建Pod存储；  
	* 云硬盘类型：提供通用型SSD盘、性能型SSD盘、容量型HDD云盘；详见[云硬盘](https://docs.jdcloud.com/cn/cloud-disk-service/product-overview)  
	* 选择按配置计费时，可设置云硬盘是否随Pod自动删除；  
	* 支持xfs和ext4两种文件系统格式；创建Pod时系统将根据已选择的文件系统格式对云硬盘进行初始化；选择新建云盘或使用快照时，将根据已选择的文件系统格式对新建云盘进行强制初始化；选择已有云盘时，请按需选择是否对云硬盘进行强制格式化；  
	* 单台Pod最多支持挂载七块云硬盘作为存储；且只支持在创建Pod时挂载云硬盘。        
	* 云硬盘费用与实例独立，具体价格信息请查阅[云硬盘价格][9]。    
       ![](https://github.com/jdcloudcom/cn/blob/edit/image/Native-Container/Podvolume.png)    
       
9. 定义容器  

	* 单台Pod中可添加多个容器，您可以为每个容器定义具体的参数配置，详情如下：  
	* 选择镜像，您可以选择京东云镜像或第三方镜像  
		* 京东云镜像：**推荐使用该方式**；镜像保存在京东云镜像仓库中，与Pod服务无缝集成，实现高速镜像下载；选择当前地域已添加的仓库和镜像；如果当前地域未创建任何仓库，可点击新建注册表按钮跳转到注册表创建页，详情参考[镜像仓库帮助中心][10]；  
		![](https://github.com/jdcloudcom/cn/blob/edit/image/Native-Container/podjcr.png)  
		* 第三方镜像：默认为docker.io，**选择docker.io将基于Docker Hub提供的官方镜像**创建容器；选择仓库认证信息后将基于对应的镜像仓库提供的公有或私有镜像创建容器。未添加任何仓库认证信息时，京东云将默认使用Docker Hub获取容器镜像；如需使用第三方私有镜像仓库，您需要先将仓库认证信息添加到京东云，选择添加第三方镜像仓库认证信息到京东云。**注意事项**:在Docker Hub用户创建的镜像，无论公有镜像或者私有镜像，都需要添加第三方仓库认证才能创建成功，仓库域名建议该地址：https://index.docker.io 。    
		![](https://github.com/jdcloudcom/cn/blob/edit/image/Native-Container/poddockehub.jpg)  

	* 容器名称：设置容器名称；一个Pod中容器名称唯一且不可修改；不可为空，且长度不超过63字符，以字母数字开始和结尾，中间可使用小写字母、数字或“-”；    
	* 资源限制：设置容器被分配的CPU、内存资源上限；资源上限可为空或不超过已选择的规格类型；  
	* 资源需求：设置容器被分配的CPU、内存资源下限；CPU资源下限默认为100m，内存资源下限默认为64Mi；指定容器的资源需求不超过对应的资源限制；已定义的容器资源限制之和不超过已选择的规格类型；  
	* 系统盘：提供通用型SSD盘、性能型SSD盘、容量型HDD云盘，容量范围为10-100G；系统盘文件系统格式支持xfs或ext4。目前系统盘必须跟随容器删除。     
	* 存储：选择已经创建的存储，设置挂载点。将存储挂载到指定的目录下，挂载目录必须是绝对路径且不可重复，以/开始；支持读写、只读两种模式。  
	* 运行的命令：输入启动容器时运行的第一条Entrypoint指令，将覆盖镜像中设置的Entrypoint指令；   
	* 运行的参数：输入启动容器时运行的第一条CMD指令，将覆盖镜像中设置的CMD指令；如已在运行的命令中设置了Entrypoint指令，该条指令将会附加到Entrypoint指令的参数中被执行；   
	* 环境变量：设置容器运行时的环境变量。可以为每一个容器设置多组环境变量，每一组环境变量的键和值必须一一对应；容器启动后可使用env命令查看容器的环境变量；点击+按钮，添加一组环境变量；点击“删除”按钮删除一组环境变量;  
	* 工作目录：设置容器的工作目录。容器的工作目录必须是绝对路径，以/开始且不能包含“:”、“.”字符；如不设置，默认使用根目录“/”作为容器的工作目录
	* 启动项：点击按钮开启或关闭TTY；默认情况下TTY为关闭状态；开启后将为容器分配一个伪终端，打印容器的Stdin、Stdout、Stderror信息；    
	* 探针：勾选存活探针或就绪探针复选框，为容器配置存活或就绪探测；  
		* 延迟触发：设置容器启动后，探针被初始化的延迟时间；未设置时默认延迟10秒；  
		* 时间间隔：设置探测结果设置为超时的等待时间；未设置时默认等待10秒；  
		* 失败阈值：设置探测结果被诊断为失败前，探测行为被重复执行的最少次数；未设置时默认执行3次；  
		* 成功阈值：设置探测结果被诊断为成功前，探测行为被重复执行的最少次数；未设置时默认执行1次；  
		* Pod支持三种探针类型：Execaction、HttpGet、TcpSocket；  
		* Execaction探测：容器文件系统的根目录（'/'）下以Exec的方式执行探测命令；  
		* HttpGet：以HTTP Get请求的方式执行容器探测命令；  
		* TcpSocket：指定一个TCP 端口执行指定的TCPSocket探测命令；  
		
 11. 高级设置  
 
	 * 重启策略：设置Pod中已定义容器的重启策略；可选择总是、从不、失败时重启三种策略；  
	 * 主机名：设置Pod的主机名；如不设置,则使用PodID作为主机名；  
	 * 域名和IP映射：非必填项，在容器hosts文件中增加一组域名和IP映射；点击+按钮，增加一组域名和IP映射；点击删除按钮，删除一组域名和IP映射。最多可添加十组域名和IP映射；  
	 * DNS配置：非必填项，设置Pod /etc/resolv.conf文件中的DNS配置；点击+按钮，增加一组DNS配置；点击删除按钮，删除一组DNS配置。最多可添加六组DNS配置；  
	 
 12. 基本信息  
 
	 * 名称：为必填项，名称不可重复、不可为空且不能超过253字符，必须以小写字母数字开始和结尾，中间可包含小写字母、数字、“-”或“.”；  
	 * 描述：为非必填项，您可按需设置，容器描述最长不能超过256字符；  
	 
 13. 确认Pod数量及购买时长  
 
	 * 购买数量受限该地域您容器、云硬盘、公网IP限额以及所选子网剩余IP数量，若限额不够，可通过提交工单提升限额；  
	 * 若购买包年包月实例，则需要设置购买时长，最短为1个月，最长为3年。若需要更长服务时长请提交工单。 
	 
  14. 完成Pod相关配置之后，点击【立即购买】完成支付后即可进入控制台>>弹性计算>>原生容器>>Pod，查看创建的Pod。  


 


  [2]: https://docs.jdcloud.com/cn/native-container/billing-rules
  [3]: https://docs.jdcloud.com/cn/native-container/recommend-instance
  [4]: https://docs.jdcloud.com/cn/virtual-private-cloud/product-overview
  [5]: https://docs.jdcloud.com/cn/virtual-private-cloud/subnet-features
  [6]: https://docs.jdcloud.com/cn/native-container/security-group
  [7]: https://docs.jdcloud.com/cn/elastic-ip/product-overview
  [8]: https://docs.jdcloud.com/cn/elastic-ip/billing-rules
  [9]: https://docs.jdcloud.com/cn/cloud-disk-service/price-overview
  [10]: https://docs.jdcloud.com/cn/container-registry/create-registry
