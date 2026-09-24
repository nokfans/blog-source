---
title: 用 Hexo + Fluid 在 GitHub Pages 上搭建博客
date: 2026-09-23 16:00:00
tags:
  - Hexo
  - GitHub Pages
  - 静态博客
categories:
  - 技术教程
---

Hexo 是 Node 生态里的静态博客生成器。你在本地写 Markdown,Git 负责版本管理,GitHub Pages 负责免费托管。整套流程没有服务器成本,内容本身也天然带着提交历史。

这篇笔记记录从零搭建的过程。

## 环境准备

需要 Node.js 18 以上、Git,以及一个 GitHub 账号。

```bash
node -v
git --version
```

## 初始化项目

```bash
npx hexo-cli init blog
cd blog
npm install
```

Hexo 会在 `source/_posts/` 下放一篇默认文章,`_config.yml` 是整个站点的配置入口。

## 换一个顺眼的主题

Fluid 主题简洁、中文友好,适合技术博客。

```bash
git clone --depth 1 https://github.com/fluid-dev/hexo-theme-fluid themes/fluid
```

然后在 `_config.yml` 里把 `theme` 改成 `fluid`。

## 写第一篇文章

```bash
npx hexo new "我的第一篇技术笔记"
```

文章落在 `source/_posts/`,正文就是 Markdown,写完保存即可。

## 本地预览

```bash
npx hexo server
```

打开 `http://localhost:4000` 就能看到效果,改动会即时刷新。

## 部署到 GitHub Pages

在 `_config.yml` 里配置部署目标:

```yaml
deploy:
  type: git
  repo: https://github.com/<用户名>/<用户名>.github.io.git
  branch: main
```

然后生成并发布:

```bash
npx hexo clean && npx hexo generate && npx hexo deploy
```

等一两分钟,访问 `https://<用户名>.github.io` 就能看到站点。

## 小结

以后每写一篇,`hexo clean && hexo generate && hexo deploy` 三步就完成更新。工具链搭好之后,时间可以留给内容。
