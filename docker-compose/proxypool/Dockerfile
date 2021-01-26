FROM alpine
WORKDIR /data/
RUN sed -i "s/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g" /etc/apk/repositories
RUN apk add --no-cache tzdata
COPY proxypool-linux-amd64 /data/proxypool
COPY config /data/config
RUN chmod +x /data/proxypool
# 配置网络代理
ENV http_proxy http://10.8.2.151:1082
ENV https_proxy http://10.8.2.151:1082

EXPOSE 12580

ENTRYPOINT ["/data/proxypool","-c","/data/config/config.yaml"]