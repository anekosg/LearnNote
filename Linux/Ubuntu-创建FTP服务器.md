#### 基于Ubuntu创建 FTP服务器
1. 更新ubuntu服务器（update，upgrade）
2. apt 安装 vsftpd 服务
```
sudo apt install vsftpd
```
3. cd到etc目录下 更改 
```
sudo vim /etc/vsftpd.conf
一些设置：
//加入ftpuser目录
local_root=/home/ftpuser  
//配置 20任意端口范围（必须大于1024）
pasv_min_port=10000
pasv_max_port=10050 

listen=NO
listen_ipv6=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_file=/var/log/vsftpd.log
xferlog_std_format=YES
ftpd_banner=Welcome to blah FTP service.
chroot_local_user=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
ssl_enable=NO
utf8_filesystem=YES

加入创建的用户
sudo vim /etc/vsftpd.chroot_list # 加入创建的用户 ftpuser
```
4. 在home下创建用户文件夹,并更新权限
```
sudo mdkir /home/ftpuser
sudo chmod -R 777 /home/ftpuser 
```
5. 添加ftp用户
```
sudo useradd -d /home/ftpfile  ftpuser
sudo passwd ftpuser 输入密码
```
6. 重启vsftpd 服务
```
sudo service vsftpd restart
```
7. 开启防火墙端口
```
sudo ufw allow 21/tcp
sudo ufw allow 10000:10050/tcp
```
