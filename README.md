更新系统组件

apt-get update
apt-get install curl

开启BBR

echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf
sysctl -p
sysctl net.ipv4.tcp_available_congestion_control
lsmod | grep bbr

安装V2ray

bash <(curl -L -s https://install.direct/go.sh)

创建目录

mkdir /etc/你的域名

执行：
vi /etc/ssh/sshd_config
按 i
修改PermitRootLogin no,为yes；
修改passwordAuthentication no为yes。
按     esc  
输入  :wq   保存
执行passwd root，给root用户添加密码。密码不回显。
执行：/etc/init.d/ssh restart 或者 service sshd restart 重启sshd服务。
启动服务

service v2ray start

停止服务

service v2ray stop

v2ray配置文件生成器

https://v2.ziyls.com/

申请域名：

https://ap.www.namecheap.com/
https://dash.cloudflare.com/

代码：

https://bb-r.net/?p=222

制作证书
添加TXT记录

https://freessl.cn/
https://www.myssl.cn/tools/merge-pem-cert.html

视频连接：
https://www.youtube.com/watch?v=FXWGOxjiFVM&t=1903s

3.搭建完成后，登陆：https://intmainreturn0.com/v2ray-config-gen/#，生成v2ray配置保存到一个名为config.json的文件。备用
4.执行：vi /etc/ssh/sshd_config，修改PermitRootLogin no,为yes；passwordAuthentication no为yes。
执行passwd root，给root用户添加密码。密码不回显。
执行：/etc/init.d/ssh restart 或者 service sshd restart 重启sshd服务。
5.下载Winscp.exe，打开后文件协议选择：scp，然后点击“高级（A）”按图2设置，点击登陆。
      
6.进入\etc\v2ray中，将第3步制作好的config.json覆盖原来的文件。
7.下载v2rayN ，https://github.com/2dust/v2rayN/releases,任意一个目录解压缩，之后打开，进行配置，再然后启用http代理，之后还不能科学上网。为什么呢？看控制台报错信息
