---
title: Hexo使用记录
date: 2019-07-14 19:15:20
tags:
---

# Hexo使用记录

## Hexo简介

官网链接：https://hexo.io/zh-cn/docs/

生成静态页面，可以部署在github.io或者gitee上，实现搭建自己的博客。

相对于普通的博客网站，比如cnblogs csdn等，一来数据完全自己所有，可以随意迁移备份，二来不受网站控制影像，即使倒闭了，将数据部署到新的网站上完全一样。

缺点是没有交互，不过单纯记录发表一些东西足够用了。

## 安装

需要已经安装git  nodejs

安装过程很简单，打开命令行，一条命令：

```powershell
npm install -g hexo-cli
```



## 使用

首先创建初始目录：

```
hexo init <folder>  //比如 hexo init .
```

在指定目录初始化，然后会自动生成很多目录文件。

其中_config.yml是配置文件，source目录存放用户资源，所写的文章在\_posts目录下。

如果要写一篇文章，只需要hexo new  [layout]<title> ，不过刚接触，没使用layout，只是

```
hexo new 文章名
```

来添加新文章。文章对应\_posts目录下的一个md文件，使用markdown语法进行编辑即可，Typora用起来挺不错，尤其是打印机模式和专注模式。

文章写完可以通过 

```
hexo g
```

来生成，然后通过

```
hexo server -p 80
```

在本地查看，如果直接hexo s，默认端口是4000。

确认无误后可以部署到server上，比如github.io，

```
hexo d
```

进行部署，然后github.io下就可以看到了。

当然前提是需要在_config.yml中进行设置，主要是在最后面的deploy项目

 ```
deploy:
  type: git 
  repo: XXXXXX
  branch: master
 ```

需要注意的是，：和值之间要有一个空格。，repo里面填写github.io对应的git即可。



## 其他

github网络会有一些问题，本来是部署在gitee上的，不过可能是用到了一些墙外的资源，同样的内容，部署在github上的显示效果和在 本地一样，但是在gitee上就只是单纯的文本了，完全没了主题效果。好在目前够用，后面得想办法处理下，可能需要进行更换主题之类的操作。



## 更新

1 .gitee上也没有问题，需要创建和用户名完全一样的仓库，其他和GitHub一样。



2，update 2019年07月27日21:17:19

标签，通过Hexo new "title"创建新文档后，可以添加标签，分类管理文章。

使用方式为tags下输入，比如：

```
tags:
	- leetcode
```





##### update 2019年8月12日13:41:51

https://blog.csdn.net/xcantloadx/article/details/78296227

https://blog.csdn.net/burststar/article/details/45115905

下载博客后提示Local hexo not found in XXX，重新执行npm install即可。

或者修改.gitingore，取消忽略node_modules文件夹。



##### update 2019年8月18日19:17:30

```
date: 2019-07-14 19:15:20
tags:
	- XXX
```

可以按照上面所示添加标签，对博客进行分类。

可以添加多个标签。



