# docker-smu
用dock-compose一键搭建神秘的多用户平台:)

## 使用

1. 安装好docker(>=17.x)和docker-compose(>=1.16)
2. 添加编辑配置文件
```
git clone https://github.com/rongself/docker-smu.git
cd docker-smu
cp .env.example .env
```
3. 编辑配置,填写好邮箱smtp设置,其他根据需求自行改动
```
vi .env

# 邮箱信息,用于管理平台发注册短信验证码
SMTP_HOST=smtp.126.com
SMTP_USERNAME=用户名@126.com
SMTP_PASSWORD=密码 #注意:126邮箱不是用密码,而是要到设置里设置 客户端授权密码

```
4. 运行
```
docker-compose up
```

5. 访问http://[你的ip或域名]:[默认6002端口],注册账号,默认第一个注册的就是超级管理员

这个平台的使用方法参考官方文档:[https://github.com/shadowsocks/shadowsocks-manager/wiki/WebGUI](https://github.com/shadowsocks/shadowsocks-manager/wiki/WebGUI)
