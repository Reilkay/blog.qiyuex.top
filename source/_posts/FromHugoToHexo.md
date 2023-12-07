---
title: 从Hugo到Hexo
date: 2020-09-24 21:33:40
updated: 2020-09-28 11:24:50
tags: ["Hexo", "博客", "日常"]
categories: 博客相关
keywords: ["Hexo", "Hugo", "博客", "Vercel"]
description: 记录把博客从Hugo折腾到Hexo的故事~
top_img:
comments:
cover: https://cdn.jsdelivr.net/gh/Reilkay/blog-cdn@master/img/banner/Art-FromHugoToHexo.jpg
toc:
---

今年五月份的时候，因为服务器炸了的缘故，丢掉了几乎所有的文章，于是本着图方便，数据不会丢失的考虑，开始考虑转向使用静态无后端的博客系统。当时选择了 Hugo 来作为框架，一方面是被构建的快速所吸引，另一方面是当时很喜欢简约的主题，简约的主题在提升访问速度方面也有不小的帮助。

近些天一方面是得知将博客部署在 Vercel 可以提高访问速度，另一方面可能也是觉得原先的博客太简约了，没什么实用的小功能，主题也是年久失修，故准备将原博客从 Hugo 迁移到 Hexo，整点花里胡哨的小玩意~

## Hexo 和 Hugo 对比

### 构建速度

显然，Hugo 的构建速度是高于 Hexo 的，毕竟在 Hugo 的官网上打出的标语就是：“The world’s fastest framework for building websites.”

这一点在本地调试的时候显得很明显，增加一篇博文或者修改某些配置后，使用 Hexo 构建大概需要 4-5 秒的时间，而 Hugo 几乎不需要等待。

但是由于个人文章并不多且使用自动部署的方式，目前来看这方面感知并不算强，所以切换到 Hexo 并没有让我感觉到性能和体验有过多的下降。

### 调试方便程度

依赖于 Hugo 快速构建的特点，Hugo 在调试方面的体验也是高于 Hexo 的，在本地调试的过程中，Hugo 可以在浏览器上实时预览，而 Hexo 则需要手动进行刷新，且在某些配置修改后，需要重新输入命令进行调试。

### 上手简单程度

Hugo 的传播广泛度是不及 Hexo 的，这就导致使用 Hugo 的 dalao 数量较少，虽说近年 Hugo+Github Page 的使用也逐渐普及，但比起 Hexo 来说还是少的多，于是相关的搭建教程就要少一些。

另一方面，由于 dalao 数量较少，所以虽然 Hugo 拥有的主题数量不少，但主题的成熟度相对较低，很多都需要自己修改和优化，要求用户有一定代码能力。

Hexo 在这个方面就显得优秀很多，如本博客使用的 Butterfly 主题，成熟度就相当高，基本集成了绝大多数个人需要的功能，只需要按照 Hexo 的官方文档和主题文档就可以完成配置，上手非常简单，不需要什么基础知识就可以完成。

### 丰富度

Hexo 拥有丰富的插件，合理的利用这些插件可以人性化的提供更多有用的功能，和各种花里胡哨的效果，这一点也是我从 Hugo 换到 Hexo 的主要原因，因为个人能力不足的缘故，使用 Hugo 很难做出一些自己想要的效果，网上各种教程资料数量较少，又有很多都已经“年久失修”，这时 Hexo 丰富的插件就能给予我很大的帮助。

### 结论

虽然从 Hugo 切换到 Hexo 牺牲了构建速度，但相对于对我而言感知较不明显的速度，Hexo 构建的简易度和站点最终的效果更加吸引我，~~（或许以后会真香也说不定。~~

## Vercel+jsDelivr 的使用

之前也提到过使用 Hugo 简约风的博客，一方面是为了提升访问的速度。那么 Vercel 和 JSDELIVR 就是我最终下定决心换到 Hexo 的理由了。

### Vercel 的使用

之前的博客一直是部署在 Github Page 上的，由于众所周知的原因，在国内某些众所周知的地方，Github 的访问相当受限，且在国内大部分地区，Github 的访问体验也并不好，延迟较高暂不说，访问速度也非常糟糕，使用某些复杂的主题时，打开首页就需要 3 秒以上，十分降低使用体验。

今年在[@amtoaer](https://allwens.work)大神的介绍下得知 Vercel，经过测试访问速度确实能快上许多，于是就准备将博客从 Github Page 转到 Vercel 上来。

Vercel 使用非常简单，几乎不需要什么配置，全程傻瓜式操作，就不多做描述了。

1. 用 Github 账号登陆 Vercel，导入 Git Repository

![导入Git Repo](https://i.loli.net/2020/09/28/7fNKonb6i51wOEs.png)

2. 输入 Project Name，选择使用的博客框架，点击 Deploy。

    ![Import Project](https://i.loli.net/2020/09/28/SBuntcYfWko2HI4.png)

3. 配置完成后，Vercel 就会自动在每次 push 后重新部署站点了。

### jsDelivr 的使用

jsDelivr 是一个免费且好用的 CDN，CDN 即 Content Delivery Network——内容分发网络，依靠部署在各地的边缘服务器，通过中心平台的负载均衡、内容分发、调度等功能模块，使用户就近获取所需内容，降低网络拥塞，提高用户访问响应速度和命中率。

总而言之，就是能使用户访问博客静态资源时速度提升。

使用方法如下：

1. 将所需资源上传到 Github 仓库。

2. 使用如下链接引用资源。

    ```bash
    https://cdn.jsdelivr.net/gh/你的用户名/你的仓库名@发布的版本号(分支名)/文件路径
    ```

    例如：若要访问`Reilkay`用户，`blog-cdn`仓库，`master`分支下，`img/favicon.png`文件，则使用如下链接。

    ```
    https://cdn.jsdelivr.net/gh/Reilkay/blog-cdn@master/img/favicon.png
    ```

## 博客迁移

### 主题选择

主题方面选择了较为（非常）成熟的 Butterfly 主题，这次主要耗时也是在主题的配置方面，但由于主题成熟度相当高的缘故，即使其提供的功能非常丰富，但参考其文档：[Butterfly 安裝文檔](https://demo.jerryc.me/posts/21cfbf15/) 以及 Hexo 的官方中文文档：[Hexo 文档](https://hexo.io/zh-cn/docs/) ，配置过程还是很简单的。最终效果也是非常漂亮。

![博客首页](https://i.loli.net/2020/09/28/UPQXaGrMVEhLjtT.png)

### 文章迁移

由于是无后端的静态博客，而且个人文章较少，故只是手动复制了 MarkDown 文件至 Hexo 的`_post`目录下并手动修改了`Front-matter`。

注：如果需要不改变网址以便 SEO，则需要修改根目录下`_config.yml`文件的该部分：

```yaml
# URL
## If your site is put in a subdirectory, set url as 'http://example.com/child' and root as '/child/'
url: https://blog.qiyuex.top
root: /
permalink: :title/
permalink_defaults:
pretty_urls:
    trailing_index: true # Set to false to remove trailing 'index.html' from permalinks
    trailing_html: true # Set to false to remove trailing '.html' from permalinks
```

将`permalink`修改为和 Hugo 一样的形式。

## 尾声

这次得益于 Hexo 成熟的主题 Butterfly，折腾的内容不算太多，启用了 Pjax，Valine，Mathjax 后暂时也是得到了一个自己想要的效果，漂亮就完事儿了！

最后，Hexo 真香~
