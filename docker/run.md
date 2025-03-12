# Docker使用

1. docker ps: 查看本地创建的容器
1. docker image ls: 查看本地存储的镜像
1. docker run -i -t --name <container_name>  -v /path:/workspace <image> /bin/bash
    - -i -t: 交互式启动，自动打开命令行窗口
    - --name: 为容器命名
    - -v: 在运行时将本地目录挂载到workspace目录下
    - <image>: 镜像名
1. docker start <container_name>: 启动容器
1. docker commit -m="has update" -a="runoob" e218edb10161 <image>：将这个容器对应的镜像存储为新的镜像