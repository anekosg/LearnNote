#### Linux 操作
##### 文件使用
```
--显示
ls -lt  //按时间排序
--查找
find  -type f  -name "*ftp.conf*"   //-type 限制类型 f 文件类型,-name 限制名字 "*ftp.conf*" 正则匹配
```
##### 文件夹使用
```
mkdir dir 添加文件夹
删除
rm -r * 删除文件和文件夹
移动
cp -r venv ../PythonProject  //-r 递归

```
##### 权限
```
//sudo 
chmod 更新权限(文件或文件夹下的 用户有什么权限)
chmod -R a=rwx,g=rwx,o=rwx  /home/ftpfile 

chmod -R 777 /home/ftpfile  
// -R 递归文件和文件夹
// 777 权限(a=rwx,b=rwx,c=rwx)
其中a,b,c各为一个数字，分别表示User、Group、及Other的权限。
若要rwx属性则4+2+1=7；

chown 更新权限（文件或文件夹 属于谁）
chown -R -v root:mail test6     //root拥有者,mail群组 test6文件或文件夹 -R递归文件夹 -v显示详情
```
##### 用户管理
```
--添加
sudo useradd -d /home/ftpfile  ftpuser   // -d 指定用户的根目录（登录显示的目录）ftpuser 用户名
sudo passwd ftpuser //设置用户的密码
--查看 当前所有用户
cat /etc/passwd
--修改 用户
sudo usermod
```
##### vim使用
```
vim file 
i   进入编辑模式
:q  退出
:w  保存
:w! 强制保存
:qw 保存并退出
:q! 强制退出，不保存更改
```
##### ufw防火墙使用
``` 
sudo ufw enable 开启防火墙
sudo ufw status 查看状态和存在的规则
sudo ufw allow 22/tcp 开启规则（一定要使用，要不然ssh连不上服务器了）
sudo ufw allow 10000:12000/tcp  开启连续规则
sudo ufw delete allow 10000:12000/tcp  删除连续规则
```
##### 下载器/安装
```
wget -b -c url   //b后台运行，c断点续传
dpkg -i xxx.deb  //i安装 
```
##### apt
```
sudo apt install -f pack  //f修复安装包的依赖；
```
##### 系统工具
```
netstat -an|grep 3306  //指定端口是否开启
sudo netstat -nltp  //查看所有开发监听的端口 不加sudo 显示不全
sudo lsof -i -P -n | grep LISTEN  // 也可以查看 服务接口
```