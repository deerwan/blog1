---
title: 如何在HEXO中插入图片
date: 2024-10-02 21:45:24

tags: "HEXO"


---

---

<!-- more -->

在 Hexo 中插入图片有多种方式，具体方法取决于你使用的 Hexo 插件和图片的存储位置。以下是几种常见的方式：

1. 使用相对路径插入本地图片
在 Hexo 的 source 文件夹下，创建一个文件夹（如 images），并将图片放入其中，然后使用 Markdown 语法插入图片：



```
![图片描述，可为空](images/your-image.png)
```



2. 使用 hexo-asset-image 插件插入图片
如果希望图片和文章内容一起管理，可以使用 hexo-asset-image 插件，使图片放在每篇文章的同名文件夹中。

安装插件
在你的 Hexo 博客目录中运行：

```
npm install hexo-asset-image --save
```

插入图片
在 source/_posts 文件夹中，找到你的 Markdown 文件（如 post-title.md）。

在同一目录下创建一个同名文件夹 post-title/，然后将图片放入该文件夹。

使用以下格式插入图片：

```

![alt text](post-title/image.png)
```


3. 使用 URL 链接插入外部图片
如果你的图片在外部服务器或图床上，可以直接使用 URL 插入：

```
![alt text](https://example.com/path-to-image.png)
```


4. 使用 hexo-tag-image 插件
hexo-tag-image 插件提供了更多自定义选项，比如指定图片的宽度、高度、对齐方式等。

安装插件

```
npm install hexo-tag-image --save
```

插入图片
使用如下语法：

```
{% image [class names] /path/to/image [width] [height] [title text [alt text]] %}
```

例如：

```
{% image center https://example.com/image.png 600 400 "Title text" "Alt text" %}
```

每种方法适用于不同的场景，你可以根据需求选择合适的方法。





