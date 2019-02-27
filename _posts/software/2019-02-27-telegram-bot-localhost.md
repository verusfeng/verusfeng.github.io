---
layout: post
category: 软件
title: 使用ngrok在本地运行Telegram机器人应用
---

# ngrok

- 注册, 使用免费账户就行. 
- 把本地端口的服务, 映射到ngrok指定的地址上, 让外网可以访问本地应用.
- 方便开发, 减少不必要的步骤
- telegram的webhook设置到ngrok给出的地址, 服务由本地端口映射出去,提供webhook服务.

## 运行ngrok

- 执行ngrok http 8080 , 记住这个端口
- 会返回一个https的地址 https://<random>.ngrok.io, 保存这个地址, 保持ngrok服务运行

# 本地运行bot应用

0. 新建虚拟环境, virtualenv
1. 安装依赖
1. 新建应用bot.py,编写程序.
2. 运行flask run -p 8080 , 端口必须与ngrok端口一致
    - flask网页服务出错的话, 要设置一下应用和环境
    - set FLASK_APP=bot.py
    - set FLASK_ENV=development
    - 重新运行即可
3. 提示网络错误. 代理问题. 因为是在本地上跑的服务, 无法直接连接telegram的服务器的.
    - 找到第三方库中,网络连接的部分, 这里是telebot的文件apihelper.py. 
    - 修改proxy=none 为proxy=dict({'https':"host:port"})
4. 重新运行就好了.

# 其它
1. token等其它敏感数据可以放在独立的配置文件中 config.ini
2. 在应用中读取, 需要configparser库,安装就好了. 

# 整个bot的流程

1. 有用户给bot发送信息了. 
2. telegram会看有没有设置webhoo, 有设置webhook了,数据包就会post到webhook上, 即ngrok的地址
3. ngrok得到一个post的数据包, 通过内网穿透,等同于post到本地端口8080
4. 而这里跑着一个flask应用, 会处理这个数据包. 然后执行回复信息. 
5. 这个数据有用户的user_id, 本地程序使用了telebot库, 实际也是封装了bot api
6. 发送信息, 就是用```API/sendmessage?chat_id=<id>&text=<reply_msg>``` 
7. 所以在本地运行需要设置一下代理.

