在Linux服务器上启动项目时，发现启动失败。查看启动日志时，发现卡在
```
[INFO] Deploying web application directory ...
```
在网上找了找原因，再次记录一下
### 解决方案
在jdk的安装目录下找到 ${JAVA_home}/jre/lib/security/Java.security 文件
修改 securerandom.source 设置项
```
securerandom.source=file:/dev/./urandom
```
### 原因
linux或者部分unix系统提供随机数设备是 /dev/random和/dev/urandom
两个有区别，urandom安全性没有random高，但random需要时间间隔生成随机数。
jdk默认调用random。
附上 [原文](http://www.cnblogs.com/mycifeng/p/6972446.html)链接