---
title: algolia实现第三方搜索功能
tags:
  - 技术总结
  - 学习
  - 搜索功能
categories:
  - GitHub
  - 个人网站
  - 搜索功能
abbrlink: e7c68ffd
date: 2020-07-07 14:17:54
---

[Algolia](https://www.algolia.com/) 是一家第三方搜索服务商，有免费服务可提供搜索功能。它使用外部托管的搜索引擎为客户的网站提供网络搜索服务。产品只需索引客户的网站里的内容，因此搜索任务要简单得多。

# 注册

首先打开`Algolia` 官方网站注册账号

![](https://cdn.jsdelivr.net/gh/cyzhangwenbo/image/learn/algolia/sousuo1.png)

> 输入邮箱注册时会向邮箱发送确认链接，进入注册即可。如果邮箱接收不到邮件，那最好选用第三方登录，GitHub、Google账户均可

# 配置

注册成功后登录账户，填入 `NEW Index` 

![](https://cdn.jsdelivr.net/gh/cyzhangwenbo/image/learn/algolia/sousuo2.png)

> 输入便于记忆的名称即可，如`my_blog`
>
> 注：该名称一定要记住，后续`Hexo/_config.yml`配置需要用到

点击侧边栏进入 `API Keys` 选项卡,可以看到如下界面

![](https://cdn.jsdelivr.net/gh/cyzhangwenbo/image/learn/algolia/sousuo3.png)

> 记录如图中的 `Application ID`、`Search-Only API Key`、`Admin API Key` 三个字段的值用于后续配置

# 使用

首先打开站点文件根目录使用 Git Bash 命令执行 `npm install --save hexo-algolia` 进行 `algolia` 的安装

安装完毕后，打开站点根目录 Hexo 的配置文件`_config.yml`(注意和 Hexo 下其他主题的`_config.yml`文件进行区分)，在配置文件中输入如下配置字段：

```yml
algolia:
  applicationID: # 你的APP ID
  apiKey:  # 你的API Key
  indexName: # New index 的ID
  chunkSize: 5000 # 默认即可，不用修改
```

> `_config.yml`配置中分别填入对应字段的值，填写完成后保存并关闭

再打开使用的 Hexo 主题下的配置文件 `_config.yml` 输入如下字段：

```yaml
algolia_search:
  enable: true
  src: /js/search/algolia-search.js
  hits:
    per_page: 10 # the number of search results per page
```

> 这种配置仅限于基于 Hexo 的 Yun 主题，其他主题配置与之类似，目的是开启`algolia 搜索`功能，具体查看对应主题的文档即可

打开 Git Bish 执行如下命令：

```shell
export HEXO_ALGOLIA_INDEXING_KEY= #输入配置中的 Admin API Key 字段的值
hexo algolia
```

执行完毕后稍等片刻，若没有报错成功配置完成，则分别执行` hexo clean` `hexo g` `hexo s` 命令后打开本地站点验证是否成功配置了`algolia`

![](https://cdn.jsdelivr.net/gh/cyzhangwenbo/image/learn/algolia/sousuo4.png)

> 成功配置`algolia`后，在站点搜索界面的开发者选项模式下可以看到 `js/search` 下有`algolia-search.js`文件被加载



所有步骤完成后即可畅快体验快而精准的搜索功能啦！

**注：`algolia` 的免费版有每日的搜索次数上限呦，若有较大的搜索条目需求应升级付费项目或更换搜索方式！**