---
title: node+pm2+mongodb+centos7部署网站
date: 2018-03-05 13:37:16
tags:
---
# node+pm2+mongodb+centos7部署网站
### 1、云服务器申请
- 我这用的腾讯云1G内存+1M带宽 操作系统选了centos7
- 域名big-whale.club 腾讯云上的活动价2块钱 

### 2、服务器软件安装
- yum install git 安装git
- 安装nginx

```

- 添加源
 sudo rpm -Uvh http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm
- 安装
 sudo yum install -y nginx
- 自行启动
 sudo systemctl start nginx.service
```
- 安装mongodb

```
1.配置MongoDB的yum源

创建yum源文件：
vim /etc/yum.repos.d/mongodb-org-3.4.repo
添加以下内容：
[mongodb-org-3.4]  
name=MongoDB Repository  
baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/3.4/x86_64/  
gpgcheck=0  
安装之前先更新所有包 ：yum update （可选操作）

2.安装MongoDB
安装命令：
yum -y install mongodb-org

3.启动MongoDB 
启动mongodb ：systemctl start mongod.service
停止mongodb ：systemctl stop mongod.service

4.设置mongodb远程访问：
编辑mongod.conf注释bindIp,并重启mongodb.
vim /etc/mongod.conf
```
- 安装node
```
1、安装nvm
wget -qO- https://raw.githubusercontent.com/creationix/nvm/v0.31.1/install.sh | bash

2、nvm安装node
nvm install v8.6.0

3、安装pm2
npm install -g pm2
```
- 工程部署
1. 克隆工程 git clone 
2. 安装 npm i
3. nginx 监听80 重定向
4. 域名指向

- 防火墙控制
```
systemctl stop firewalld.service             #停止firewall
systemctl disable firewalld.service        #禁止firewall开机启动

>>> 开启端口
firewall-cmd --zone=public --add-port=80/tcp --permanent
 命令含义：
--zone #作用域
--add-port=80/tcp #添加端口，格式为：端口/通讯协议
--permanent #永久生效，没有此参数重启后失效
>>> 重启防火墙
firewall-cmd --reload
```



