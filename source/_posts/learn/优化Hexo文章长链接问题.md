---
title: 优化Hexo文章长链接问题
abbrlink: ae0ee4bd
date: 2020-07-06 22:04:19
tags:
  - Hexo
  - 技术问题
categories:
  - Hexo
  - 学习
---

基于Hexo主题下的博客，在生成静态网页时文章内会在页脚`permalink`生成长链接如下

![](https://cdn.jsdelivr.net/gh/cyzhangwenbo/image/learn/changlianjie.png)

需要利用 [hexo-abbrlink](https://github.com/rozbo/hexo-abbrlink) 插件解决生成短链接

> 1. 在文件目录下 Git 命令执行 `npm install hexo-abbrlink --save` 安装插件
>
> 2. 在 `hexo/_config.yml` 找到 `permalink: ` 字段相关代码进行修改：
>
> 将 hexo 自带如下字段屏蔽掉
>
> ```yaml
> permalink: :year/:month/:day/:title/
> permalink_defaults:
> ```
>
> 再添加如下字段
>
> ```yaml
> # URL
> ## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
> url: http://yoursite.com
> root: /
> # permalink: :year/:month/:day/:title/  # 旧的注释掉
> # permalink_defaults:                   # 旧的注释掉
> permalink: posts/:abbrlink/
> abbrlink:
>   alg: crc32  #support crc16(default) and crc32 （算法 crc16(default) and crc32，默认为crc16）
>   rep: hex    #support dec(default) and hex （十进制和十六进制，默认为十进制）
>   drafts: false #(true)Process draft,(false)Do not process draft
>   # Generate categories from directory-tree
>   # depth: the max_depth of directory-tree you want to generate, should > 0
>   auto_category:
>      enable: false                      #默认为 true， 手改改为 false
>      depth: 
> ```

修改完毕后保存，在文件目录下的 Git 命令依次执行 `hexo clean ` `hexo g` `hexo s`，打开`http://localhost:4000/` 进行预览文章尾部的 `permalink` 链接是否已经生成新的短链接，新的链接样式如下：

![](https://cdn.jsdelivr.net/gh/cyzhangwenbo/image/learn/duanlianjie.png)

这种短链接地址会在 Git 进行 `hexo g` 生成静态网页时自动的在对应的 MarkDown 文件中的头部添加`abbrlink:序列号` 字段，该字段便成为文章链接地址 URL 的一部分

**注意：在基于 Hexo 的 Yun 主题中，修改 `auto_category:` 字段下的 `enable` 为 `true`，可能会导致文章分类或归档出现问题！**

