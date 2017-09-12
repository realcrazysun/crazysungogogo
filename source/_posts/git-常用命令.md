---
title: git 常用命令
date: 2017-09-08 14:40:21
tags:
---
### 常用命令
``` bash
$ git clone 
$ git stash
$ git commit
$ git pull
$ git push
$ git rm -r --cached .   //清楚缓存  gitignore 失效时使用
```
### angular 提交规范
``` bash
$ npm install -g commitizen //安装Commitizen
$ commitizen init cz-conventional-changelog --save --save-exact //项目支持规范
$ git cz //代替 git commit
```