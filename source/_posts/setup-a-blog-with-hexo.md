---
title: 使用Hexo搭建个人Blog
date: 2016-01-30 19:40:37
tags:
    杂项
---


最近开始打算把Wordpress上的博客迁到Github上，google了一下，发现了Hexo这个博客系统。简单看了一下文档，还挺容易的，就糙、快、猛的干起来了。Hexo的文档虽然比较简洁，但对于Hexo新手来说，有些概念交代的太少了。所以还是决定稍微写一下，方便自己回忆以及需要的人熟悉Hexo。

<!-- more -->



安装依赖环境
---

依赖:
- node.js
- git
- hexo-cli package

官网上有[安装手册][1]，我就不做搬运工了。Hexo上手起来真的很快，感觉比jekyll，Octpress要更傻瓜。


初始化本地Blog目录
----

创建一个本地目录，作为Blog的根目录。用Hexo来初始化它。具体命令：

    $ mkdir Blog 
    $ cd Blog
    $ hexo init .
    $ npm install

初始化后会生成一些列文件，参见[文档][2]


眼见为实
----

到此为止，我们就先直观看一下Hexo搭建的Blog长什么样。

    $ cd Blog
    $ hexo server

用浏览器打开http://localhost:4000，即可看到当前Blog的样式，以及一篇名为"Hello World"的文章

就是这么简单!


使用Hexo的基本流程
-----

到此为止,就有一个可以写作的环境了，真的就是这么简单。一般日常的写作流程如下：

**1. 创建一篇博客**

    $ cd Blog
    $ hexo new post "the first blog"

新的博客文件会创建到Blog/source/_post/the-first-blog.md.

**2. 写作**

用vim/emacs/sublime/其他任何编辑器编写新创建的Markdown文件

**3. 本地测试**

    $ hexo server

用浏览器打开http://localhost:4000，即可看到自己的Blog，以及第一篇文章

**4. 将本地博客同步到服务器上**

这是写作的最后一步，同步上去之后，博客就可以被其他人看到了。

    $ hexo generate
    $ hexo deploy

当然，这个步骤目前是无法执行通过的，因为我们还缺少必要的配置。

配置Blog
-----

配置文件在Blog/_config.yml, 所有配置的项介绍看[这里][3]
这个配置文件里一般只需要修改这几个配置项就够了，其他配置很少会改动。
* title,subtitle,description,author,language
这些都是Blog的基本信息：标题，副标题，描述，作者，语言。
* url,root
Blog要使用的url，以及url中的路径。
* theme
Blog的主题，很多Hexo的使用者自己开发了不同的主题供大家使用。可以选择喜欢的主题并在这里配置即可。
* deploy
Blog最后要部署到github上时，需要设置github相关的参数。当然Hexo也支持部署到其他地方，如heroku等

这里我们要配置一下deploy相关的配置，修改_config.yml中deploy部分，形如：

    deploy:
        type: git
        repo: <github中repo的url>

然后,上面提到的部署命令就可以执行了。
注意，需要在github上提前创建该repo。

具体配置项的介绍可参见[文档][4]
        

选择不同的主题
----

默认的主题确实比较单一，Hexo主页上提供了不少[主题][5]可以使用。
点开每个主题，会有README文件介绍如何将其安装到Hexo环境，并对主题进行相应的配置。
一般来说，通用的流程是：

    $ git clone <git url of theme> Blog/theme/<theme name>
    $ 将Blog/_config.yml中theme的值设置为<theme name>
    $ 编辑Blog/theme/<theme name>/_config.yml 来修改主题配置项

很多主题在其配置项里还集成了评论，分享，数据统计功能，使得这个Blog更加完善。这里就不一一介绍了。请看每个主题的说明文档。



[1]: https://hexo.io/zh-cn/docs/index.html "安装手册"
[2]: https://hexo.io/zh-cn/docs/setup.html "初始化"
[3]: https://hexo.io/zh-cn/docs/configuration.html "配置项"
[4]: https://hexo.io/zh-cn/docs/deployment.html "部署"
[5]: https://hexo.io/themes/ "主题"
