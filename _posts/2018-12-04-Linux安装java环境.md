---
layout: mypost
title: Linux安装java环境
categories: [Linux]
---


### 下载jdk https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
###	选择对应的Linux版本下载 可在Windows下载完成后，通过FTP或者SSH到发送到Linux上

### 在usr目录下建立java安装目录，将jdk-8u191-linux-x64.tar.gz移动到java目录下

```
cd /usr

mkdir java

mv jdk-8u191-linux-x64.tar.gz /usr/java/
```

### 解压安装包

```
tar -zxvf jdk-8u191-linux-x64.tar.gz
```

### 安装完毕为他建立一个链接以节省目录长度

```
ln -s /usr/java/jdk1.8.0_191/ /usr/jdk
```

### 编辑配置文件，配置环境变量

```
vim /etc/profile
```

### 在文本的末尾添加如下内容：

```
JAVA_HOME=/usr/jdk
CLASSPATH=$JAVA_HOME/lib/
PATH=$PATH:$JAVA_HOME/bin
export PATH JAVA_HOME CLASSPATH
```
### 执行命令 ：source /etc/profile

### 查看安装情况  java --version

java version "1.8.0_191"
Java(TM) SE Runtime Environment (build 1.8.0_191-b12)
Java HotSpot(TM) 64-Bit Server VM (build 25.191-b12, mixed mode)


### 查看系统是64位还是32位 uname -m

