---
title: Hexo博客生成永久链接
categories:
  - 技能学习
  - hexo
tags:
  - Hexo
abbrlink: 614e46f9
date: 2023-03-15 17:20:09
---

> 先放上插件链接: [hexo-abbrlink](https://github.com/Rozbo/hexo-abbrlink)

## 前言
Hexo 文章链接默认的生成规则是：`:year/:month/:day/:title`，是按照年、月、日、标题来生成的。

这样的话，生成的链接非常长长长长长，而且如果我们的 Markdown 使用中文标题，那就更惨了，URL 一转码，将是一场灾难。

更难受的是如果我们修改了文章的日期或者标题，那么将导致链接改变，别人或者你分享出去的文章就会 404，这非常的蛋疼啊，所以就有了这种插件，不论你如何修改文章的日期、名称，只要不改变 footer-matter 中的 id 值，那么文章链接永远不会变。

## 安装插件
```bash
npm install hexo-abbrlink --save
```
## 修改hexo配置
```diff _config.yml
- permalink: :year/:month/:day/:title/
+ permalink: posts/:abbrlink.html  ## 此处可以自己设置
+ ## abbrlink config
+ abbrlink:
+   alg: crc32      #support crc16(default) and crc32 进制
+   rep: hex        #support dec(default) and hex  算法
+   drafts: false   #(true)Process draft,(false)Do not process draft. false(default) 
+   ## Generate categories from directory-tree
+   ## depth: the max_depth of directory-tree you want to generate, should > 0
+   auto_category:
+      enable: true  #true(default)
+      depth:        #3(default)
+      over_write: false 
+   auto_title: false #enable auto title, it can auto fill the title by path
+   auto_date: false #enable auto date, it can auto fill the date by time today
+   force: false #enable force mode,in this mode, the plugin will ignore the cache, and calc the abbrlink for every post even it already had abbrlink.
```
