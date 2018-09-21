
# 访问Dashboard

京东云Kubernetes集群服务已预置Dashboard插件。

一、检查dashboard插件

1、查看分配的NodePort

2、检查controller


二、访问dashboard

1、通过 API server 访问 dashboard（https 6443端口）；

使用这种方式访问dashboard需要先基于集群的config文件生成并安装P12安全证书，具体操作步骤如下：

1）获取客户端证书，进行base64转码后保存到kubecfg.crt

grep 'client-certificate-data' ~/.kube/config | head -n 1 | awk '{print $2}' | base64 -d > kubecfg.crt

2）获取客户端公钥，进行base64转码后保存到kubecfg.key
grep 'client-key-data' ~/.kube/config | head -n 1 | awk '{print $2}' | base64 -d > kubecfg.key

3）提取kubecfg.crt和kubecfg.key文件内容，生成P12安全证书，并保存到kubecfg.p12文件
openssl pkcs12 -export -clcerts -inkey kubecfg.key -in kubecfg.crt -out kubecfg.p12 -name "kubernetes-client"
     说明：生成安全证书时，需要设置提取密码，您可以设置自定义密码或设置密码为空；

4）将安全证书下载到本地，以Windows7操作系统为例，证书的安装步骤如下：

双击证书文件，弹出证书导入向导对话框；

确定要导入的证书文件


输入生成安全证书时设置的自定义密码


设置证书保存位置


完成证书导入



5）在浏览器中输入https://****/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/，其中****请使用k8s集群详情页查询到的服务端点替换，即可访问dashboard；

2、通过LoadBalance 服务访问dashboard；

 1）通过LoadBalance服务访问dashboard，您需要现在集群中创建一个LoadBalance类型的服务，yaml文件如下所示：

kind: Service
apiVersion: v1
metadata:
  name: dashboard-lb
  labels:
    k8s-app: kubernetes-dashboard
spec:
  ports:
    - protocol: TCP
      port: 8443
      targetPort: 8443
      nodePort: 30063
  type: LoadBalancer
  selector:
     k8s-app: kubernetes-dashboard
2）执行如下命令，在kube-system命名空间中创建服务：

kubectl create -f dashboard-lb.yaml --namespace=kube-system
3）在kube-system命名空间中查询新创建的服务的公网IP

kubectl get services -n kube-system
4）在浏览器中输入https://****:port/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/，其中****使用LoadBalance服务关联的公网IP替换，port使用service spec中的port替换，本示例为8443，即可访问dashboard。

三、dashboard身份认证

在dashboad中查看集群的资源信息，需要通过用户身份认证：


以获取admin服务账户的令牌为例，具体操作方法如下：

1、查看kube-system命名空间中的所有secret：

kubectl get secret -n kube-system

2、查看admin服务账户对应的secret详情，****请使用具体的secret名称替换：

kubectl describe secret **** -n kube-system

3、将Data 项中对应的token信息拷贝到dashboard窗口令牌输入框中，点击确定即可；

4、您也可以将token信息添加到config文件user项目中，之后，您即可选择Kubeconfig方式进行身份认证。