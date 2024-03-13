FROM debian:trixie-slim

RUN apt-get update && apt-get install -y \
    adduser \
    cronie \
    curl \
    git \
    libnginx-mod-http-echo \
    libnginx-mod-http-fancyindex \
    nginx \
    rsync

RUN addgroup \
    --gid=888 \
    ftpsync

RUN adduser \
    --system \
    --home=/opt/archvsync \
    --shell=/bin/bash \
    --uid=888 \
    --gid=888 \
    ftpsync

RUN git clone https://salsa.debian.org/mirror-team/archvsync.git /opt/archvsync

RUN chown -R ftpsync:ftpsync /opt/archvsync

RUN ln -sf /dev/stdout /var/log/nginx/access.log
RUN ln -sf /dev/sterr /var/log/nginx/error.log

CMD ["nginx", "-g", "daemon off;"]
