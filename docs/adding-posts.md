**如何在本项目中添加文章（写入 Markdown）**

本说明以中文介绍如何在此 Astro 项目中添加博客文章（Markdown 文件），包含必要的 frontmatter 字段示例、文件放置位置、图片说明，以及如何在本地预览与提交更改。

**文章位置**: 本博客的文章目录位于 `src/content/posts/`。

- 新文章请在 `src/content/posts/` 下新建一个 `*.md` 或 `*.mdx` 文件。
- 主页与附录类文件位于 `src/content/`，例如 `home.md`、`addendum.md`。

**必须/常用的 frontmatter 字段**

项目在 `src/content.config.ts` 中声明了文章集合（`posts`），并对 frontmatter 做了 schema 校验。下面是常用字段及说明：

- `title`（字符串，必须）: 文章标题。
- `published`（日期，必须）: 发布时间，推荐使用 `YYYY-MM-DD` 格式，例如 `2025-12-09`。
- `draft`（布尔，可选）: 是否为草稿，`true` 会将文章标记为未发布（默认为 `false`）。
- `description`（字符串，可选）: 摘要/描述，用于列表页或 meta。
- `author`（字符串，可选）: 作者名。
- `series`（字符串，可选）: 如属于某个系列，可写系列名。
- `tags`（字符串数组，可选）: 标签列表，例如 `['typescript', '入门']`，默认空数组。
- `coverImage`（对象，可选）: 封面图片，结构为：

  ```yaml
  coverImage:
    src: ./images/cover.jpg  # 或相对路径
    alt: '封面描述'
  ```

- `toc`（布尔，可选）: 是否显示目录（table of contents），默认 `true`。

注: 配置文件 `src/content.config.ts` 使用了 `astro:content` 的 schema（`zod`），因此请确保 frontmatter 字段类型与 schema 匹配。

**示例文章模板**

将下面模板复制到新文件 `src/content/posts/my-new-article.md` 并根据需要修改：

```markdown
---
title: '示例文章标题'
published: 2025-12-09
draft: false
description: '一句话简介，最多一两行。'
author: '你的名字'
tags: ['示例','教程']
coverImage:
  src: ./images/cover.jpg
  alt: '封面图示例'
toc: true
---

# 引言

这里写正文内容，支持 Markdown、代码块、图片等。

```ts
console.log('Hello world')
```

更多内容……
```

**图片与资源放置建议**

- 封面图可以放在与文章同目录的 `images/` 子目录中（如 `src/content/posts/images/cover.jpg`），并在 frontmatter 中使用相对路径（如上例）。
- 也可以将图片放到 `public/` 并以 `/images/xxx.jpg` 的路径引用。

**如何在本地预览**

项目常用命令（基于仓库根目录）：

```bash
pnpm install      # 首次或依赖变更时安装依赖
pnpm dev          # 启动本地开发服务器
```

启动后，终端会显示本地访问地址（例如 `http://localhost:3000`）。在浏览器打开该地址并导航到文章页面（通常为站点的文章列表或直接访问文章的 slug），新文章会被自动加载。

如果你使用 `npm` 或 `yarn`，将 `pnpm` 替换为相应命令：`npm install` / `npm run dev` 或 `yarn` / `yarn dev`。

**提交到 Git 的建议流程**

```bash
git add src/content/posts/your-new-post.md
git commit -m "feat: add post '你的文章标题'"
git push
```

如果你同时新增了图片：

```bash
git add src/content/posts/your-new-post.md src/content/posts/images/cover.jpg
git commit -m "feat: add post with cover image"
git push
```

**常见问题与提示**

- 如果页面不显示新文章，确认 frontmatter 中 `draft` 是否为 `true`（草稿通常不会显示）。
- 确认 `published` 字段是有效日期格式，schema 使用 `z.coerce.date()`，错误的日期格式可能导致构建/加载失败。
- 若使用封面图片失败，尝试将图片放到 `public/` 并使用绝对路径测试（例如 `/images/cover.jpg`）。

---

如果你希望我：

- 自动为你创建一个新文章文件（我可以代为生成并提交），
- 或者把这段文档合并到项目根 `README.md`，

请告诉我你希望的下一步。我也可以生成一个文章模板脚本来快速创建带图片文件夹的文章骨架。
