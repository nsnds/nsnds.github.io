---
title: npm的常见问题
date: 2018-03-29 09:23:37
tags: npm
---

### ~ or ^

~会匹配最近的小版本依赖包，如~1.2.3匹配所有1.2.x
^会匹配最新的大版本依赖包，如^1.2.3匹配所有1.x.x
既没有<font color="red">~</font>也没有<font color="red">^</font>的情况属于精准安装模块指定版本号，如：```"moment": "2.4.0"```。对应命令：```npm i --save-exact moment@2.4.0```

### package-lock.json

npm V5以上版本会有一个package.json文件，它记录安装模块的细节。确定当前安装包的依赖，以便后续重新安装的时候生成相同的依赖，忽略项目开发中有些依赖已经发生的更新。

<font color="red">V5.0.0</font>的坑：手动修改packsge.json中已有的模块，直接执行npm i不会安装新指定的版本，只能通过npm i XXX@YY更新。
<font>V5.4.2</font>后如果改了package.json且和lock不同，那么npm i会依照package中的版本号及语义含义下载包，并更新至lock。

### npm config

查看和管理npm的基础配置。```npm config ls -l```

```
# 查看是否设置了npm的代理
npm config get proxy
```

### 常见命令

查看安装的模块：npm ls

卸载模块：npm uninstall

更新模块：npm update

发布模块：npm publish

用户登录：npm adduser

查看模块版本：npm version

初始化项目：npm init

查看模块的注册信息：npm view

查看包的安装路径：npm root

查看某条命令的详细帮助：npm help

### dependencies or devDependencies or optionalDependencies

1. dependencies：生产环境的依赖包目录

使用```npm i --save moduel```命令安装的模块会注册到package.json中的dependencies。

而<font color="red">npm V5</font>开始不加--save也会把模块注册到dependencies中。

在生产环境只需要安装dependencies中的依赖时，执行```npm i -- production```即可。若配置了NODE_ENV环境变量为production，那么```npm i 只会安装dependencies中的依赖```。

2. devDependencies：开发环境的依赖包目录

使用```npm i --dev moduel```命令安装的模块会注册到package.json中的devDependencies。

3. optionalDependencies：可选依赖包目录

使用```npm i --save-optional module```安装的模块会注册到optionalDependencies中。

使用npm i --no-optional可以跳过可选包的安装。若有lock时，需要使用npm i --no-optional --no-package-lock才能跳过。

### npm cache

npm i的执行过程：

	发出npm i命令

	npm向registry查询模块压缩包的网址

	下载压缩包，存放在~/.npm(本地npm缓存)目录

	解压压缩包到当前项目的node_modules目录

实际上模块安装后，本地是有两份文件的。一是在~/.npm目录的压缩包，二是node_modules目录的解压后的代码。但运行npm i时只会检查node_modules，不检查~/.npm。若~/.npm中有模块的压缩包，但没有安装在node_modules中，npm依然会从远程仓库下载一次新的压缩包。

在npm V5中离线安装时不再尝试连接网络，而是降级尝试从缓存中读取，或直接失败。

查看本地npm缓存的完整路径：npm config get cache

对缓存进行垃圾回收：npm cache verify

### 更改npm的缓存、全局包文件夹

npm安装后，node安装目录下多出npm目录外，还会多出两个文件夹，分别在C:/User/Administrator/AppData/Roaming/npm-cache(缓存模块安装目录) & npm(全局模块安装目录)。

**更改npm-cache的目录**
```
# 获取npm-cache目录路径
npm config get cache

# 修改npm-cache目录地址
npm config set cache "D:\program Files\npm cache"
```

**更改npm的目录**
```
# 获取npm目录路径
npm config get prefix

# 修改npm目录地址
npm config set prefix "D:\program Files\npm-global"
```

修改完成后是无法使用已安装的全局包的，需要修改PATH环境变量。增加npm目录地址(D:/Program Files/npm-global)，再重启电脑。

### 更新本地包

获取更新包的信息：```npm outdated```

更新全部：npm update

更新部分(dependencies)：npm install grunt@1.0.1 --save

更新部分(devDependencies)：npm install grunt@1.0.1 --save-dev

验证：npm update 

### 更新全局包

获取更新包的信息：npm outdated -g --depth=0

全部更新：npm update -g

部分更新：npm install -g webpack

# 参考文章：
* [参考地址1](https://segmentfault.com/a/1190000013585195)

* [参考地址2](https://segmentfault.com/a/1190000006666168)