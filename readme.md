# WNMP(sodevel.com版) 说明文档

本环境基于 `bill-wangwang/wnmp` 的v1.0.2 版本上修改而成。目的是让新同学快速、稳定的搭建开发环境，开始你的PHP之旅。

- 本开发包为“绿色版本”，无需安装，解压即用。
- 网传主要都是基于apache，而目前主流的nginx 几乎没有。

# 联系作者

工作微信：pmtt9121

PHP课程官网：https://www.sodevel.com

# 环境说明

基于 windows7（64位） 的操作系统测试通过，估计 windows 10 也没问题。

不支持 32位 操作系统「目前主流都是64位」。

- PHP 默认使用 7.1.17版本（可切换至5.6.36）
- nginx  1.14.0 
- MySQL 5.6.40

使用 `RunHiddenConsole.exe` 运行nginx、mysql，如果有杀毒软件报错，请忽略或设置白名单。

# 使用说明

如果碰到不可解决的问题，请联系工作微信`pmtt9121`，索取视频安装课程。

## 下载

[https://github.com/983430207/sodevel-wnmp/archive/master.zip](https://github.com/983430207/sodevel-wnmp/archive/master.zip)

部分同学反映下载速度慢，提供国内备份地址：[点此下载](https://gitee.com/sodevel/sodevel-wnmp/) 在页面右侧寻找 “克隆/下载”的按钮，选择 `下载zip`。
 
## 安装

解压文件到任意目录（注意：目录中不能出现中文和空格），建议使用 `d:\wnmp` 这样简单的目录位置。

## 启动

- 双击 “启动全部.bat” 即可启动全部服务（最好用管理员权限运行）
- 双击 “停止全部.bat” 即可停止全部服务
- 双击 “重启nginx.bat”即可重启nginx

## 测试效果

输入 `http://127.0.0.1/phpmyadmin/` 和 `http://127.0.0.1/` 能看到数据库管理工具、PHP状态信息，就算成功。

## xxx.dll 不存在的解决方案

本套件需要 vc10、vc11、vc14 库方可运行。

如果报错，可以依次安装 `vs_redist` 目录下的三个文件即可。

强烈建议：使用管理员账号（administrator）登陆电脑，否则可能会因为权限不足导致安装失败、安装后错误依然存在等问题。

如果不知道如何使用管理员账号登陆，最好用管理员权限运行。

## 因为端口占用导致失败的解决方案

- nginx 使用 80 端口
- php 使用 9000 和 9001 端口
- mysql 使用 3306 端口

如果安装失败，请检查端口是否被占用。检查方法：

先进入 `cmd` 命令行，输入指令 `netstat -ano|findstr 80` 可以看到80端口是否被占用。

如果被占用，可以根据pid找到对应的进程，强行关闭即可。

注意：应该将占用的软件彻底删除掉，否则下次还会出问题，如果实在没办法，重新安装操作系统是好选择。

# 数据库信息

数据库默认账号：root，默认密码：123456。

启动成功后，输入 http://127.0.0.1/phpmyadmin 即可登陆web管理界面。

建议：在开发中使用 navicat 管理数据库。

# 目录结构
```
├─logs  ------------------------------- nginx日志目录 （必须有可写权限）
├─mysql-5.6.40-winx64  ---------------- mysql目录
│  ├─data  ---------------------------- mysql数据库数据存储目录（必须有可写权限）
├─nginx-1.14.0   ---------------------- nginx目录
│  ├─conf  ---------------------------- nginx配置目录
│  │  └─vhost ------------------------- 虚拟站点配置目录（自动加载里面的*.conf）
├─php-7.1.17  ------------------------- php7目录（9000端口）
├─php-5.6.36  ------------------------- php5目录（9001端口）
├─temp  ------------------------------- nginx temp目录 （必须有可写权限）
└─web   ------------------------------- 网站根目录（代码存放处）
    └─phpmyadmin  ---------------------phpMyAdmin站点目录

```