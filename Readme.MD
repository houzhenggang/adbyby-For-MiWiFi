adbyby小米路由配置教程
===
——小米路由去广告

* 开启SSH，安装xshell、winscp并配置好地址用户名密码。
* 使用winscp将项目文件拷贝到/extdisks/sda1/usr/bin，没有就自己新建，adbyby修改权限为777。
* 设置环境变量：`export PATH=$PATH:/extdisks/sda1/usr/bin`
以及`echo 'export PATH=$PATH:/extdisks/sda1/usr/bin' >> /etc/profile`
* 运行adbyby：`adbyby &`
* 要使用去广告，需要设置代理，路径有两个，任选其一：
* 1.设置PC等终端的代理为 192.168.31.1:8118，使用火狐Foxyproxy等扩展可以同时用Goagent和去广告
* 2.要使所有终端去广告，需路由设置透明代理：`iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-ports 8118`，可写入防火墙文件：`echo 'iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-ports 8118' >> /etc/firewall.user`
* 开机启动：`vi /etc/init.d/usb_deploy_init_script.sh`
找到以下两行
`rm -rf /tmp/xiaomi_router` 及 
`mkdir -p /tmp/xiaomi_router`
在下面加入一行命令`adbyby &` 


