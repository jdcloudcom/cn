# 构建规范

构建规范是构建命令及相关设置的编译脚本，采用 YAML 格式。您可以把构建规范脚本放在源代码中，也可以在创建项目时定义。如果在源代码中包含构建规范，构建规范文件必须名为 build.yml 且放置在源目录的根目录中。

构建规范语法如下：

```
envs:
name: TEST_ENV
value: test
cmds:
name: who
cmd: id
name: see
cmd: pwd
name: build
cmd: ./build.sh
out_dir: output
```

