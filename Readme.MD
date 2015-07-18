adbyby小米路由配置教程
===
——小米路由去广告

* 开启SSH，安装xshell、winscp并配置好地址用户名密码。
* 使用winscp将项目文件拷贝到/extdisks/sda1/usr/bin
* 设置环境变量：·export PATH=$PATH:/extdisks/sda1/usr/bin·
以及·echo 'export PATH=$PATH:/extdisks/sda1/usr/bin' >> /etc/profile·
* 运行adbyby：·adbyby &·
* 要使用去广告，需要设置代理，路径有两个，任选其一：
* 1.设置PC等终端的代理为 192.168.31.1:8118，使用火狐Foxproxy等扩展可以同时用Goagent和去广告
* 2.要使所有终端去广告，需路由设置透明代理：·iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-ports 8118·，可写入防火墙文件：·echo 'iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-ports 8118' >> /etc/firewall.user·
* 开机启动：·vi /etc/init.d/usb_deploy_init_script.sh·
找到以下两行
·rm -rf /tmp/xiaomi_router· 及 
·mkdir -p /tmp/xiaomi_router·
在下面加入一行命令·adbyby &· 

# 说明
* 明文存储的密码将会在第一次登陆成功后保存为数字ID和密码的MD5，明文文件将会删除
* 会员权限及月加速流量等详见[这里](http://swjsq.xunlei.com)
* 自带[这里抄的](https://github.com/mengskysama/XunLeiCrystalMinesMakeDie/blob/master/run.py)纯python实现RSA加密，可选安装pycrypto加快(首次)运算速度
* 登陆成功后会生成`swjsq_wget.sh`以及一个ipk包，可用于直接调用或者安装后运行 __/bin/swjsq__

# TODO
* session过期时间
* web前端

