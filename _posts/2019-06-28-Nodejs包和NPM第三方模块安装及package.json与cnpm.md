---
layout:     post
title:      Nodejs包和NPM第三方模块安装 package.json与cnpm知识点
subtitle:   了解 node周边生态
date:       2019-06-28
author:     XZ
header-img: img/post-bg-node.jpg
catalog: true
tags:
    - 前端
    - node
    - npm
    - 模块化
---

## 前言

Node.js 周边的生态非常强大，NPM（Node包管理）上有超过60万个模块，日下超过载量3亿次。但对新人和其它语言背景的开发者来说，开始了解node周边生态不是一件容易的事，在入门之前需要弄懂不少复杂的概念。废话不多说，来看看本次分享 都有哪些亮点吧!


## 一、Nodejs 包 和 Npm

>关键词：流行 好用 前端开发辅助工具

### Nodejs 包 

Nodejs中除了它自己提供的**核心模块**外，我们可以*自定义模块*，也可以使用第三方的模块。

Nodejs中**第三方模块**由包组成，可以通过包来对一组具有相互依赖关系的模块进行统一管理。

![](http://tva1.sinaimg.cn/large/0060lm7Tly1g4i09c8rpnj30fa08hq2z.jpg)

完全符合CommonJs规范的包目录一般包含如下这些文件。

- package.json :包描述文件。
- bin :用于存放可执行二进制文件的目录。
- lib :用于存放**JavaScript**代码的目录。
- doc :用于存放文档的目录。在NodeJs中通过NPM命令来下载第三方的模块（包）。

在NodeJs中通过NPM命令来下载第三方的模块（包）

<https://www.npmjs.com/package/silly-datetime>

    npm i silly-datetime –save
    var sd = require('silly-datetime');
    sd.format(new Date(), 'YYYY-MM-DD HH:mm');

### NPM 介绍 

npm是世界上*最大的开放源代码* 的生态系统。我们可以通过npm下载各种各样的包，这些源代码（包）我们可以在<https://www.npmjs.com>找到。

**npm是随同NodeJS一起安装的包管理工具，能解决NodeJS代码部署上的很多问题，常见的使用场景有以下几种：**

- 允许用户从NPM服务器下载别人编写的第三方包到本地使用。(silly-datetime)

- 允许用户从NPM服务器下载并安装别人编写的命令行程序(工具)到本地使用。（supervisor）

- 允许用户将自己编写的包或命令行程序上传到NPM服务器供别人使用。

## 二、NPM命令 详解

### 1. npm -v

查看npm命令版本

### 2. 使用npm命令安装模块

    npm install _Module Name_

    如 安装jq模块：

    npm install jquery

### 3. 使用 npm uninstall ModuleName 命令卸载模块

    npm uninstall moduleName

### 4. npm list

    查看当前目录下已经安装的node包
    npm list

### 5. npm info jquery

    查看jQuery 版本
    npm info 模块    //查看模块的版本

### 6. 指定版本安装

    npm install jquery@1.8.0

## 三、package.json

> 关键词：package.json定义了这个项目所需要的各种模块,以及项目的配置信息(比如名称、版本、许可证等元数据)

### 1. 创建package.json

    npm init
    npm init -yes

### 2. package.json文件

    {
        name": "test",
        "version": "1.0.0",
        "description": "test",
        "main": "main.js",
        "keywords": [
            "test"
        ],
        "author": "wade",
        "license": "MIT",
        "dependencies": {
            "express": "^4.10.1"
        },
        "devDependencies": {
            "jslint": "^0.6.5"
        }

    }

### 3.安装模块并把模块写入package.json(依赖)

    npm install    babel-cli --save-dev
    npm install 模块 --save
    npm install 模块--save-dev

### 4. dependencies 与 devDependencies 之间的区别 ?

使用npm installnode_ module –save自动更新depende ncies字段值;

使用npm installnode_ module –save-dev自动更新devDependenc ies字段值;

dependencie   配置当前程序所依赖的其他包。

devDependencie   配置当前程序所依赖的其他包，只会下载模块，而不下载这些模块的`测试`和文档框架

    "dependencie s": {
        "ejs": "^2.3.4",
        "express": "^4.13.3",
        "formidable": "^1.0.17"
    }

^表示第一位版本号不变，后面两位取最新的

~表示前两位不变，最后一个取最新

*表示全部取最新

## 四、安装淘宝镜像

<http://www.npmjs.org> npm包官网

<https://npm.taobao.org/> 淘宝npm镜像官网

淘宝NPM 镜像是一个完整npmjs.org 镜像，你可以用此代替官方版本(只读)，同步频率目前为10分钟一次以保证尽量与官方服务同步。

**我们可以使用我们定制的cnpm (gzip 压缩支持) 命令行工具代替默认的npm:**

    npm install -g cnpm --registry=https: //registry.npm.taobao.org

## 结语

OK，这次的 分享 到这就结束了，虽然有点少，但是对于小白入门node周边生态基本足够了。

### 参考

- [node.js 学习社区](https://http://www.nodeclass.com/)
- [node.js 专业中文社区](https://https://cnodejs.org/)

 