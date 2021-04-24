---
title: hexo常用指令
date: 2020-02-10 04:08:29
categories: 配置
tags:
---
前段时间刚部署好博客，特地记录一下几个常见命令。
1.创建博文
```
hexo new "title";
```
2.发博文外加部署到github
```
hexo clean;
hexo s/server;
hexo g/generate;
hexo d/deploy;
```
3.组合命令
```
hexo g -d/hexo d -g;
```
