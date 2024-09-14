FROM maven as build-stage
RUN mkdir -p /zjzWx
WORKDIR /zjzWx
COPY . /zjzWx
RUN --mount=type=cache,id=maven-store,target=/root/.maven-store \
    mvn clean install -Dmaven.test.skip=true
#编译JAR包HivisionIDPhotos-wechat-weapp-1.0-SNAPSHOT.jar
## -- stage: target => java
FROM eclipse-temurin:8-jre

## 创建目录，并使用它作为工作目录
RUN mkdir -p /zjzWx
WORKDIR /zjzWx
## 将后端项目的 Jar 文件，复制到镜像中
COPY --from=build-stage /zjzWx/target/HivisionIDPhotos-wechat-weapp-1.0-SNAPSHOT.jar app.jar

## 设置 TZ 时区
ENV TZ=Asia/Shanghai
## 设置 JAVA_OPTS 环境变量，可通过 docker run -e "JAVA_OPTS=" 进行覆盖
ENV JAVA_OPTS="-Xmx1024M -Xms256M"

## 应用参数
ENV ARGS=""

## 暴露后端项目的 8010 端口
EXPOSE 8010

## 启动后端项目
CMD java ${JAVA_OPTS} -jar app.jar $ARGS
