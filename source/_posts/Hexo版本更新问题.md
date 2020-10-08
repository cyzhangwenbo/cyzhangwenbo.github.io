---
title: Hexo版本更新问题
categories:
  - Hexo
  - Hexo常见问题
tags:
  - Hexo
abbrlink: 1a9d37da
date: 2020-10-08 20:42:24
---

#  Hexo版本更新问题

> 由于Hexo版本较低，可能导致某些插件无法使用，因此多方搜索查询实践后记录一下。

hexo版本和插件以及依赖关系均存放在仓库根目录下的`package.json`中，因此需先修改文件中的版本信息然后进行对应的更新。

----

1. 打开仓库根目录下的`package.json`文件
2. 修改文件夹下的`dependencies`下的`hexo`属性为对应的版本号 (**具体更新内容及版本信息见[Github/hexojs](https://github.com/hexojs/hexo)下的`Releases`**)

![](https://cdn.jsdelivr.net/gh/cyzhangwenbo/image/question/hexogengxin.png)

> 注意版本号前面要带符号`^`

3. 打开根目录下的`Git bash`，终端输入`npm install`，等待、Hexo更新完成
4. 终端输入`hexo -v`查看版本号是否为所更新的版本号判断是否更新成功。

---

*Hexo版本更新其他问题待更新*…