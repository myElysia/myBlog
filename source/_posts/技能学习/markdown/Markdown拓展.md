---
title: Markdown拓展
tags:
  - Markdown
  - R Markdown
  - Hexo
keywords:
  - Code Block
  - Note
  - Tabs
  - Path Links
categories:
  - 技能学习
  - markdown
top_img: 'https://pic3.zhimg.com/v2-d8e1c695f6f11a6ba6e1d9c465a541c6_r.jpg'
description: >-
  「标签」(Tag Plugin) 是 Hexo 提供的一种快速生成特定内容的方式。 例如，在标准 Markdown
  语法中，我们无法指定图片的大小。这种情景，我们即可使用标签来解决。...tab标签用于快速创建 tab选项卡...
abbrlink: 129f6bc0
date: 2023-03-15 14:16:23
---
{% note info %}
节选自 [Hexo写作技巧](https://eblog.gitee.io/posts/hexo/hexo-writing-skills.html), 可以前往原作查漏补缺。  
Markdown [基本语法](https://www.markdownguide.org/basic-syntax) 和 [进阶技巧](https://www.markdownguide.org/extended-syntax) 可参考链接，本文不再赘述。  
本文 参考了 [内置标签-NexT使用文档](https://theme-next.iissnan.com/tag-plugins.html), 有需要的同学请自行翻阅。  
部分内容需要安装 `hexo-tag-bootstrap` 对功能进行拓展, 插件官网: [hexo-tag-bootstrap](https://github.com/wzpan/hexo-tag-bootstrap)
{% endnote %}

「标签」(Tag Plugin) 是 Hexo 提供的一种快速生成特定内容的方式。 例如，在标准 Markdown 语法中，我们无法指定图片的大小。这种情景，我们即可使用标签来解决。Hexo内置来许多标签来帮助写作者可以更快的书写， [完整的标签列表](https://hexo.io/docs/tag-plugins.html) 可以参考 Hexo官网。另外，Hexo 也开放来接口给主题，使主题有可能提供给写作者更简便的写作方法。

## 代码块进阶用法

可以通过为代码块附加参数的形式为其添加更丰富的信息提示，效果如下：

```javascript HelloWorld https://example.com 链接地址
console.log("Helloworld")
```

代码块语法规则如下:

```
``` [language] [title] [url] [link text]
code snippet
/```
```

其中，各参数意义如下：

- langugae：语言名称，引导渲染引擎正确解析并高亮显示关键字
- title：代码块标题，将会显示在左上角
- url：链接地址，如果没有指定 link text 则会在右上角显示 link
- link text：链接名称，指定 url 后有效，将会显示在右上角

url 必须为有效链接地址才会以链接的形式显示在右上角，否则将作为标题显示在左上角。以 url 为分界，左侧除了第一个单词会被解析为 language，其他所有单词都会被解析为 title，而右侧的所有单词都会被解析为 link text。

如果不想填写 title，可以在 language 和 url 之间添加至少三个空格。

可以在站点配置文件中设置 `highlight.auto_detect: true` 来开启自动语言检测高亮。

```diff _config.yml
highlight:
  enable: true
  line_number: false
- auto_detect: false
+ auto_detect: true
  tab_replace:
```

## note标签

通过 note 标签可以为段落添加背景色，语法如下:

```
{% note [class] %}
文本内容 (支持行内标签)
{% endnote %}
```

支持的class种类包括 `default` `primary` `success` `info` `warning` `danger`，也可以不指定 class。
它们的效果如下:
{% note default %} note tag {% endnote %}
{% note primary %} note tag {% endnote %}
{% note success %} note tag {% endnote %}
{% note info %} note tag {% endnote %}
{% note warning %} note tag {% endnote %}
{% note danger %} note tag {% endnote %}

更多配置 可以在 主题配置文件 中进行配置
```yaml _config.themename.yml
note:
  # Note 标签样式预设
  style: modern  # simple | modern | flat | disabled
  icons: false  # 是否显示图标
  border_radius: 3  # 圆角半径
  light_bg_offset: 0  # 默认背景减淡效果，以百分比计算
```

## tab标签
tab标签用于快速创建 tab选项卡, 语法如下:
```
{% tabs [Unique name], [index] %}
  <!-- tab [Tab caption]@[icon] -->
  标签页内容（支持行内标签）
  <!-- endtab -->
{% endtabs %}
```
其中，各参数意义如下：
- Unique name: 全局唯一的 Tab 名称，将作为各个标签页的 id 属性前缀
- index: 当前激活的标签页索引，如果未定义则默认选中显示第一个标签页，如果设为 - 1 则默认隐藏所有标签页
- Tab caption: 当前标签页的标题，如果不指定则会以 Unique name 加上索引作为标题
- icon: 在标签页标题中添加 Font awesome 图标

## 网易云音乐
在网页版云音乐中找到歌曲，点击生成外链播放器 并根据个人喜好调整尺寸大小和播放模式，然后将获得的 `iframe` 代码添加到页面中。
默认样式如下:
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=1868943615&auto=1&height=66"></iframe>  

如果你还想让播放器居中，可以将 `iframe` 包在 `<center>` 标签内。  

<center>
<iframe frameborder="no" border="0" marginwidth="0" marginheight="0" width=330 height=86 src="//music.163.com/outchain/player?type=2&id=1868943615&auto=1&height=66"></iframe>
</center>  

{% note warning %}
其实这种通过 HTML 标签实现 CSS 样式的做法并不合适，写前端代码的时候不推荐这么做，并且 HTML5 中也已经废除了 `<center>` `<strong>` 等纯粹为了改变样式而存在的 HTML 标签，HTML 标签应该只负责文档结构，所有样式相关的工作应该交给 CSS 来实现。
网易云音乐中部分歌曲因版权保护已经无法生成外链了，即使是通过控制台强行拿到外链地址，嵌入网页后也无法播放。
{% endnote %}

## 引用站内文章
Hexo 提供了一个叫作 `post_link` 的标签语法来专门对内部博文进行引用。它的格式如下：
```markdown
{% post_link 文件名(不要后缀,可带路径) 文章别名(可选) %}
```
其中文件名指的是 `Markdown` 文件的文件名，例如你的博客中有一篇文件名为 HelloWorld.md 的博文，那你就可以使用以下方式引用:
```markdown
{% post_link hello/HelloWorld %}
```
Hexo 会自动将这篇博文的标题显示在文章中，并带上正确的链接。当然，你也可以给链接使用一个另外的名字，比如 “我的 HelloWorld”：
```markdown
{% post_link HelloWorld 我的HelloWorld %}
```