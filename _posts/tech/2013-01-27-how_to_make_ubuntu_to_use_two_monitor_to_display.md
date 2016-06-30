---
layout: post
title: ［操作系统］Ubuntu 12.04 + Gnome 3 的笔记本+显示器 配置成双屏幕显示
author: Taffy
category: tech
description: 由于家里有一台多余显示器，所以希望能够连接上笔记本配置ubuntu为双屏幕。环境是：ubuntu12.04 + Gnome 3
---

由于家里有一台显示器，所以希望能够连接上笔记本配置ubuntu为双屏幕。环境是：ubuntu12.04 + Gnome 3

查了一下网上的类似的情况，都写的很不清楚。

方法有好几种，可以在终端下配置，也可以利用图形界面来配置。这里介绍一种最简单的方法。

---
## 1.登录配置界面


![](http://img.my.csdn.net/uploads/201301/27/1359278858_4866.png)

---
## 2.进入显示界面并设置。

![](http://img.my.csdn.net/uploads/201301/27/1359278878_2560.png)

反选在镜像显示。并且两个显示器都选上开启。（这时候可能会出现配置问题，

提示要设置的显示部分超出了screen的最大设置max（x,x））

---
## 3.配置xorg.conf（如果上一步没有报错的话就不用来这里了）

ubuntu12.04里的 xorg.conf 在 /etc/X11这个文件夹里面

*注：Xorg是 X11 窗口系统的一个开源实现。Xorg 在 Linux 用户中非常流行，已经成为图形用户程序的必备条件，所以大部分发行版都提供了它。Xorg 可以通过/etc/X11/xorg.conf 或/etc/xorg.conf 和位于/etc/X11/xorg.conf.d/ 的配置文件配置，另外鸟哥有一篇专门介绍X window体系的系列见： [X Window設定介紹][X window]*

从终端里进入目录/etc/X11并打开xorg.conf （之所以用终端是因为要获取管理员权限，即sudo），找到下面这段

    Section "Screen"  
        Identifier "aticonfig-Screen[0]-0"  
        Device     "aticonfig-Device[0]-0"  
        Monitor    "aticonfig-Monitor[0]-0"  
        DefaultDepth     24  
        SubSection "Display"  
            Viewport   0 0  
            Depth     24  
        EndSubSection  
    EndSection  

在subsection "Display"这段中加上一句（4096也可是别的什么数，但是必须要大于两个显示器的总宽度，比如说Monitor A最大为1600 × 900， B最大为1440 × 900， 则要想实现显示至少为Virtual至少为3040 × 900）

    Virtual         4096 4096  

即变为

    Section "Screen"  
        Identifier "aticonfig-Screen[0]-0"  
        Device     "aticonfig-Device[0]-0"  
        Monitor    "aticonfig-Monitor[0]-0"  
        DefaultDepth     24  
        SubSection "Display"  
            Virtual         4096 4096  
            Viewport   0 0  
            Depth     24  
        EndSubSection  
    EndSection  

---
## 4.接下来重复第二步即可。

[X window]: http://linux.vbird.org/linux_basic/0590xwindow.php

<script type="text/javascript">
     $('pre').addClass('prettyprint linenums')
</script>

<script src="https://google-code-prettify.googlecode.com/svn/loader/run_prettify.js?skin=sunburst"></script>
