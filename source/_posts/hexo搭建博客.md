---
title: '在github上搭建hexo博客'
date: 2018-03-19 21:42:51
tags: hexo
---

##### 1.配置环境

node：8.10.0
npm：5.7.1
hexo: 3.6.0

<!-- more -->

##### 2.github上创建项目

> 创建一个仓库
![创建一个仓库](2018-3-19-001.png)

> 给仓库配置名字并创建
![给仓库配置名字并创建](2018-3-19-002.png)

> 进入设置选项页面查看是否成功开启ph-pages功能
![进入设置选项页面查看是否成功开启ph-pages功能](2018-3-19-003.png)

> 下图表示成功开启
![Github Pages中显示your site is published at https://nsnds.github.io/表示成功开启](2018-3-19-004.png)

##### 3.创建本地博客

新建blog文件夹(文件名随便取)
进入blog文件夹
命令行执行hexo init，初始化hexo
命令行执行hexo g，生成静态文件
命令行执行hexo s，创建本地服务进行调试，[http://localhost:4000/](http://localhost:4000/)就能进行访问

##### 4.关联github

若没有配置好github的ssh key，则需进行以下

```
git config --global user.name "你的用户名"

git config --global user.eamil "你的邮箱"

# 进入.shh文件夹
cd ~/.ssh

# 生成id_rsa.pub
ssh-keygen -t rsa -C "你的邮箱"
```

然后在github上添加ssh

![进入设置页面](2018-3-19-005.png)
![选择添加ssh](2018-3-19-006.png)
![填写](2018-3-19-007.png)

最后验证是否添加成功
```
ssh -T git@github.com

# 若是Hi 你的用户名则表示成功

# 失败的话，对照以下步骤

ssh-add -D

rm -r ~/.ssh

ssh-keygen -t rsa -C "你的邮箱"

# ...接下来是正常操作
```

若已配置好ssh key，可以直接进行配置blog/\_config.yml
```
deploy:
  type: git
  repository: git@github.com:nsnds/nsnds.github.io.git
  branch: master
```
repository的值就是nsnds.github.io仓库的ssh
![nsnds.github.io的shh值](2018-3-19-008.png)

之后就可以部署到github了
```
# 生成静态模版
hexo g

# 部署到github
hexo d

# 生成及部署
hexo d -g

# 最后访问http://你的用户名.github.io，就可以看到部署好的博客了。
```

##### 5.配置主题

进入blog/themes，命令行运行

```
git clone https://github.com/litten/hexo-theme-yilia.git
```

配置blog文件夹下的_config.yml

```
# 修改theme的值
theme: hexo-theme-yilia

# 添加hexo-theme-yilia配置
jsonContent:
  meta: false
  pages: false
  posts:
    title: true
    date: true
    path: true
    text: false
    raw: false
    content: false
    slug: false
    updated: false
    comments: false
    link: false
    permalink: false
    excerpt: false
    categories: false
    tags: true
```

##### 6.[图片配置](https://blog.csdn.net/u010828718/article/details/55505631)

blog文件夹下下载插件
```
npm install https://github.com/CodeFalling/hexo-asset-image -- save
```

配置blog的_config.yml
```
post_asset_folder: true
```

新增一篇文章，就会新建一个文件名为文章名的文件夹，可以放入这篇文章使用到的图片。

##### 7.[配置网站图标](https://blog.csdn.net/ganzhilin520/article/details/79048034)

把图标文件放在当前主题文件夹(hexo-theme-yilia)/source/img

配置blog的_config.yml
```
# 网站图标
favicon: /img/header.JPG

# 博客头像
avatar: /img/header.JPG
```

8.[不同电脑利用分支进行管理博客的同步和上传](https://www.zhihu.com/question/21193762)

创建新分支(hexo分支)
![创建hexo分支](2018-3-19-009.png)

设置hexo为默认分支
![设置hexo为默认分支](2018-3-19-010.png)

本地_config.yml配置deploy为master

小乌龟提交nsnds.github.io的hexo分支代码

执行hexo g -d 提交静态网站文件到master分支


* 搭建博客参考于：[链接1](http://www.cnblogs.com/fengxiongZz/p/7707219.html)|[链接2](https://www.cnblogs.com/joy99/p/6985456.html)
