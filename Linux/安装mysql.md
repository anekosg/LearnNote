### 安装MYSQL
```
1，sudo apt install mysql-server
2，需要使用默认密码登录（允许外网访问）：
    cd ../../etc/mysql.conf.d/mysqld.cnf
    更新   bind-address  = 0.0.0.0
3，拿到默认账号密码 cd ../../etc/mysql.cnf
4，默认账号密码登录：
sudo mysql  -u root -p
5，更改登陆用户的权限（root 用户允许外网登录）
use mysql;
查看：select host,name from user;
更新账户：update user set host ='%' where name ='root'
更新密码： alter user 'root'@'%' identified with mysql_native_password by 'password';  //root用户，password密码，%为user表host字段
最后一步刷新：flush privileges;
```