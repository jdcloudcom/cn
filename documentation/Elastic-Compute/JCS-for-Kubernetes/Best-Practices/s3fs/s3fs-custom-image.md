# 构建s3fs自定义镜像
使用S3fs可以把Bucket当成一个文件夹挂载到Linux系统内部，当成一个系统文件夹使用。更多详情参考[使用S3fs在Linux实例上挂载Bucket](https://docs.jdcloud.com/cn/object-storage-service/s3fs)。在Kubernetes集群中使用s3fs需要先构建s3fs的镜像，本文提供了s3fs镜像的的Dockerfile，您可以在Dockerfile中添加自定义参数，构建自定义s3fs镜像。

## 一、s3fs Dockerfile

1. 将s3f3 Dockerfile下载到本地

`
wget https://kubernetes.s3.cn-north-1.jdcloud-oss.com/s3fs/s3fs-dockerfile.yml
`
    
2. Dockerfile内容说明如下

```    
FROM ubuntu:16.04

# 定义Dockerfile中CMD exec指令使用的ENV环境变量
ENV S3_BUCKET ''
ENV MNT_POINT /data
ENV S3_URL ''
ENV S3_UID 0
ENV S3_GID 0
ENV OPTION ''

RUN DEBIAN_FRONTEND=noninteractive apt-get -y update --fix-missing && \
apt-get install -y automake autotools-dev g++ git libcurl4-gnutls-dev wget \
libfuse-dev libssl-dev libxml2-dev make pkg-config && \
git clone https://github.com/s3fs-fuse/s3fs-fuse.git /tmp/s3fs-fuse && \
cd /tmp/s3fs-fuse && ./autogen.sh && ./configure && make && make install && \
ldconfig && /usr/local/bin/s3fs --version && \
mkdir -p "$MNT_POINT" && \
DEBIAN_FRONTEND=noninteractive apt-get purge -y wget automake autotools-dev g++ git make && \
apt-get -y autoremove --purge && apt-get clean && \
rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

CMD exec /usr/local/bin/s3fs $S3_BUCKET $MNT_POINT -f -o passwd_file=/mysecret/passwd-s3fs -o url=$S3_URL -o uid=$S3_UID -o gid=$S3_GID $OPTION
    
```

3. 构建docker镜像；

    ```
    ##使用京东云提供的dockerfile构建##
    docker build --network host -t s3fs:latest https://kubernetes.s3.cn-north-1.jdcloud-oss.com/s3fs/s3fs-dockerfile.yml
    
    ##使用自定义dockerfile构建,请根据dockerfile文件的实际情况替换$PATH##
    docker build --network host -t s3fs:latest $PATH

    ##镜像构建成功后，请使用如下命令验证新构建的docker镜像
    docker images

    REPOSITORY                                            TAG                  IMAGE ID            CREATED             SIZE
    s3fs                                                  latest               9581af047109        13 seconds ago      307 MB    
    ```

4. 将docker镜像s3fs保存到[京东云镜像仓库](https://docs.jdcloud.com/cn/container-registry/create-image)或其他可以通过公网访问的镜像仓库。

5. 使用自定义s3fs镜像挂载对象存储，详情参考[在Kubernetes集群中挂载对象存储Bucket](https://docs.jdcloud.com/cn/jcs-for-kubernetes/Oss-s3fs-volume)。


