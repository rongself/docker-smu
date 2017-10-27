FROM alpine:3.5

RUN apk add --no-cache py-pip \
        && pip install shadowsocks
RUN apk add --no-cache nodejs
RUN npm update && npm i -g shadowsocks-manager

ARG SSMGR_PASSWORD=123456
ENV SSMGR_PASSWORD=${SSMGR_PASSWORD}

ARG SS_PORT_RANGE=8381-8390
ENV SS_PORT_RANGE=${SS_PORT_RANGE}

COPY ./config/multiple-user.json /root/multiple-user.json
ENTRYPOINT ssserver --manager-address 0.0.0.0:6001 -c /root/multiple-user.json -d start \
            && ssmgr -t s -s 127.0.0.1:6001 -p ${SSMGR_PASSWORD} -m 0.0.0.0:4001 --debug

EXPOSE 6001 4001 ${SS_PORT_RANGE}