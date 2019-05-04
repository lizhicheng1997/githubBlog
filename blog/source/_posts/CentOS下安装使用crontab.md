---
title: CentOS下安装使用crontab（这是测试文章）
date: 2018-11-28 15:47:53
tags:
  - CentOS
categories:
  - Linux
  - Linux & Crontab
top: 100
copyright: true
password: 123456
---

## 快速使用

### 一、安装

```
yum install crontabs    // 安装crontab
```

### 二、crontab日志

{% blockquote %}
1.crontab日志位置: /var/log/cron
2.若误删了crontab日志文件, 可重启rsyslogd服务来回复日志文件, 命令为: service rsyslog restart
{% endblockquote %}

### 三、常用命令

```
service crond start     // 启动服务
service crond stop      // 关闭服务
service crond restart   // 重启服务
service crond reload    // 重新载入配置
service crond status    // 查看crontab服务状态
service crond start     // 手动启动crontab服务
chkconfig crond on      // 加入开机自动启动
crontab -e              // 添加相应的任务
vi /etc/crontab         // 添加相应的任务
crontab -l              // 查看当前定时任务
```

<!--more-->

![这是测试图片](CentOS下安装使用crontab/test.jpg)

More info: [Deployment](https://hexo.io/docs/deployment.html)
