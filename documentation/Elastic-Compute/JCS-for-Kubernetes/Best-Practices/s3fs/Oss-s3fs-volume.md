# 在Kubernetes集群中挂载对象存储Bucket
S3fs是基于FUSE的文件系统，允许Linux 挂载Bucket在本地文件系统，S3fs能够保持对象原来的格式。使用S3fs可以把Bucket当成一个文件夹挂载到Linux系统内部，当成一个系统文件夹使用。更多详情参考[使用S3fs在Linux实例上挂载Bucket](https://docs.jdcloud.com/cn/object-storage-service/s3fs)。本文将使用Daemonset方式，将对象存储Bucket挂载到Kubernetes集群工作节点，并提供应用示例说明如何在两个Pod中共享指定的Bucket存储。

## 一、使用DaemonSet方式部署挂载S3的BUCKET

1. 创建一个secret保存访问对象存储Bucket的秘钥文件，文件名称保存为s3fs-secret.yaml，执行如下命令创建secret对象；

    ```
    wget https://kubernetes.s3.cn-north-1.jdcloud-oss.com/s3fs/s3fs-secret.yaml                #请先修改s3fs-secret.yaml文件中的Access_Key_ID、Access_Key_Secret，再执行secret创建操作

    kubectl create -f s3fs-secret.yaml
    ```
    
    Yaml文件内容如下：

    ```
    
    apiVersion: v1
    kind: Secret
    metadata:
      name: s3fs-secret
      namespace: default
    type: Opaque
    stringData:
      passwd-s3fs: |-
        Access_Key_ID:Access_Key_Secret     #Access_Key_ID、Access_Key_Secret请分别使用具有指定对象存储Bucket访问权限的Access Key内容替换；
    ```

2. 使用Daemonset方式创建具有s3fs文件系统的Pod，在允许使用对象存储Bucket的工作节点上部署Daemonset，本例将Daemonset部署到集群的全部工作节点上，：

  * 执行如下命令创建Daemonset对象:

    ```
    wget https://kubernetes.s3.cn-north-1.jdcloud-oss.com/s3fs/s3fs-ds.yaml                #请先修改s3fs-ds.yaml文件中对象存储Bucket相关的内容，再执行Daemonset创建操作

    kubectl create -f s3fs-ds.yaml
    ``` 
  **注**：本例中Daemonset使用的京东云提供的s3fs镜像，您也可以参考[构建s3fs自定义镜像](https://docs.jdcloud.com/cn/jcs-for-kubernetes/s3fs-custom-image)帮助文档说明构建自定义镜像
  * Yaml文件内容如下：
    ```
    
    apiVersion: extensions/v1beta1
    kind: DaemonSet
    metadata:
      name: s3fs-mount
    spec:
      selector:
        matchLabels:
          name: s3fs-mount
      template:
        metadata:
          labels:
            name: s3fs-mount
        spec:
          containers:
          - name: s3fs-mount
            image: jdcloud-cn-north-1.jcr.service.jdcloud.com/jdcloud/oss-volumes:latest       #京东云提供的s3fs镜像，您也可以使用自定义的s3fs镜像替换
            securityContext:
              privileged: true        #不可修改，否则对象存储Bucket将无法挂载
            env:
            - name: S3_BUCKET
              value: storage-1026     #value值请使用对象存储Bucket名称替换  
            - name: S3_URL
              value: https://s3.cn-north-1.jdcloud-oss.com        #value值请使用对象存储Bucket的外网Endpoint替换
            - name: MNT_POINT
              value: /data    #value值可不修改；或使用对象存储Bucket在容器中的挂载目录替换；如需修改value值请同时修改名称为mntdatas3fs的volume的mountPath值，保证共享目录名称一致；
            volumeMounts:
            - name: mntdatas3fs
              mountPath: /data:shared       #mountPath值可不修改；如ENV MNT_POINT的value值被修改，则mountPath值必须同时被修改，以保证共享目录名称一致
            - name: mysecret
              mountPath: "/mysecret"
          volumes:
          - name: mntdatas3fs
            hostPath:
              path: /mnt/data-s3fs
          - name: mysecret
            secret:
              secretName: s3fs-secret
              items:
              - key: passwd-s3fs
                path: passwd-s3fs        #path值不可修改，因s3fs指令会检查文件/mysecret/passwd-s3fs的权限（0600）
                mode: 0600        #mode值不可修改，因s3fs指令会检查文件/mysecret/passwd-s3fs的权限（0600）

    ```

* **注**：

  * 如需在Pod中使用指定UID、GID访问s3fs的挂载目录，请在SecurityContext中增加runAsUser或runAsGroup定义。
  * 如需在s3fs-mount container的CMD exec指令中添加其他s3fs自定义参数，可通过env的OPTION添加；例如授权所有用户访问MNT_POINT，请新增一组env定义，name设置为OPTION，value值定义为allow_other（ENV OPTION allow_other）：

    ```
    - name: OPTION
      value: allow_other
    ```



* 执行如下命令，确定所有Daemonset处于running状态：
    ```
    
    kubectl get daemonset s3fs-mount

    NAME         DESIRED   CURRENT   READY   UP-TO-DATE   AVAILABLE   NODE SELECTOR   AGE
    s3fs-mount   3         3         3       3            3           <none>          73m
    ```

4. 所有Daemonset均处于运行状态后，即可参考如下示例在集群中部署共享对象存储Bucket的应用。

## 二、示例应用

示例应用将创建两个Pod，第一个Pod在对象存储中创建一个名称为SUCCESS的文件，第2个Pod将在名称为SUCCESS的文件中写入内容“helloworld”。

1. 部署第一个Pod在对象存储中创建一个名称为SUCCESS的文件，将Yaml文件名称保存为test-s3fs-pod1.yaml，执行如下命令创建Pod对象：

    ```
    wget https://kubernetes.s3.cn-north-1.jdcloud-oss.com/s3fs/test-s3fs-pod1.yaml

    kubectl create -f test-s3fs-pod1.yaml
    ```
    
    Yaml文件内容如下：
    ```
    
    kind: Pod
    apiVersion: v1
    metadata:
      name: test-s3fs-pod-1
    spec:
      containers:
      - name: test-s3fs-pod-1
        image: busybox:latest
        command:
        - "/bin/sh"
        args:
        - "-c"
        - "touch /mnt/SUCCESS && sleep 60000 || exit 1"
        volumeMounts:
        - name: mntdatas3fs
          mountPath: "/mnt"
      restartPolicy: "Never"
      volumes:
      - name: mntdatas3fs
        hostPath:
          path: /mnt/data-s3fs
      ```
      执行如下命令，确定pod处于running状态：

      ```
      
      kubectl get pod test-s3fs-pod-1

      NAME              READY   STATUS    RESTARTS   AGE
      test-s3fs-pod-1   1/1     Running   0          9s
      ```
      执行完成后，在上一步部署Daemonset时指定的对象存储 [Bucket详情页] - [Object管理Tab页]下即可看到新创建的名称为SUCCESS的空文件；
   
2. 部署第二个Pod在上一步中创建的SUCESS文件中写入字符“helloworld”，将Yaml文件名称保存为test-s3fs-pod2.yaml，执行如下命令创建Pod对象：

    ```
    wget https://kubernetes.s3.cn-north-1.jdcloud-oss.com/s3fs/test-s3fs-pod2.yaml

    kubectl create -f test-s3fs-pod1.yaml
    ```
    
    Yaml文件内容如下：
    ```
    
    kind: Pod
    apiVersion: v1
    metadata:
      name: test-s3fs-pod-2
    spec:
      containers:
      - name: test-s3fs-pod-2
        image: busybox:latest
        command:
        - "/bin/sh"
        args:
        - "-c"
        - "echo helloworld > /mnt/SUCCESS && sleep 60000 || exit 1"
        volumeMounts:
        - name: mntdatas3fs
          mountPath: "/mnt"
      restartPolicy: "Never"
      volumes:
      - name: mntdatas3fs
        hostPath:
          path: /mnt/data-s3fs
      ```
    执行如下命令，确定pod处于running状态：

    ```
    
    kubectl get pod test-s3fs-pod-2

    NAME              READY   STATUS    RESTARTS   AGE
    test-s3fs-pod-2   1/1     Running   0          11s
    ```
    执行完成后，在上一步创建的名称为SUCCESS的文件中即可看到输出内容“helloworld”。
