# 持续交付

**前言**

在DevOps平台，可以一站式完成应用的生命周期管控，包括编译构建、部署、启停、重启和应用下线等，实现对应用的全流程管理。
- **编译构建**

DevOps编译构建为开发者提供基于容器的自动化持续集成服务。支持多语言构建环境，自动/手动触发任务，查看构建结果及日志。编译构建实现容器化隔离，支持自定义构建容器，为产品的持续集成提供上游基础服务，提升研发效率。
- **线上发布**

支持京东云主机、物理机及其他厂商云主机的部署功能。
- **日志服务**

日志服务提供了数据采集、展示、检索的一站式服务，灵活的检索功能提供秒级查询能力，支持关键字高亮检索，查看上下文等功能。

**术语定义**

**现场日志**

服务器上目前存在的日志文件，称为现场日志

**历史日志**

通过日志订阅，日志通过采集、清洗、存储在存储库中的日志，称为历史日志

**产品功能**

**编译构建**

1. 选择菜单“持续交付—编译构建”，点击“新增构建”按钮，设置编译构建基本信息。 

- Git代码地址：提供源码地址，命名规范如下：
group名需>两个字符 模块名&分支名命名规范小写字母+数字+下划线+中划线（目前大写字母会自动转为小写字母），不支持/等特殊字符
- 代码分支：选中需要编译的代码分支
- 模块名：根据代码地址自动生成，后续线上发布将依赖此模块名
- 构建镜像：选择编译环境，目前支持Java、golang、node、static_resource等不同语言的多个版本的编译环境
- 编译依赖：可添加编译依赖
- 构建方式：支持build.sh和makefile两种方式，提供不同语言对应的编译模板 

```
#以golang为例，需要在代码库的根路径增加编译脚本，示例build.sh如下：
#!/bin/bash
#编译脚本的原理是将编译结果放到output目录中，这个样例模版提供一个产生一个最基本golang运行程序包的编译脚本，对于特殊的需求请酌情考虑
#
#1、该脚本支持参数化，参数将传入build_package函数（内容为最终执行的编译命令）
#   ，用$1,$2....表示，第1,2...个参数
#2、部署需要启动程序，所以需要提供control文件放在当前目录中，用于启动和
#   监控程序状态
#用户修改部分
readonly PACKAGE_DIR_NAME=""    #main文件相对于src文件夹所在的目录,可选项
readonly PACKAGE_BIN_NAME=""    #定义产出的运行程序名,必填项
readonly CONF_DIR_NAME=""       #定义配置文件目录,此路径为相对路径,可选项
#最终的抽包路径为$OUTPUT
if [[ "${PACKAGE_BIN_NAME}" == "" ]];then
    echo "Please set "PACKAGE_BIN_NAME" value"
    exit 1
fi
function set_work_dir
{
    readonly OUTPUT=$(pwd)/output
    readonly WORKSPACE_DIR=$(pwd)
}
#清理编译构建目录操作
function clean_before_build
{
    cd ${WORKSPACE_DIR}
    rm -rf bin pkg
    rm -rf ${OUTPUT}
}
#实际的编译命令
#这个函数中可使用$1,$2...获取第1,2...个参数
function build_package()
{
    cd ${WORKSPACE_DIR}
    export GOPATH=$(pwd)
    go install ${PACKAGE_DIR_NAME} || return 1
}
#建立最终发布的目录
function build_dir
{
    mkdir -p ${OUTPUT}/bin || return 1
}
function dir_not_empty()
{
    if [[ ! -d $1 ]];then
        return 1
    fi
    if [[ $(ls $1|wc -l) -eq 0 ]];then
        return 1
    fi
    return 0
}
#拷贝编译结果到发布的目录
function copy_result
{
    cd ${WORKSPACE_DIR}
    cp -r ./bin/${PACKAGE_BIN_NAME} ${OUTPUT}/bin/${PACKAGE_BIN_NAME} || return 1
    cp -r ./control ${OUTPUT}/bin || return 1
    (dir_not_empty ${WORKSPACE_DIR}/${CONF_DIR_NAME} && mkdir -p ${OUTPUT}/${CONF_DIR_NAME};cp -rf ./${CONF_DIR_NAME}/* ${OUTPUT}/${CONF_DIR_NAME}/);return 0
}
#执行
function main()
{
    cd $(dirname $0)
    set_work_dir
    echo "At: "$(date "+%Y-%m-%d %H:%M:%S") 'Cleaning...'
    clean_before_build || exit 1
    echo "At: "$(date "+%Y-%m-%d %H:%M:%S") 'Clean completed'
    echo
    echo "At: "$(date "+%Y-%m-%d %H:%M:%S") 'Building...'
    build_package $@ || exit 1
    echo "At: "$(date "+%Y-%m-%d %H:%M:%S") 'Build completed'
    echo
    echo "At: "$(date "+%Y-%m-%d %H:%M:%S") 'Making dir...'
    build_dir || exit 1
    echo "At: "$(date "+%Y-%m-%d %H:%M:%S") 'Make completed'
    echo
    echo "At: "$(date "+%Y-%m-%d %H:%M:%S") 'Copy result to publish dir...'
    copy_result || exit 1
    echo "At: "$(date "+%Y-%m-%d %H:%M:%S") 'Copy completed'
    echo
    exit 0
}
main $@
```

