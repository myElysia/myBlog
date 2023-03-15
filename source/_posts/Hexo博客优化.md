---
title: Hexo博客优化
date: 2023-03-15 15:46:27
categories: 技能学习
tags:

- Hexo
- 美化相关

keywords:

- 腾讯COS图床
- RSS订阅
- 插件推荐

---
{% note info %}
本篇 参照了 [hexo 教程 - 搭建个人博客踩坑](http://gungnir.top/27148.html), 若有语焉不详的内容请翻看原文或百度。

refer:

- [故障排错参考官方文档](https://hexo.io/docs/troubleshooting.html#Git-Deployment-Problems)
- [butterfly 安装文档](https://butterfly.js.org/posts/dc584b87/)
- [hexo-butterfly - 搜索系统引入](https://cloud.tencent.com/developer/article/2024117)
- [hexo-butterfly 魔改记录](https://www.cnblogs.com/yyyzyyyz/p/15542401.html)
- [利用 Hexo 在多台电脑上提交和更新 github pages 博客](https://www.jianshu.com/p/0b1fccce74e0)
- 巨好用：[【Hexo 插件系列】日志的自动分类插件 hexo-auto-category](https://blog.eson.org/pub/e2f6e239/)
- [Hexo 同时部署在 GitHub、Coding、Gitee_Ashin Wang’s Blog 的博客 - CSDN 博客](https://blog.csdn.net/weixin_45667885/article/details/101084532)
- H[exo + 腾讯云 COS，为你的站点加速 - 简书 (jianshu.com)](https://www.jianshu.com/p/fb6086126959)
- [利用腾讯云对象存储 COS 桶托管 hexo 博客 - 腾讯云开发者社区 - 腾讯云 (tencent.com)](https://cloud.tencent.com/developer/article/1947477)
- [Hexo-deployer-cos-cdn 插件安装使用指南 | 悟尘记 - 李小龙的博客网站 (lixl.cn)](https://www.lixl.cn/2020/020936412.html#toc-heading-10)
- [Hexo 静态网站托管到腾讯云 COS+CDN 加速以及缓存自动刷新完美方案 - 掘金 (juejin.cn)](https://juejin.cn/post/6943242978010316807#heading-7)

{% endnote %}

## 插件推荐

> [rozbo/hexo-abbrlink: create one and only link for every post for hexo (github.com)](https://github.com/rozbo/hexo-abbrlink)
>
> 可以把链接 permalink 转为数字的插件，配置容易，生成时自动转为数字。
> 
> [hexojs/hexo-generator-feed: Feed generator for Hexo. (github.com)](https://github.com/hexojs/hexo-generator-feed)
> 
> 生成 RSS 文件的插件
> 
> [hexojs/hexo-filter-nofollow: Add nofollow attribute to all external links automatically. (github.com)](https://github.com/hexojs/hexo-filter-nofollow)
> 
> 为网站使用到的所有外链添加 rel=”noopener external nofollow noreferrer”, 可以有效地加强网站 SEO 和防止权重流失
> 
> [hexojs/hexo-generator-sitemap: Sitemap generator for Hexo. (github.com)](https://github.com/hexojs/hexo-generator-sitemap)
> 
> 生成 sitemap 的插件
> 
> [coneycode/hexo-generator-baidu-sitemap: Baidu Sitemap generator plugin for Hexo (github.com)](https://github.com/coneycode/hexo-generator-baidu-sitemap)
>
> 看名字就知道，是专门为百度生成 sitemap 的插件

## Hexo 生成RSS

> [Hexo 博客教程之添加 RSS 订阅_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV13g4y1v7UP/?vd_source=e73a152dada4626bad49c30d848902f7)

## Hexo 加速
### Gulp 压缩全站静态资源

> [使用 gulp 压缩博客静态资源 | Akilar の糖果屋](https://akilar.top/posts/49b73b87/)

### 静态资源压缩 Hexo-all-minifier

> [chenzhutian/hexo-all-minifier: A plugin for Hexo that optimizes HTML, CSS, JS and imagages, and it can optionally deploys your blog. (github.com)](https://github.com/chenzhutian/hexo-all-minifier)

模块安装
```shell bash/zsh
npm install hexo-all-minifier --save
```

Hexo配置文件修改
```yaml _config.yml
all_minifier: true
html_minifier:
  silent: true
css_minifier:
  silent: true
js_minifier:
  silent: true
image_minifier:
  enable: false
```