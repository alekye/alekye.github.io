title: 使用Hexo和Github搭建个人站点
author: Alek Ye
date: 2018-12-20 11:49:21
tags:
---
首先要有自己的Github账号，我的账号访问地址：https://github.com/alekye，<!--more-->

###### 创建代码仓库

在Github上创建代码仓库 alekye.github.io，命名必须是 账号+.github.io，只有这样才可以通过http协议访问。

###### 创建分支hexo

创建分支的目的是为了让站点的html文件和工程代码分离，把Hexo项目放在hexo分支，html文件发布到master分支。把代码仓库clone到本地，并且切换到hexo分支，代码如下

``` bash
$git clone https://github.com/alekye/alekye.github.io.git
$cd alekye.github.io.git
$git checkout -b hexo origin/hexo
```

###### 创建hexo项目

由于创建hexo项目需要指定一个空目录，所以在临时目录中创建，然后再拷贝到代码仓库中。

``` bash
$cd ~/temp
$hexo init MyBlog
```

添加插件 [hexo-admin](https://github.com/jaredly/hexo-admin) 和 [hexo-deployer-git](https://github.com/hexojs/hexo-deployer-git)

hexo-admin 用来管理站点内容的发布， hexo-deployer-git 用来发布到Github。

``` bash
$npm install hexo-admin --save
$npm install hexo-deployer-git --save
```

###### 修改配置文件

修改根目录下的配置文件 _config.yml 的 deploy 如下：

``` 
deploy:
  type: git
  repo: https://github.com/alekye/alekye.github.io.git
  branch: master
```

###### 发布站点

``` bash
$hexo deploy
```

###### 提交项目代码

``` bash
$git push origin hexo
```