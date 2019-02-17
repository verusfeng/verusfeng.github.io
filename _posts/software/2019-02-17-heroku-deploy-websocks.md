---
layout: post 
category: 软件
title: 使用Heroku部署websocks代理
---

## 使用Heroku部署websocks代理

1. 参考[链接](https://github.com/onplus/shadowsocks-heroku)

2. 注册heroku，Verify email.

3. 跟随github中readme.md的指引部署。



## 本地安装软件

1. 下载[地址](https://github.com/onplus/shadowsocks-heroku/releases)
2. 解压本地，修改json文件
```
{
  "server": "_your_app_name__.herokuapp.com",  
  "local_address": "127.0.0.1",
  "scheme": "ws",
  "local_port": "__ur_local_port__",
  "remote_port": "80",
  "password": "__your_passcode__",
  "timeout": 600,
  "method": "aes-256-cfb"
}
```

3. 修改相关信息即可

4. 运行ss-h.exe 或者start.vbs(后台运行)

5. Try Connect to google, success!