---
title: hexo常用命令
date: 2018-06-02 16:28:05
tags: hexo
---

### 命令简写

* 新建文章： `hexo n '文章名'`  >>>  `hexo new '文章名'`
* 发布草稿： `hexo p '文章名'` >>> `hexo publish '文章名'`
* 生成静态文件： `hexo g`  >>>  `hexo generate`
* 启动本地服务： `hexo s` >>> `hexo server`
* 部署发布： `hexo d` >>> `hexo deploy`

<!--more-->
### 常用命令

1. 更改端口： `hexo s -p 3333`
2. 自定义ip： `hexo s -i 192.168.1.1`
3. 清除缓存： `hexo clean`
4. 生成静态文件后发布： `hexo s -g`
5. 新建草稿： `hexo n draft '草稿名'`

### 设置文章摘要

>这是摘要部分
>`<!--more-->`
>这是余下全文

### 预览草稿

1. 修改配置文件：`render_drafts: true`
2. 启动服务添加参数：`hexo s --drafts`
