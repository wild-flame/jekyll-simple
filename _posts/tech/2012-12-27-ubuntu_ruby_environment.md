---
layout: post
title: ［Ruby］Ubuntu(12.04)下Ruby的安装与配置
author: Taffy 
category: tech
description: linux下安装Ruby有很多方法，不过这里推荐一种使用用 RVM (Ruby Version Manage) 来安装的方法。
---

首先，安装Ruby有很多方法，不过还是这里推荐用 [RVM (Ruby Version Manage)][RVM] 来安装

可能您已经使用过apt安装RVM，或者用ubuntu软件中心，不过为了避免以后出现莫名奇妙的错误，最好还是自己重新安装一下。因此首先清除可能已经的安装好的RVM管理器。
    
    $ sudo apt-get --purge remove ruby-rvm 
    $ sudo rm -rf /usr/share/ruby-rvm /etc/rvmrc /etc/profile.d/rvm.sh 

之后重新启动终端并检查环境变量（关于环境变量，）：

如果有显示，试一试重新开启终端（Terminal），如果仍有可以尝试重启计算机。

安装 RVM:

    $ t.rvm.io | bash -s -- --auto-dotfiles 

*其中curl是利用URL语法在命令行方式下工作的文件传输工具。*

安装完以后最后能看到这样一段话：

    # To start using RVM you need to run `source /home/***/.rvm/scripts/rvm`
    # in all your open shell windows, in rare cases you need to reopen all shell windows.

故输入

    source /home/***/.rvm/scripts/rvm 

其中***指的是你自己的名字

*source命令用法：`source FileName` 作用:在当前bash环境下读取并执行FileName中的命令。 注：该命令通常用命令“.”来替代。如 `source /etc/profile` 与 `. /etc/profile`是等效的。 注意：source命令与shell scripts的区别是，source在当前bash环境下执行命令，而scripts是启动一个子shell来执行命令。这样如果把设置环境变量（或alias等等）的命令写进scripts中，就只会影响子shell,无法改变当前的BASH,所以通过文件（命令列）设置环境变量时，要用source 命令。*

关于RVM的详细实用安装与使用方法参见：[Installing RVM][]。安装好RVM后就可以使用它来安装Ruby了。

输入：

    $ rvm list known 
    $ rvm install 1.9.2 

接下来：使用刚刚安装的Ruby

    $ rvm use 1.9.2 

检查是否工作正常：

    $ ruby -v 

显示 `ruby 1.9.2p320 (2012-04-20 revision 35421) [i686-linux]`

    $ which ruby 

显示 `/home/***/.rvm/rubies/ruby-1.9.2-p320/bin/ruby`

[Installing RVM]: https://rvm.io/rvm/install/
[RVM]: http://ruby-china.org/wiki/rvm-guide

<script type="text/javascript">
     $('pre').addClass('prettyprint linenums')
</script>

<script src="https://google-code-prettify.googlecode.com/svn/loader/run_prettify.js?skin=sunburst"></script>