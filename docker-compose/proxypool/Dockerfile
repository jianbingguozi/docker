FROM alpine
WORKDIR /data/
COPY proxypool-linux-amd64 /data/proxypool
RUN sed -i "s/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g" /etc/apk/repositories
# 配置网络代理
ENV http_proxy http://10.8.2.151:1082
ENV https_proxy http://10.8.2.151:1082

ENTRYPOINT ["/data/proxypool","-c","/data/config/config.yaml"]