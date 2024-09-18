# 使用CentOS官方镜像作为基础镜像
FROM centos:centos7.9.2009
#RUN mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo.backup
COPY CentOS-Base.repo /etc/yum.repos.d/
#RUN curl -o /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo
#RUN sed -i -e '/mirrors.cloud.aliyuncs.com/d' -e '/mirrors.aliyuncs.com/d' /etc/yum.repos.d/CentOS-Base.repo
# 安装OpenJDK
RUN yum install -y java-1.8.0-openjdk java-1.8.0-openjdk-devel
 
# 设置JAVA_HOME环境变量
ENV JAVA_HOME /usr/lib/jvm/java-1.8.0-openjdk
 
# 安装Mave
WORKDIR /usr/local/maven
COPY maven /usr/local/maven
# 设置MAVEN_HOME环境变量
ENV MAVEN_HOME /usr/local/maven
 
# 设置PATH环境变量，确保mvn命令可以被全局调用
ENV PATH $PATH:$MAVEN_HOME/bin
 
# 设置工作目录
WORKDIR /app
 
# 这个命令在构建镜像时执行，用于清理缓存和临时文件
RUN yum clean all
 
# 当容器启动时，显示一个欢迎信息
#CMD ["echo", "CentOS + JDK + Maven Docker Image is ready."]
