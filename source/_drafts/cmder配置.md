---
title: cmder配置
tags: cmder
---

### 配置环境变量

* 添加系统环境变量
> 变量名：CMDER_HOME
  变量值：cmder的绝对路径(G:\cmder)
* 系统path环境变量添加值：%CMDER_HOME%

<!-- more -->

### 添加到右键菜单

> 需管理员权限的cmd

输入Cmder.exe /REGISTER ALL

### 打开一个管理员权限的终端

1. cmder中快捷键Ctrl + t
2. 参照下图勾选
> ![](2018-6-2-01.png)

### 设置bash为默认开启
1. cmder中快捷键win + alt + p
2. 参照下图选择
> ![](2018-6-2-02.png)

### 中文乱码

操作：settings >>> startup >>> environment，添加以下内容：
> set LANG=zh_CN.UTF-8
> set LC_ALL=zh_CN.utf8

如下图：
> ![](2018-6-2-03.png)

* 2：搜索视窗出现过的关键字

* 3：

### 常用功能

![](2018-6-2-04.png)




### 常用快捷键

* tab，路径补全
* ctrl + t，打开新页签
* ctrl + w，关闭页签
* crtl + tab，切换页签
* alt + f4，关闭所有页签
* alt + shift + 1，开启cmd.exe
* alt + shift + 2，开启powershell.exe
* alt + shift + 3，开启powershell.exe（管理员权限）
* ctrl + n，切换到第n个页签
* alt + enter，全屏模式
* ctrl + r，历史命令搜索

## 参考文章

![https://segmentfault.com/a/1190000011361877#articleHeader5](https://segmentfault.com/a/1190000011361877#articleHeader5)

![汉化sublime](https://blog.csdn.net/heyangyi_19940703/article/details/51869502)



















