FROM alpine:3.9

RUN apk update && apk add --no-cache nodejs-npm && npm update && npm i --unsafe-perm -g shadowsocks-manager

ARG SSMGR_PASSWORD=123456
ENV SSMGR_PASSWORD=${SSMGR_PASSWORD}

ARG SMTP_HOST=smtp.126.com
ENV SMTP_HOST=${SMTP_HOST}

ARG SMTP_USERNAME=xxxx
ENV SMTP_USERNAME=${SMTP_USERNAME}

ARG SMTP_PASSWORD=123456
ENV SMTP_PASSWORD=${SMTP_PASSWORD}

COPY ./config/webgui.yml /root/webgui.yml

RUN  sed -i "s:__PLACEHOLDER_USERNAME__:${SMTP_USERNAME}:" /root/webgui.yml \
    && sed -i "s:__PLACEHOLDER_HOST__:${SMTP_HOST}:" /root/webgui.yml \
    && sed -i "s:__PLACEHOLDER_PASSWORD__:${SMTP_PASSWORD}:" /root/webgui.yml

ENTRYPOINT  ssmgr -t m -c /root/webgui.yml -p ${SSMGR_PASSWORD} --debug
EXPOSE 6002