# BlogProject

#### 介绍

hexo 博客项目，原始的文件，用来做同步

#### 软件架构

hexo+page+其他


#### 安装教程

1. 安装HEXO
2. markdown编写博客
3. 预览发布查看

#### 使用说明

1. git clone XXX
2. hexo
3. 本地查看

# FAQ

1 如何创建文章？

hexo n(new)  [模板，如post、draft等]  【文章名称】

如 hexo n Test

之后source里面生成对应的md文档，进行编辑即可。



2 Hexo如何修改主题？

https://zhuanlan.zhihu.com/p/137338730

a 下载主题

b 修改config.yml文件



3 hexo如何发布草稿

a hexo n draft XXX 在draft目录下创建源码，heox s后看不到

b hexo publish XXX即可将draft发布，实际上是从_drafts目录移到了 _posts目录下



