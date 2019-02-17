---
layout: post
category: 文章
title: 对ssh的初步认识
---

# ssh原理与应用

### 问题来源

- 群里讨论了ssh隧道的问题。对于这个我不懂隧道是什么，所以网上搜了下。有推荐文章[www.ruanyifeng.com](https://www.ruanyifeng.com/blog/2011/12/ssh_remote_login.html).

- 关于ssh记录md笔记

- 网络隧道，利用一种网络协议（隧道协议）来传输另一种网络协议（源协议）

### ssh是什么
- ssh是每一台linux的标准配置，linux设备就有ssh功能
- ssh是一种网络协议，那么ssh可以充当隧道协议，来传输另一种协议。
- ssh用于计算机之间的加密登陆。传输中，被截获也不会泄露密码和信息

- ssh的实现
    - 商业实现
    - 开源实现 openssh
- ssh的软件 
    - putty
    - xshell

#### 熟悉的ssh应用
- github的ssh协议，github还有一个https的


#### ssh的基础
1. 默认端口22
2. ssh主要用于远程登录
    - ssh user_name@target_host  ssh 用户名@目标IP地址
    - ssh -p 2222 user_name@target_host  
    - 使用参数-p修改登录地址，有些为了安全，服务器没有使用22端口作为ssh登录端口

#### ssh的安全
- ssh-keygen
- 使用github的就知道，计算机要访问远程remote时，需要生成公钥和私钥，公钥放在github上，可以公开分发，私钥不公开。作为本机访问远端服务器的凭证。（李永乐有一个视频时讲ssh安全性的）

- ssh的登录过程，当用ssh访问远程主机时
    1. 远程主机收到用户的登录请求，把自己的公钥发给用户。
    2. 用户收到公钥，用公钥把<登录密码>加密，返回给主机。
    3. 主机可以用私钥，把加密后的数据，解密出登录密码，密码正确允许登录。

- 公钥，私钥，大质数
    - 公钥指纹， 公钥的长度比较长，对其做md5后，变为128位(16个字节)的指纹
    - RSA key fingerprint is 98:2e:d7:e0:de:9f:ac:67:28:c2:42:2d:37:16:58:4d
    - 公钥指纹主要是为了让用户不要访问到其他伪装的钓鱼服务器
    - 公钥指纹是远程主机公开贴出，给用户比对的。

- ssh密码登录，每次ssh登录执行流程都如上面类似。
- ssh公钥登录，远程主机存放公钥，本机存放私钥。类似git
    - ssh-keygen生成公私钥匙
    - ssh-copy-id user@host 把公钥复制到远程主机上。
    - 如果还是不行，就打开远程主机的/etc/ssh/sshd_config这个文件，检查下面几行前面"#"注释是否取掉
        - RSAAuthentication yes
        - PubkeyAuthentication yes
        - AuthorizedKeysFile .ssh/authorized_keys
    - 再重启ssh服务
     - service ssh restart (for ubuntu)
     - ssh restart (for debian)

#### ssh尝试
1. 从ss节点中找一个服务器地址
    - ![ssh-host](./note-pic/ssh-host.png)
2. 用xshell登录，填入地址端口22
    - ![ssh-login](./note-pic/ssh-xshell-login.png)
3. 确认公钥指纹是否正确
    - ![ssh-pubkey](./note-pic/ssh-pubkey.png)
4. 输入用户名
    - ![ssh-username](./note-pic/ssh-username.png)
5. 输入用户名对应密码
    - ![ssh-passcode](./note-pic/ssh-passcode.png)
6. 可选public key认证
    - ![ssh-keylogin](./note-pic/ssh-keylogin.png)


#### ssh转发
1. 绑定本地端口，ssh -D 8080 user@host 让所有通过本地8080的数据通过ssh传向远程主机。
    - 软件可以设置走本地8080端口的。

2. 本地端口转发
    - 假定
    - host1是本地主机 
    - host2是远程主机 
    - 由于种种原因，这两台主机之间无法连通。
        - host1不能直连host2
    - 但是
    - 另外还有一台host3
    - 可以同时连通前面两台主机。
        - host1 可以连接 host3
        - host2 可以连接 host3
    - 通过host3，将host1连上host2。

    - $ ssh -L 2121:host2:21 host3
        - 命令中的L参数一共接受三个值，分别是"本地端口:目标主机:目标主机端口"，它们之间用冒号分隔。这条命令的意思，就是指定SSH绑定本地端口2121，然后指定host3将所有的数据，转发到目标主机host2的21端口（假定host2运行FTP，默认端口为21）。
    - 这样一来，我们只要连接本地的2121端口，就等于连上了host2的21端口，就可以访问host2 21端口的服务了
        - $ ftp localhost:2121

    - $ ssh -L 5900:localhost:5900 host3
        - 它表示将本机的5900端口绑定host3的5900端口（这里的localhost指的是host3，因为目标主机是相对host3而言的）。

3. 远程端口转发
    - 绑定远程端口的转发。

```text

host1 是家用电脑，在公网
host2 是公司主机（比如内部数据库）, 在内网
host3 是公司办公电脑，在内网

现在，host1连不上host2，也连不上host3。但是，host3可以同时连上host1和host2，所以要通过它中转。

```