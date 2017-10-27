FROM alpine:3.5

RUN apk add --no-cache wget openssl ca-certificates && update-ca-certificates \
    && wget https://github.com/xtaci/kcptun/releases/download/v20171021/kcptun-linux-amd64-20171021.tar.gz \
    && mkdir /root/kcptun \
    && tar -zxvf kcptun-linux-amd64-20171021.tar.gz -C /root/kcptun 

WORKDIR /root/kcptun/

ARG KCPTUN_PASSWORD=123456
ENV KCPTUN_PASSWORD=${KCPTUN_PASSWORD}

ARG KCPTUN_TARGET=127.0.0.1:3389
ENV KCPTUN_TARGET=${KCPTUN_TARGET}

ENTRYPOINT ./server_linux_amd64 \
            --listen ":8088" \
            --target "${KCPTUN_TARGET}" \
            --key "${KCPTUN_PASSWORD}" \
            --crypt "aes-128" \
            --mode "fast2" \
            --mtu 1400 \
            --sndwnd 1024 \
            --rcvwnd 1024 \
            --datashard 30 \
            --parityshard 15 \
            --nocomp false
EXPOSE 8088/udp