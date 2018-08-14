---
layout: mypost
title: Linux下Mysql忘记密码解决办法
categories: [Mysql]
---


###修改/etc/my.cnf 配置文件,在[mysqld]下添加一行

```
skip-grant-tables
```
### 保存退出,重启Mysql服务
### 进入Mysql命令行,mysql -u root -p输入密码回车进入,
```
mysql> use mysql; #更改数据库
mysql> UPDATE user SET PASSWORD =password("你的密码") where user='root'; 更改密码
Query OK, 3 rows affected (0.00 sec)
Rows matched: 3  Changed: 3  Warnings: 0
mysql> flush privileges;	#刷新MySQL的系统权限相关表，以防止更改后拒绝访问；或者重启MySQL服务器
Query OK, 0 rows affected (0.00 sec)

```

### 更改完成后,修改/etc/my.cnf 配置文件,在[mysqld]下 skip-grant-tables 这行删除

### 重启Mysql服务,即可登录

###注意事项
###修改配置文件前可拷贝一份作为备份
###重启MySQL服务前，最好断掉与MySQL关联的服务，以免数据丢失。

