---
title: Hexo文章变量配置
date: 2023-03-14 14:18:18
updated: 2023-03-15 14:00:00
categories:

- 技能学习

tags:

- Hexo
- Node.js

keywords:

- Front-matter

---

> 可参照官方文档[Front-matter](https://hexo.io/zh-cn/docs/front-matter) 获得更详细的配置内容, 本文只是做个转载和备份.

## Front-matter

Front-matter 即文件最上方以 `---` 进行分隔的区域, 用于指定一些文件的变量, 举个栗子:

```markdown
---
title: Hello World
date: 2013/7/13 20:46:25
---
```

以下是预先定义的参数, 你可以在模板中使用这些参数值来对文章进行定义:

| 参数              | 描述                                                                                     | 默认值                   |
|-----------------|----------------------------------------------------------------------------------------|-----------------------|
| layout          | 布局                                                                                     | config.default_layout |
| title           | 文章标题                                                                                   | 文章的文件名                |
| date            | 建立时间                                                                                   | 文件的建立时间               |
| updated         | 更新时间                                                                                   | 文件的更新时间               |
| comments        | 开启文章的评论功能                                                                              | true                  |
| tags            | 文章标签(不适应分页)                                                                            ||
| categories      | 文章分类(不适应分页)                                                                            ||
| permalink	      | 覆盖文章的永久链接，永久链接应该以 / 或 .html 结尾                                                         | 	null                 |
| excerpt	        | 纯文本的页面摘要。使用 [该插件](https://hexo.io/zh-cn/docs/tag-plugins#文章摘要和截断) 来格式化文本               ||
| disableNunjucks | 启用时禁用 Nunjucks 标签 `{{ }}/{% %}` 和 [标签插件](https://hexo.io/zh-cn/docs/tag-plugins) 的渲染功能 | false                 |
| lang	           | 设置语言以覆盖 自动检测	                                                                          | 继承自 _config.yml       |

## 分类和标签

只有文章支持分类和标签，您可以在 Front-matter 中设置。在其他系统中，分类和标签听起来很接近，但是在 Hexo 中两者有着明显的差别：分类具有顺序性和层次性，也就是说 `Foo, Bar` 不等于 `Bar, Foo`；而标签没有顺序和层次。  

{% note warning %}
__分类方法注意事项__
下面的指定方法：

```
categories:
  - Diary
  - Life
```

会使分类 `Life` 成为 `Diary` 的子分类，而不是并列分类。因此，有必要为您的文章选择尽可能准确的分类。  
如果你需要为文章添加多个分类，可以尝试以下 list 中的方法。

```
categories:
- [Diary, PlayStation]
- [Diary, Games]
- [Life]
```

此时这篇文章同时包括三个分类： `PlayStation` 和 `Games` 分别都是父分类 `Diary` 的子分类，同时 `Life` 是一个没有子分类的分类。
{% endnote %}