- 构建参数：填写构建过程中，需要的参数
- 触发条件：手动构建，或提交代码到分支时，自动触发编译构建
- 构建类型：构建产出物，支持代码包
- 版本规则：提供版本命名规则，归档至版本库
- 缓存编译工作区：是否缓存工作区，对于多次编译构建，可加速编译过程
- 构建上传位置（多选）：为加速上线发布获取编译结果的速度，可根据云主机所在地域，选择构建包上传位置
高级选项：
- 开启LFS：应对代码库中的大文件
- webhook地址：可填写需要触发的notification
- 邮件通知：可填写邮箱地址
- 通知频率：可设置通知频率为 构建异常发送 每次构建都发送

2.保存后进入编译构建列表，点击“立即构建”，可进行编译构建操作，构建成功即可在 模块—查看版本，看到已编译构建的模块版本。

**模块管理**

在模块分页中，可支持用户创建模块、手动上传程序包至模块、版本管理。

![image](https://github.com/jdcloudcom/cn/blob/DevOps/image/DevOps/Operation-Guide12.png)


**应用部署**

1.基本设置

选中左侧服务树中某应用，选择菜单“持续交付—线上发布”，进入“上线”页。点击“基本设置”分页，设置执行账户，将应用与 所属模块 绑定（只有将二者绑定后，上线时才能选到所属模块下的编译的包版本）

2.分组配置

在“分组配置”页，点击“配置”，可对各分组设置配置文件及环境变量。

其中，配置文件可支持新增、上传、克隆。
 
![image](https://github.com/jdcloudcom/cn/blob/DevOps/image/DevOps/Operation-Guide13.png)

3.上线

在“上线”页，选择要上线的分组，并对上线并发度、超时时间进行设置，选择需要上线的包版本进行上线。在“上线动态”页可查看上线详情及进行回滚操作。

至此，基本的上线发布过程结束。

4.实例管理

可对实例维度，支持重启、启动、停止、开启或关闭流量、缩容(弹性部署)批量操作

![image](https://github.com/jdcloudcom/cn/blob/DevOps/image/DevOps/Operation-Guide14.png)
 
在代码根目录下 bin/增加control 脚本，用来启动、停止、服务健康检查 

control示例如下：

```
#!/bin/bash
cd "$(dirname $0)"/.. || exit 1
PROC_NAME=confcenter # 进程名 一般就是二进制的名字java类程序一般就是java
START_COMMAND='bin/confcenter' #在output目录下启动你程序的命令
PROC_PORT=8055 # 程序占用的端口，建议写，程序不占用端口的话只用ps来判断进程是否启动，机器上有同名程序是可能有问题
WAIT_TIME=60 # 执行START_COMMAND后到程序能完全启动listen端口需要花的时间
  
PROC_NAME=${PROC_NAME::15}
if [ -f default_env.sh ];then
    source default_env.sh
fi
help(){
    echo "${0} <start|stop|restart|status>"
    exit 1
}
  
checkhealth(){
    if [[ -n "$PROC_PORT" ]] ; then
        PORT_PROC=$(/usr/sbin/ss -nltp "( sport = :$PROC_PORT )" |sed 1d |awk '{print $NF}' |grep -oP '".*"' |sed "s/\"//g" |uniq)
        if [ X"$PORT_PROC" = X"$PROC_NAME" ] ; then
                echo "running"
            return 0
        fi
        echo "not running"
        return 1
   else
       ps -eo comm,pid |grep -P  "^$PROC_NAME"
       if [ "$?" = 0 ] ; then
       echo "running"
           return 0
       fi
       echo "not running"
       return 1
   fi
}
  
start(){
    checkhealth
    if [ $? = 0 ]; then
        echo "[WARN] $PROC_NAME is aleady running!"
        return 0
    fi
    mkdir -p log
  
    nohup $START_COMMAND  </dev/null &>> /dev/termination-log  &
  
  
    for i in $(seq $WAIT_TIME) ; do
        sleep 1
        checkhealth
        if [ $? = 0 ]; then
            echo "Start $PROC_NAME success"
            return 0
        fi
    done
    echo "[ERROR] Start $PROC_NAME failed"
    return 1
}
  
stop(){
    if [[ -n "$PROC_PORT"  ]] ; then
        PROC_ID=$(  /usr/sbin/ss -nltp "( sport = :$PROC_PORT )" |sed 1d  | awk '{print $NF}' |  grep -oP ',.*,' | grep -oP "d+" |  uniq )
    else
        PROC_ID=$(ps -eo comm,pid  | grep "^$PROC_NAME" |awk '{print $2}')
    fi
  
    if [[ -z "$PROC_ID" ]] ; then
        echo "[WARN] $PROC_NAME is aleady exit, skip stop"
        return 0
    fi
  
    checkhealth
    if [ "$?" != "0" ] ; then
        echo "[WARN] $PROC_NAME is aleady exit, skip stop"
        return 0
    fi
    kill $PROC_ID
    for i in $(seq $WAIT_TIME) ; do
        sleep 1
        checkhealth
        if [ "$?" != "0" ] ; then
            echo "Stop $PROC_NAME success"
            return 0
        fi
    done
  
    kill -9 $PROC_ID
    sleep 1
    checkhealth
    if [ "$?" != "0" ] ; then
        echo "Stop $PROC_NAME success"
        return 0
    fi
  
    echo "[ERROR] Stop $PROC_NAME failed"
    return 1
}
  
case "${1}" in
    start)
        start
        ;;
    stop)
        stop
        ;;
    status|health|checkhealth)
        checkhealth
        ;;
    restart)
        stop && start
        ;;
    *)
        help
        ;;
esac
```
5.日志服务

5.1 现场日志：选中要查看日志的应用，选择菜单“持续交付”-“线上发布”，在“日志服务-现场日志”页，即可查看各实例对应的日志，日志查看支持关键字高亮，与反向查询，整词匹配等，点击某行日志，还可查看上下文日志。
 
 ![image](https://github.com/jdcloudcom/cn/blob/DevOps/image/DevOps/Operation-Guide15.png)
 
5.2 日志订阅与历史日志：选中要查看日志的应用，选择菜单“持续交付”-“线上发布”，在“日志服务-日志订阅”页，点击“新增订阅”设置日志路径并保存，即可在下次上线动作后从历史日志页查看订阅的分组及实例的日志。
 
 ![image](https://github.com/jdcloudcom/cn/blob/DevOps/image/DevOps/Operation-Guide16.png)

**编排上线**

可支持跨应用的部署发布操作，并提供穿并行、失败阈值等设置

1.新建视图

填写视图名称、超时时间等配置

2.编写视图内容

- 层之间是串行的
- 每层内的 job 可以并行，如层的并发度设置为6，则最多有6个 job 同时执行
- job 内的并发度按 job 支持的方式设置，与页面操作行为一致。如包部署 job，其 concurrency 字段取值及含义为：0-串行，30-30%，70-70%，100-并行；而镜像部署 job，concurrency 字段取值：0-并行，1-串行…
- 层内执行失败的 job 数达到配置的 max_fail（失败阈值）时，标记该层以及整个视图失败
可参看以下示例，

```
[
    // 层级1
    {
        "concurrency": 2, // 分组1内并发度（注意：0表示全并发，1表示串行，n 表示最多同时有 n 个 job 同时执行）
        "timeout": 1200,  // 分组1超时时间（s）
        "pause": 1,       // 本层执行完成后，视图会进入“暂停”状态，在执行记录中点击“继续执行”后方可执行后续层级
        "max_fail": 3,    // 本层失败 job 数达到3时才标记本层（以及整个视图）为失败，这里如果给0则忽略所有失败 job
        // 分组1内的部署 job，每个 job 对应一个 APP 的部署
        "jobs": [
            // job1
            {
                "app_name": "yangxiaojia-test-app1",  // job1 APP 名
                "concurrency": "0",                   // job1 实例并发度（包部署：0-串行，30-30%，70-70%，100-并行 || 镜像部署：0-并行，1-串行，2-同时最多2个实例并行…）
                "instance_timeout": 300,              // job1 执行超时时间（s）
                // job1 部署目标
                "target": [
                    "group-hb",                      // 目标分组（如果是包部署也可以是实例，如0.group-hb）
                    "group-sh"
                ],
                "type": "1",                          // job1 上线类型：1-包部署，2-镜像部署，4-弹性部署，5-弹性扩容
                "version": "4f40681d-20170622095458"  // job1 上线包版本
            }
            // 其他job
            ...
        ]
    }
    // 其他层级
    ...
]
```

3.保存视图后，可支持编辑、执行、查看执行历史、删除操作
