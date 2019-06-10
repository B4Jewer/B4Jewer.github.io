---
layout: post
title: Blogging Like a Hacker
---
检查是否对错误日志进行管理:

```
show variables like 'log_error';
```

检查是否配租二进制日志：

```
show variables like 'log_bin';
show binary logs;
```

检查是否配租通用查询日志安全：

```
show variables like '%general%';
```

检查是否设置禁止MySQL对本地文件存取：

```
show variables like 'local_infile'; 
load data local infile 'sqlfile.txt' into table users fields terminated by ',';
```

检查test是否已被删除：

```
show databases;
```

检查是否对无关账号进行管理：

```
SELECT user,host FROM mysql.user WHERE user = ''
```

检查是否对user授权表进行控制：

```
SELECT * FROM user\G;
SELECT user,host from mysql.user where (select_priv='Y') or (insert_priv='Y') or (update_priv='Y') or (create_priv='Y') or (drop_priv='Y');

select user, host from mysql.user where File_priv = 'Y';
select user, host from mysql.user where Process_priv = 'Y';
select user, host from mysql.user where Super_priv = 'Y';
SELECT user, host FROM mysql.user WHERE Shutdown_priv = 'Y';
SELECT user, host FROM mysql.user WHERE Create_user_priv = 'Y';
SELECT user, host FROM mysql.user WHERE Reload_priv = 'Y';
SELECT user, host FROM mysql.db WHERE Grant_priv = 'Y';
```

检查是否对db授权表进行控制：

```
SELECT * FROM db\G;
SELECT user, host FROM mysql.db WHERE db='mysql' AND ((select_priv='Y') OR (insert_priv='Y') OR (update_priv='Y') OR (delete_priv='Y') OR (create_priv='Y') OR (drop_priv='Y'));

SELECT user,host,db FROM mysql.db WHERE select_priv='Y' OR insert_priv='Y' OR update_priv='Y' OR delete_priv='Y' OR create_priv='Y' OR drop_priv='Y' OR alter_priv='Y';
```

检查是否对账号运行权限进行管理：

```
select * from mysql.user\G;
show grants;
```

检查是否配置了单个用户最大连接数：

```
show variables like '%max_connections%'; //整个服务器
show variables like 'max_user_connections'; //单个用户最大连接数
```

检查默认管理员账号是否已更名：

```
SELECT * from MySQL.user where user='root';
select user,host from user;
```

检查是否使用默认端口：

```
show global variables like 'port';
```



