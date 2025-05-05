### 安装

```

sudo apt install -y mysql-server
```

### 版本
```
mysql --version
```

### 启动
```
sudo systemctl start mysql
```

### 开机自启sql
```
sudo systemctl enable mysql
```

### 状态检查
```
sudo systemctl status mysql
```
## 本地使用（目前我觉得没什么用）
登录mysql
```
sudo mysql
```


## 开启远程权限

### 更改配置文件，监听所有ip访问
```
cd /etc/mysql/mysql.conf.d/*
```
里面按理说有**mysqld.cnf**
```
sudo nano mysqld.cnf
```
把
```
bind-address = 127.0.0.1
```
改为
```
bind-address = 0.0.0.0
```
### 重启mysql,配置生效
```
sudo systemctl restart mysql
```

### 创建授权远程用户
先登录
```
sudo mysql
```
创建一个用户用于远程连接
```
CREATE USER 'remote_user'@'%' IDENTIFIED BY 'strong_password';
GRANT ALL PRIVILEGES ON your_database.* TO 'remote_user'@'%';
FLUSH PRIVILEGES;
```
验证用户是否创建
```
SELECT user, host FROM mysql.user;
```

