---

title: Hexo入门
date: 2024-08-08 22:05:54

tags: 
---

---

<!-- more -->

创建新文章

```
hexo n
```

清除掉旧的数据

```
hexo clean
```

生成新的页面

```
hexo g
```

本地预览

```
hexo s
```

部署到Github

```
hexo d
```



#### 所有博客显示未命名(untitled)

刚开始写的博客都是通过自己创建MarkDown文件导入到post中的，所以自然没有前缀，解决方式如下即可

```
#以如下格式输入相应的字段
---
title: hexo入门
date: 2024-08-08 22:05:54
tags:
---
#####正文内容
```

hexo在generate的时候会自动索引当前文件的标题、时间和tags等

#### 博客首页折叠

部署后发现首页的文章都是全部预览的，但别人的都是有个**阅读全文**，其实在MD文件中添加一行代码就搞定了

```
#####首页显示内容
<!-- more -->
#####隐藏内容
```



#### hexo部署后，CNAME会被自动删除

将需要上传至github的内容放在source文件夹，例如CNAME、favicon.ico、images等



#### hexo创建新文章

```
$ hexo new "your file name"
```

该命令会在source/_post/目录下生成一个your-file-name.md文件，文件会默认附带标题、时间和tag/category等开头，如下：

```
---
title: hexo搭建博客的几个小问题
date: 2024-08-08 22:05:54
tags:
---
```

#### hexo创建新的分类

```
$ hexo new page "your page name"
```

此时需要在scaffolds/post.md文件中添加一行你的分类，例如：

```
---
title: {{ title }}
date: {{ date }}
tags:
categories: # 添加该行，新增的分类
---
```

#### hexo创建草稿

```
$ hexo new draft "your draft file name"
```

该命令会在source/下创建一个与**_post**对应的**_draft**文件夹，其中存放待编辑的草稿，而草稿不会影响正常的生成（hexo generate）部署（hexo deploy）

#### hexo草稿预览

如果需要预览草稿可以使用下面的命令进行预览

```
$ hexo server --draft
```

#### hexo草稿发布

草稿编写完成后需要生成到public中并且进行部署，使用如下命令即可：

```
$ hexo publish "your draft file name"
```
