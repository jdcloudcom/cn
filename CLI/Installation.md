
# 安装 #

目前支持在Linux、macOS、Windows系统上安装CLI。

## 安装须知 ##

京东云CLI基于Python语言和京东云Python SDK开发，使用CLI前请安装Python 2.7.*版本。请访问官网下载并安装Python2.7.*版本。

京东云Python SDK不用手动安装，Python包管理工具会自动下载并安装对应版本的依赖包。如果您已经安装了京东云Python SDK，并且因为CLI版本与之不对应而不能正常工作，请参考“CLI使用说明”中的版本对应表，安装对应版本或删除旧的Python SDK并重新安装CLI。

  

##1. Python2.7安装 ##

官网下载安装：https://www.python.org/downloads

操作系统包管理工具安装

CentOS  


	yum install python


Ubuntu


	apt-get install python2.7


macOS


	brew install python@2


##2. pip安装 ##

官网安装请参考：https://pip.pypa.io/

具体命令为 

	curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
	python get-pip.py


使用Linux各发行版包管理工具安装pip，请参考安装方法：

https://packaging.python.org/guides/installing-using-linux-tools/#installing-pip-setuptools-wheel-with-linux-package-managers



##3. CLI安装 ##

### Linux & macOS安装 ###

- 方式一：pip安装（推荐）


	pip install jdcloud_cli


- 方式二：源码安装

下载地址：https://github.com/jdcloud-api/jdcloud-cli

解压缩后在项目目录中执行：


	python setup.py install


- 打开Bash自动完成

执行以下命令，可以开启CLI的自动完成功能。


	echo 'eval "$(register-python-argcomplete jdc)"' >> .bashrc
	echo 'export COLUMNS=100' >> .bashrc
	source ~/.bashrc


自动完成功能可以极大提高CLI的使用效率，建议安装。配置后，输入两次tab键就可以弹出相应命令的提示。效果如下所示。 

	Bash-3.2$ jdc configure [tab][tab]
	--help    --version   -v       delete        show-current
	--output  -h          add      show-all      use


### Windows安装 ###

京东云CLI在Windows上运行依赖Git 2.9.0以上版本，建议使用最新版本。下载地址为：https://git-scm.com/download/win

请注意：安装时模拟终端选项要选择“Use MinTTY (the default terminal of MSYS2)”。

                                               


-方式一： pip安装


	pip install jdcloud_cli


-方式二： 源码安装（不依赖pip）


	python setup.py install


- 打开Bash自动完成

安装后在git bash中执行以下脚本：

	curl https://raw.githubusercontent.com/jdcloud-api/jdcloud-cli/master/jdcloud_cli/resources/jdc.rc > ~/jdc.rc
	echo 'source ~/jdc.rc' >> ~/.bashrc
	echo 'export PYTHONIOENCODING="UTF-8"' >> ~/.bashrc
	source ~/.bashrc


## 卸载CLI ##


	pip uninstall jdcloud_cli


## 升级CLI ##

使用以下命令可以升级到最新版本。

	pip install --upgrade jdcloud_cli
