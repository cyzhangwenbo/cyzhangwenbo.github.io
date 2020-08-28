---
title: GitHub+jsDelivr+PicGo图床
tags:
  - 图床
  - 工具
categories:
  - GitHub
  - 图床工具
abbrlink: a66e99c0
date: 2020-06-18 16:35:22
---

Github图床是个自定义存储图片的不错选择，利用jsDelivr CDN加速访问（免费开源CDN解决方案），PicGo工具一键上传，简单高效，且GitHub和jsDelivr都是大厂，不必担心跑路问题和容量问题。（国内服务器搭建图床容量多费用就高），该方案是目前免费图床的最佳方案！

方法如下：

## 新建GitHub仓库

登录 / 注册GitHub，新建一个仓库(Repositories)，填写好正确的仓库名和仓库描述(选填)，并根据个人需求是否自动生成README.md文件,之后点击创建。

![](https://cdn.jsdelivr.net/gh/cyzhangwenbo/image/learn/tuchuang1.png)

## 生成一个Token

在主页依次选择

> 【Settings】→【Developer settings】→【Personal access tokens】→【Generate new token】，并写好描述(一般仓库名写一样即可)

勾选【repo】，然后点击【Generate token】生成一个Token，复制这个Token并进行保存(仅显示这一次)

![](https://cdn.jsdelivr.net/gh/cyzhangwenbo/image/learn/tuchuang2.png)

![](https://cdn.jsdelivr.net/gh/cyzhangwenbo/image/learn/tuchuang3.png)

## 下载配置PicGo

前往[PicGo](https://github.com/Molunerfinn/picgo/releases)

下载后安装并运行开始配置

![](https://cdn.jsdelivr.net/gh/cyzhangwenbo/image/learn/tuchuang4.png)

> 1. **设定仓库名：**按照 `用户名/图床仓库名 ` 的格式填写
> 2. **设定分支名：**`master `(如果仓库有其他分支或想要保存其他分支，可以写已有分支)
> 3. **设定Token：**粘贴之前生成的 `Token`
> 4. **指定存储路径：**填写想要储存的路径，如`learn/`，这样就会在仓库下创建一个名为` learn` 的文件夹，图片将会储存在此文件夹中 (尽量避免输入中文，由于要作为地址，不同浏览器设置 *Unicode* 转码可能会出错 )
> 5. **设定自定义域名：**它的作用是，在图片上传后，PicGo 会按照`自定义域名+储存路径+上传的图片名`的方式生成访问链接，并放到粘贴板上，因为我们要使用 jsDelivr 加速访问，所以可以设置为`https://cdn.jsdelivr.net/gh/用户名/图床仓库名 ` (命名规则)，上传完毕后，我们就可以通过 `https://cdn.jsdelivr.net/gh/用户名/图床仓库名/图片路径 ` 加速访问我们的图片了，比如上图的图片链接为： `https://cdn.jsdelivr.net/gh/cyzhangwenbo/image/learn/tuchuang4.png` 

设置完成后，点击确定重新启动PicGo，点击**上传区**进行图片上传，上传成功后在**相册区**可以进行已上传图片预览，打开浏览器访问上传图片对应的URL地址，访问成功即完成配置。

## 创作使用

配置好PicGo后，我们就可以进行高效创作了，将图片拖拽到上传区，将会自动上传并复制访问链接，将链接粘贴到博文中就行了，访问速度杠杠的，此外PicGo还有相册功能，可以对已上传的图片进行删除，修改链接等快捷操作，PicGo还可以生成不同格式的链接、支持批量上传、快捷键上传、自定义链接格式、上传前重命名等，更多功能自己去探索吧



文章参考于[TRHX’S BLOG Github+jsDelivr+PicGo 打造稳定快速、高效免费图床](https://www.itrhx.com/2019/08/01/A27-image-hosting/)