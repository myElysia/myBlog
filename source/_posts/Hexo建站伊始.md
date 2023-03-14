---
title: Hexo建站伊始
date: 2023-03-14 11:22:33
categories:

- 技能学习

tags:

- Node.js
- Hexo

keywords:

- Hexo
- 初始化

---

# Hexo建站流程简述(一)

## 初始化Hexo

* 安装必要的软件

| 软件名称     | 软件介绍         |
|----------|--------------|
| Node.js  | hexo依赖环境     |
| git      | 版本管理工具       |
| Typora   | markdown编写工具 |
| WebStorm | web类项目编写工具   |

* 安装Hexo

  > Hexo官方地址: [Hexo官网](https://hexo.io/zh-cn)

    1. 建立博客项目根文件夹, 例如 `D:/Hexo/`.  
       因为每个人的命名习惯不同, 之后统一以`[Blogroot]`指代博客根目录.
    2. 使用`npm`安装`Hexo`, 并在 `终端` 进入 \[Blogroot\],输入
       ```shell
       # npm源替换为阿里的镜像源
       npm config set registry https://registry.npmmirror.com
       # hexo-cli 是 hexo 的指令集
       npm install hexo-cli -g
       # 在根目录下建一个项目目录
       hexo init <floder>
       ```

* Hexo 初始化项目目录
    1. 安装项目可能需要的插件
       ```shell
       npm install hexo-generator-index --save
       # 主页插件，最新版Hexo默认安装，可跳过
       npm install hexo-generator-archive --save
       # 归档插件，最新版Hexo默认安装，可跳过
       npm install hexo-generator-category --save
       # 分类插件，最新版Hexo默认安装，可跳过
       npm install hexo-generator-tag --save
       # 标签插件，最新版Hexo默认安装，可跳过
       npm install hexo-server --save
       # 服务插件，最新版Hexo默认安装，可跳过
       npm install hexo-renderer-marked --save
       # markdown渲染支持插件，最新版Hexo默认安装，可跳过
       npm install hexo-renderer-stylus --save
       # nib css支持插件，如无需求，可跳过
       npm install hexo-generator-feed --save
       # RSS订阅支持插件，如无需求，可跳过
       npm install hexo-generator-sitemap --save
       # sitemap生成插件，帮助搜索引擎抓取，如无需求，可跳过
       npm install hexo-admin --save
       # 网页端hexo文档管理插件，如无需求，可跳过
       npm install hexo-deployer-git --save
       # git部署插件，必须安装
       ```
    2. 添加分类页面 和 标签页面
        * 分类页面  
          终端 进入 `[Blogroot]/<floder>`, 并输入
          ```shell
          hexo new page categories
          ```
          打开 `[Blogroot]/<floder>/source/categories/index.md`, 并加上 `type` 属性.
          ```diff
          ---
          title: categories
          date: 2017-05-27 13:47:40
          + type: "categories"
          ---
          ```
        * 标签页面
          终端 进入 `[Blogroot]/<floder>`, 并输入
            ```shell
            hexo new page tags
            ```
          打开 `[Blogroot]/<floder>/source/tags/index.md`, 并加上 `type` 属性.
            ```diff
            ---
            title: tags
            date: 2017-05-27 13:47:40
            + type: "tags"
            ---
            ```
        * 标签和tag的添加
          给文章添加标签和tag, 可以参照以下示例
            ```diff
            ---
            title: HelloWorld
            date: 2020-10-01 00:00:00
            + categories: 学习笔记
            + tags:
            +   - node.js
            +   - 📁Hexo
            ---
          ```

## Github配置

1. 配置hexo部署插件
    * 确保已经安装了`hexo-deployer-git`, 如果没有，请参照上方初始化流程重新安装
    * 打开 `[Blogroot]/<floder>/_config.yml`, 修改`deploy`配置项. 若不存在，则手动添加
      > 注: 此处的仓库是 username.github.io 才可在浏览器中直接 https://username.github.io 进行访问.

         ```yaml
         # 站点部署到github要配置Deployment
         ## Docs: https://zespia.tw/hexo/docs/deploy.html
         deploy:
           type: git
           repo:
           github:
             url: git@github.com:username/username.github.io.git  # 记得把username替换为自己的用户名
             branch: master #2020年10月后github新建仓库默认分支改为main，注意修改
             # 也可以用另一种写法,二选一即可
           github: git@github.com:username/username.github.io.git,master
         ``` 
2. 把 `hexo` 博客内容提交到git仓库
   ```bash
   hexo clean
   hexo generate
   hexo deploy
   ```

## 域名配置

1. 获取项目所在服务器IP地址
   首先要取得博客部署服务器的IP地址，这里以github举例:
   ```shell
    ping username.github.io
   ```
2. 域名解析配置
   前往域名服务商 提供的 域名控制台，添加解析记录.
3. Hexo配置域名信息
   在 `[Blogroot]/<floder>/source` 目录下新建 `CNAME` 文件, 并在`CNAME`文件中添加上你购买的域名.
4. github配置
   打开 `username.github.io`, 点击仓库中的 `setting`, 下拉找到 `Github Pages`栏, 在 `Custom domain` 中填入你购买的域名.