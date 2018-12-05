---
layout: mypost
title: Linux安装elasticsearch-rtf 
categories: [Linux]
---

安装包下载 github地址：https://github.com/medcl/elasticsearch-rtf

下载上传到服务器/usr/local 目录下

解压安装包 unzip elasticsearch-rtf-master.zip

解压完成后 查看elasticsearch-rtf组件	 bin/elasticsearch-plugin list

删除不必要的组件，节省内存

```
bin/elasticsearch-plugin list > /tmp/plugin.log

vim /tmp/plugin.log	删除 analysis-ik 这行，保存退出


cat /tmp/plugin.log

cat /tmp/plugin.log|xargs -I {} bin/elasticsearch-plugin remove {}	删除不必要的组件

```

[root@VM_0_9_centos elasticsearch-rtf-master]# bin/elasticsearch-plugin list	#只剩下一个组件
analysis-ik
[root@VM_0_9_centos elasticsearch-rtf-master]# 


运行
bin/elasticsearch -d

如果报错：是内存不足导致的
```
 Java HotSpot(TM) 64-Bit Server VM warning: INFO: os::commit_memory(0x0000000085330000, 2060255232, 0) failed; error='Cannot allocate memory' (errno=12)
#
# There is insufficient memory for the Java Runtime Environment to continue.
# Native memory allocation (mmap) failed to map 2060255232 bytes for committing reserved memory.
# An error report file with more information is saved as:
# /usr/local/elasticsearch/elasticsearch-rtf-master/hs_err_pid10700.log
```

解决办法：
vim config/jvm.options 修改jvm空间分配

-Xms2g
-Xmx2g

改为
-Xms512m
-Xmx512m

elasticsearch-rtf 需要非root用户运行
adduser 用户名
passwd 用户名 回车输入密码

chown 用户名 文件夹 -R   更改文件所属

非root用户运行 bin/elasticsearch -d
[kkk@VM_0_9_centos elasticsearch]# curl localhost:9200
{
  "name" : "zZimIPO",
  "cluster_name" : "elasticsearch",
  "cluster_uuid" : "jduGCIaJR6mTWpVZm7uhvw",
  "version" : {
    "number" : "5.1.1",
    "build_hash" : "5395e21",
    "build_date" : "2016-12-06T12:36:15.409Z",
    "build_snapshot" : false,
    "lucene_version" : "6.3.0"
  },
  "tagline" : "You Know, for Search"
}










