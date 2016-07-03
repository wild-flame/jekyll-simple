---
layout: post
title: ［Python］ubuntu 12.04下面安装影像处理的库PIL的安装, Pygame的安装，以及一些实用的资料整理
author: Taffy
category: tech
description: 之前做影像处理都是用的Matlab,这次打算用Python来做，因此要在Python上面安装PIL（PYTHON IMAGE LIBRARY)，安装的环境是ubuntu12.04, Python 2.7.3, GCC 4.6.3
---

<!--下面是正文-->
之前做影像处理都是用的Matlab,这次打算用Python来做，因此要在Python上面安装PIL（PYTHON IMAGE LIBRARY)，安装的环境是ubuntu12.04, Python 2.7.3, GCC 4.6.3等。

## 1.Install PIL

    $ sudo apt-get install python-imaging
    $ sudo apt-get install libjpeg-dev libfreetype6 libfreetype6-dev zlib1g-dev

然后：

    $ sudo ln -s /usr/lib/`uname -i`-linux-gnu/libfreetype.so /usr/lib/
    $ sudo ln -s /usr/lib/`uname -i`-linux-gnu/libjpeg.so /usr/lib/
    $ sudo ln -s /usr/lib/`uname -i`-linux-gnu/libz.so /usr/lib/

最后：

    $ pip install PIL

一般这样就可以了。完成！^^

----------
但是如果出现：

    gcc -pthread -fno-strict-aliasing -DNDEBUG -g -fwrapv -O2 -Wall -Wstrict-prototypes -fPIC -IlibImaging -I/usr/include -I/usr/local/include -I/usr/include/python2.6 -c _imaging.c -o build/temp.linux-i686-2.6/_imaging.o
    _imaging.c:75:20: error: Python.h: 没有那个文件或目录
    In file included from libImaging/Imaging.h:14,from _imaging.c:77:

错误信息，最后的显示结果为：
    command 'gcc' failed with exit status 1

就还需要做下面的事情。

----------

**1.安装python-all-dev**

**2.然后执行PIL文件下的setup.py**

----------
参见此君的博文：

<http://blog.sina.com.cn/s/blog_5cd78a5d0101jcza.html>

>*为了找到缺什么，我们运行*
>   *apt-cache search python | grep dev*h
>*没有找到python的C语言开发包。*
>*安装python-all-dev,于是然后执行PIL文件下的setup.py，安装成功。*

--------------

## Pygame的安装

如果输入

    $ pip intsall Pygame

会出现下面的错误

    No such file or directory: '/home/×××××/build/Pygame/setup.py'

使用就可以

    $ pip install http://www.pygame.org/ftp/pygame-1.9.1release.tar.gz

可以详细看关于这个Bug的issue讨论：<https://bitbucket.org/pygame/pygame/issue/59/pygame-has-no-pypi-page-and-cant-be>

## 2.有用的参考资料：

- 官方文档 <http://effbot.org/imagingbook/>
- 数字图像处理PIL的一个实例 <http://blog.sina.com.cn/s/blog_4b5039210100f6ki.html>
- 一篇关于如何成为Python高手的文章，是从 How to become a proficient Python programmer 这篇文章翻译而来的 <http://www.zhizhihu.com/html/y2011/3093.html>
- 把图片的数据变换成数组 <http://blog.csdn.net/zhengkarl/article/details/5731317>
- Python图形图像处理库的介绍之Image模块 <http://tojaoomy.iteye.com/blog/1413810>
- 微博关键字图片生成算法 <http://ued.ctrip.com/blog/?p=2471>
- Matplotlib的官方文档 <http://matplotlib.sourceforge.net/Matplotlib.pdf>

---

## 3.References:

- <http://askubuntu.com/questions/156484/how-do-i-install-python-imaging-library-pil>
- <http://www.sandersnewmedia.com/why/2012/04/16/installing-pil-virtualenv-ubuntu-1204-precise-pangolin/>
- <http://blog.sina.com.cn/s/blog_5cd78a5d0101jcza.html>
