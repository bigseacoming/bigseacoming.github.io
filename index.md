# dockerfile
| 关键字| 描述 | example    |
| :--- | :---| :--- |
| FROM | 从一个基础镜像构建我们的镜像 | FROM ubuntu:16.04 |
| MINTAINER | 镜像拥有者信息 | bigseacoming “bigseacoming@gmail.com” |
| RUN | 运行一个指令 | As-is.  /bin/sh -c your command |
| EXPOSE | 公开端口 | 80 docker run -P 随机映射端口 |
| EXEC | 运行一个指令 | your command 不同于RUN是不添加/bin/sh -c 前缀 |
| ENV | 设置一个环境变量,适用于RUN命令 | ENV JAVA_HOME /ust/javahome |
| CMD | docker启动未指定指令时的默认指令 | CMD ["java","-jar","application.jar"] |
| ENTRYPOINT | docker启动时的指令，docker run 指定了指令，指定的指令会被当成传入的参数 | ENTRYPOINT /bin/bash docker run xxxxx -l equals to /bin/bash -l |
| WORKDIR | 设置各种指令如CMD RUN ENTRYPOINT等的运行目录 | WORKDIR /bin |
| VOLUME | docker中的数据卷，使用 docker run -v (绝对路径挂载local目录到容器中，非绝对路径视为volun的名称，将此volumn挂载到container中) | 创建：docker volume create testvolumn 使用 docker run -v testvolumn:/home/test |
| ADD | 从构建上下文中查找源文件，目录添加到images中，对于tar文件则会自动解压添加到images指定目录 | ADD source.properties /opt/source.properties |
| COPY | 同ADD一样从上向文中拷贝数据到image中，只不过不做解压，等操作 | COPY source.properties /opt/source.properties |
| STOPSIGNAL |  |  |
| ARG | 构建时，添加环境变量的参数，通过$引用环境变量,同ENV的区别是只在构建时生效 | ARG user docker build --build-arg user=bigsea |
| SHElL | 用于替换构建时预置指令如/bin/sh-c |  |
| ONBUILD | 父镜像中定义ONBUILD 指令，子镜像dockefile FROM 父镜像，在构建子镜像时会先执行父镜像中ONBUILD指定的指令 | ONBUILD RUN  ["echo","this is a father mirror"] |

