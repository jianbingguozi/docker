# 下载要编译的源码
FROM alpine as clone
RUN sed -i "s/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g" /etc/apk/repositories
RUN apk update && \
  apk add --no-cache --virtual bash git openssh
WORKDIR /data/
RUN git clone -b hello-jar https://github.com/jianbingguozi/test.git

# 编译源码
FROM maven as build
WORKDIR /data/
COPY --from=clone /data/test .
RUN mvn clean package -Dmaven.test.skip=true

# 运行
FROM openjdk:8-jre-alpine as run
WORKDIR /data/
COPY --from=build /data/target/demo-0.0.1-SNAPSHOT-jar-with-dependencies.jar ./demo.jar
ENTRYPOINT ["java","-jar","./demo.jar"]
