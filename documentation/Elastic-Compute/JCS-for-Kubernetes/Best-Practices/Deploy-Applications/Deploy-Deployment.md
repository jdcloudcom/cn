
# 部署Deployment

下面是一个 Deployment 示例，它创建了一个 ReplicaSet 来启动3个 nginx pod。

下载示例文件并执行命令：

$ kubectl create -f https://kubernetes.io/docs/user-guide/nginx-deployment.yaml --record


将kubectl的 --record 的 flag 设置为 true可以在 annotation 中记录当前命令创建或者升级了该资源。这在未来会很有用，例如，查看在每个 Deployment revision 中执行了哪些命令。

然后立即执行 get 将获得如下结果：

$ kubectl get deployments


输出结果表明我们希望的repalica数是3（根据deployment中的.spec.replicas配置）当前replica数（ .status.replicas）是0, 最新的replica数（.status.updatedReplicas）是0，可用的replica数（.status.availableReplicas）是0。

过几秒后再执行get命令，将获得如下输出：

$ kubectl get deployments



我们可以看到Deployment已经创建了3个 replica，所有的 replica 都已经是最新的了（包含最新的pod template），可用的（根据Deployment中的.spec.minReadySeconds声明，处于已就绪状态的pod的最少个数）。执行kubectl get rs和kubectl get pods会显示Replica Set（RS）和Pod已创建。

$ kubectl get rs


您可能会注意到 ReplicaSet 的名字总是<Deployment的名字>-<pod template的hash值>。

$ kubectl get pods --show-labels


刚创建的Replica Set将保证总是有3个 nginx 的 pod 存在。

注意： 您必须在 Deployment 中的 selector 指定正确的 pod template label（在该示例中是 app = nginx），不要跟其他的 controller 的 selector 中指定的 pod template label 搞混了（包括 Deployment、Replica Set、Replication Controller 等）。Kubernetes 本身并不会阻止您任意指定 pod template label ，但是如果您真的这么做了，这些 controller 之间会相互冲突，并可能导致不正确的行为。

