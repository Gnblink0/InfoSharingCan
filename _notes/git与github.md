---
---

Git 是目前世界上最先进的**分布式版本控制系统**。

### Git 基本工作流程
![](https://picture-guan.oss-cn-hangzhou.aliyuncs.com/20220815021352.png)

主要涉及到四个关键点：
1.  工作区：本地电脑存放项目文件的地方，比如 learnGitProject 文件夹；
2.  暂存区（Index/Stage）：在使用 git 管理项目文件的时候，其本地的项目文件会多出一个.git 的文件夹，将这个.git 文件夹称之为版本库。其中.git 文件夹中包含了两个部分，一个是暂存区（Index 或者 Stage）,顾名思义就是暂时存放文件的地方，通常使用 add 命令将工作区的文件添加到暂存区里；
3.  本地仓库：.git 文件夹里还包括 git 自动创建的 master 分支，并且将 HEAD 指针指向 master 分支。使用 commit 命令可以将暂存区中的文件添加到本地仓库中；
4.  远程仓库：不是在本地仓库中，项目代码在远程 git 服务器上，比如项目放在 github 上，就是一个远程仓库，通常使用 clone 命令将远程仓库拷贝到本地仓库中，开发后推送到远程仓库中即可；


## git 与 github

Git 和 GitHub 类网站（如 Github、Gitee 等）的区别：

Git 是一款本地运行的软件，如 QQ。Github 或 Gitee 是一个在线网站，如腾讯网。

运行 Git 后有形成一系列版本文件，你可以将其提交到 Github 或 Gitee 等网站（类似于仓库）。

想用 [GitHub](https://github.com/)？我的建议是：==下载一个 GitHub Desktop 解千愁！ ！ ！==

Github 日常依然是使用[[命令行]]操作，但是 Desktop提供了图形化界面，非常适合新手入门和操作

## 资料

[Git 和 GitHub - 学习 Web 开发丨MDN](https://developer.mozilla.org/zh-CN/docs/Learn/Tools_and_testing/GitHub)

[Git零基础入门到实战详解_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1sJ411D7xN?spm_id_from=333.999.0.0&vd_source=edb3b9d2edcf09617c0c07c0499efd40)

[主页 // 像 (a) Git 一样思考](http://think-like-a-git.net/)

[git 简明指南](https://www.runoob.com/manual/git-guide/)

[Git基本语句](https://ufkqhva2uf.feishu.cn/mindnotes/bmncnWRCctHYfPd4Wi6I4jnGzBe)

[Eished/git_notes: web前端工程师 -前后端交互技术 Git和GitHub详解（完） ----学习笔记](https://github.com/Eished/git_notes)
