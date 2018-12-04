---
layout: mypost
title: unoconv文档转换中文乱码解决方法
categories: [Linux]
---

### 进入C:\WINDOWS\Fonts把此文件夹下的所有字体打包成zip格式 上传到服务器


```
unzip fonts.zip

mv fonts /usr/share/fonts 

cd /usr/share/fonts/fonts

chmod  -R 755 fonts  

```



### 加载字体 

```
mkfontscale  
mkfontdir  
fc-cache –fv  

```

### 重启服务器



