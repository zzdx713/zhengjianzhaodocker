# 使用CentOS官方镜像作为基础镜像
FROM centos:centos7.9.2009
COPY CentOS-Base.repo /etc/yum.repos.d/
WORKDIR /usr/local/node
COPY node /usr/local/node
ENV NODE_PATH /usr/local/node  
# 设置软链
RUN ln -s ${NODE_PATH}/bin/node /usr/local/bin/node && \
  ln -s ${NODE_PATH}/bin/npm /usr/local/bin/npm

#RUN npm install -g yarn --registry=https://registry.npmmirror.com
#RUN ln -s ${NODE_PATH}/bin/yarn /usr/local/bin/yarn
 
# 设置工作目录
WORKDIR /app
 
# 这个命令在构建镜像时执行，用于清理缓存和临时文件
RUN yum clean all
 
## 暴露后端项目的 3006 端口
EXPOSE 3006
