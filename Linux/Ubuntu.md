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
```
##### 权限
```
//sudo 
chmod 更新权限
chmod -R 777 /home/ftpfile  
// -R 递归文件和文件夹
// 777 权限(a=rwx,b=rwx,c=rwx)
其中a,b,c各为一个数字，分别表示User、Group、及Other的权限。
若要rwx属性则4+2+1=7；
```
##### 用户管理
```
--添加
sudo useradd -d /home/ftpfile  ftpuser   // -d 指定用户的根目录（登录显示的目录）ftpuser 用户名
sudo passwd ftpuser //设置用户的密码
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