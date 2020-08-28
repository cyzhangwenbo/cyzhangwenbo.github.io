---
title: Git 将本地文件与Github仓库关联
tags:
  - Git
categories:
  - GitHub
  - 总结
abbrlink: bf3509b4
date: 2020-06-02 23:48:50
---

## 建立步骤

第1步：建立本地 git 仓库，cd 到你的本地项目根目录下，执行 git init 命令

```markdown
cd 本地工程根目录
git init  //这个目录就变成了git可以管理的仓库
```

第2步：将本地项目工作区的所有文件添加到暂存区。小数点 “.” ，意为添加文件夹下的所有文件；也可以将 “.” 换成具体的文件名，如果想添加项目中的指定文件，那就把 “.” 改为指定文件名即可

```
git add .
```

> `git add -A` 和 `git add . ` `git add -u` 在功能上看似很相近，但还是存在一点差别
>
> - **git add .** ：他会监控工作区的状态树，使用它会把工作时的**所有变化提交**到暂存区，包括文件内容修改(modified)以及新文件(new)，但不包括被删除的文件
>
> - **git add -u** ：他仅监控**已经被add的文件**（即tracked file），他会将被修改的文件提交到暂存区。add -u 不会提交新文件（untracked file）。（git add --update的缩写)
>
> - **git add -A** ：是上面两个功能的合集（git add --all的缩写）
>
>   总结下来就是：`git add -A`  提交所有变化
>
>   `git add -u`  提交被修改(modified)和被删除(deleted)文件，不包括新文件(new)
>
>   `git add . ` 提交新文件(new)和被修改(modified)文件，不包括被删除(deleted)文件

第3步：将暂存区的文件提交到本地仓库

```bash
git commit -m "注释说明"
```

第4步：在 github 或者 gitlab 上创建新的repository ,  然后复制一下远程仓库的https地址

第5步：将本地代码仓库关联到 github 上

```csharp
git remote add origin https://github.com/cyzhangwenbo/JsAndObjc.git
```

> 如果输入上述代吗出现错误提示`fatal:remote origin already exists` 
>
> 就输入`git remote rm origin`
>
> 再输入 
>
> ```
> git remote add origin https://github.com/cyzhangwenbo/JsAndObjc.git
> ```
>
> 一般就不会报错了

第6步：将代码由本地仓库上传到 github 远程仓库，依次执行下列语句

1. 获取远程库与本地同步合并（如果远程库不为空必须做这一步，否则后面的提交会失败）

   ```cpp
   git pull --rebase origin master  //不加这句可能报错，原因是 github 中的 README.md 文件不在本地仓库中
   //可以通过该命令进行代码合并
   ```

2. 把当前分支 master 推送到远程，执行此命令后有可能会让输入用户名、密码

   ```cpp
   git push -u origin master  //执行完之后如果无错误就上传成功了，需要提示的是这里的 master 是 github 默认的分支，
   //如果你本地的当前分支不是 master，就用git checkout master命令切换到master分支，
   //如果你想用本地当前分支上传代码，则把第6步的命令里的 master 切换成你的当前分支名即可。
   ```

至此，操作完成

如何解决failed to push some refs to git

> 在使用 git 对源代码进行push到 GitHub 时可能会出错，信息如下
>
> 此时很多人会尝试下面的命令把当前分支代码上传到master分支上
>
> `git push -u origin master`
>
> 但依然没能解决问题
>
> 出现错误的主要原因是 github 中的 README.md 文件不在本地代码目录中
>
> 可以通过如下命内令进行代码合并
> `git pull --rebase origin master`
>
> 执行上面代码后容可以看到本地代码库中多了README.md文件

