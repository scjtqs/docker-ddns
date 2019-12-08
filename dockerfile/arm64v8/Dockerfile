# 基础镜像
FROM multiarch/alpine:arm64-edge

# 作者信息
MAINTAINER DDNS Docker Maintainers "scjtqs@qq.com"
# Environments
ENV TIMEZONE            Asia/Shanghai
ENV PHP_MEMORY_LIMIT    512M
ENV MAX_UPLOAD          50M
ENV PHP_MAX_FILE_UPLOAD 200
ENV PHP_MAX_POST        100M
ENV COMPOSER_ALLOW_SUPERUSER 1

# 修改源
RUN echo "http://mirrors.aliyun.com/alpine/latest-stable/main/" > /etc/apk/repositories && \
    echo "http://mirrors.aliyun.com/alpine/latest-stable/community/" >> /etc/apk/repositories

# 安装需要的软件
RUN apk update && \
    apk add --no-cache ca-certificates && \
    apk add --no-cache curl bash tree tzdata php7-openssl php7 php7-curl php7-json && \
    cp -rf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime\
    && apk del tzdata \
    && mkdir /path\
    && chmod 777 /path \
    && echo '* * * * * /usr/bin/php /path/ddns.php > /dev/null 2>&1'>>/var/spool/cron/crontabs/root \
    && rm -rf /var/cache/apk/*
RUN mkdir -p /var/log/cron \
 && touch /var/log/cron/cron.log

RUN mkdir -p /usr/local/var/log/php7/
RUN mkdir -p /usr/local/var/run/


ENTRYPOINT ["/usr/sbin/crond","-f","-L","/var/log/cron/cron.log"]
