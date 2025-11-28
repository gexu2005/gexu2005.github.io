# Blog

## 将更新完的博客push到github上

```
1.git add .
2.git commit 
3.esc
4.shift + :
5.输入wq
6.git push origin master
```

## 将代码push到新创建的仓库中

> 1. 进入你的项目目录（你已经在里面了，可以直接执行）
>
>    > cd ~/code/Agent/Auto01_agent
>    >
> 2. 初始化 git 仓库（这一步会创建 .git 文件夹）
>
>    > git init
>    >
> 3. 添加所有文件到暂存区
>
>    > git add .
>    >
> 4. 提交到本地仓库
>
>    > git commit -m "first commit"
>    >
> 5. 把 Gitee 仓库添加为远程仓库（这里取个名字叫 origin）
>
>    > === 方式A：用 HTTPS ===
>    >
>    > git remote add origin https://gitee.com/你的用户名/你的仓库名.git
>    >
> 7. 把本地 master 分支推送到 Gitee（第一次推送需要加 -u 建立关联）
>
>    > git branch -M main          # Gitee 新仓库默认主分支是 main，而不是 master（可省略如果已经是 main）
>    > git push -u origin main
>    >
