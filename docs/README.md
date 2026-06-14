# vvvcxjvvv.github.io 使用指南

本站是一个纯手写的赛博极简风格静态博客，部署在 GitHub Pages 上。不依赖任何静态站点生成器（Hexo/Hugo/Jekyll），所有页面均为手写 HTML + CSS，结构透明、修改直接。

## 仓库结构

```
vvvcxjvvv.github.io/
├── index.html           # 首页
├── css/
│   └── style.css        # 全局样式（赛博极简主题）
├── post/
│   └── dagbee.html      # 文章页（示例）
├── docs/
│   └── README.md        # 本文档
└── favicon.png          # 站点图标
```

## 样式体系

主题配置集中在 `css/style.css` 顶部的 CSS 变量中：

```css
:root {
  --neon-pink: #FF2E93;     /* 强调色 - 粉 */
  --neon-cyan: #00F0FF;     /* 强调色 - 青 */
  --bg-primary: #0A0A0A;    /* 页面背景 */
  --bg-secondary: #111111;  /* 次级背景 */
  --text-primary: #E0E0E0;  /* 主文字 */
  --text-secondary: #888888;/* 次文字 */
  --text-dim: #555555;      /* 暗文字 */
}
```

修改这些变量即可全局切换配色。字体使用 JetBrains Mono，通过 Google Fonts CDN 加载。

## 如何添加文章

### 1. 创建文章文件

在 `post/` 目录下新建 HTML 文件，例如 `post/my-article.html`。

复制以下模板：

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>文章标题 — chanchan</title>
  <meta name="description" content="文章描述">
  <link rel="icon" href="/favicon.png">
  <link rel="stylesheet" href="/css/style.css">
</head>
<body>

  <!-- Navigation -->
  <nav class="nav">
    <div class="nav-inner">
      <a href="/" class="nav-logo"><span class="accent">~</span>/chanchan</a>
      <ul class="nav-links">
        <li><a href="/">Posts</a></li>
        <li><a href="https://github.com/vvvcxjvvv" target="_blank" rel="noopener">GitHub</a></li>
      </ul>
    </div>
  </nav>

  <!-- Post Content -->
  <main class="container post-page">
    <header class="post-header">
      <div class="post-meta">
        <span>2025-07</span>
        <span class="sep">|</span>
        <span>Tag1 · Tag2</span>
      </div>
      <h1 class="post-page-title">文章标题</h1>
    </header>

    <article class="article">

      <!-- 在这里写文章内容 -->

      <h2>章节标题</h2>
      <p>正文段落...</p>

      <pre><code>代码块...<span class="lang-label">go</span></code></pre>

      <hr>

      <a href="/" class="back-link">&larr; back to posts</a>

    </article>
  </main>

  <!-- Footer -->
  <footer class="footer">
    <div class="footer-inner">
      <span>&copy; 2025 chanchan</span>
      <a href="https://github.com/vvvcxjvvv" target="_blank" rel="noopener">github.com/vvvcxjvvv</a>
    </div>
  </footer>

</body>
</html>
```

### 2. 在首页添加文章入口

编辑 `index.html`，在 `// posts` 下方添加一个新的 `post-item`：

```html
<article class="post-item">
  <span class="post-date">2025-07</span>
  <a href="/post/my-article.html" class="post-title-link">文章标题</a>
  <div class="post-tags">
    <span class="post-tag">Tag1</span>
    <span class="post-tag">Tag2</span>
  </div>
</article>
```

新增文章放在列表最上面（按时间倒序）。

## 文章内可用的排版元素

| 元素 | 写法 | 效果 |
|------|------|------|
| 二级标题 | `<h2>标题</h2>` | 带下划线分隔 |
| 三级标题 | `<h3>标题</h3>` | 无下划线 |
| 强调文字 | `<strong>文字</strong>` | 霓虹青色 |
| 斜体强调 | `<em>文字</em>` | 霓虹粉色（无斜体） |
| 行内代码 | `<code>代码</code>` | 暗底 + 粉色字 |
| 代码块 | `<pre><code>...<span class="lang-label">go</span></code></pre>` | 带语言标签 |
| 引用块 | `<blockquote>文字</blockquote>` | 左侧粉色竖线 |
| 表格 | `<table>...</table>` | 暗色条纹 |
| 分隔线 | `<hr>` | 细线 |
| 链接 | `<a href="url">文字</a>` | 青色 + 底线 |

## 如何修改导航栏

编辑每个 HTML 文件中的 `<nav>` 部分。当前导航项：

- **Posts** → 首页
- **GitHub** → 外链到 github.com/vvvcxjvvv

添加新导航项只需在 `<ul class="nav-links">` 中增加 `<li>`。

## 如何修改首页 Hero 区域

编辑 `index.html` 中的 `.hero` 部分：

- **博客名**：修改 `.hero-title`
- **副标题**：修改 `.hero-subtitle`
- **标签**：修改 `.tag` 元素

## 如何部署

### 方式一：命令行推送

```bash
cd vvvcxjvvv.github.io
git add .
git commit -m "add new post"
git push origin main
```

推送后 1-2 分钟，GitHub Pages 会自动构建部署，访问 https://vvvcxjvvv.github.io/ 即可看到更新。

### 方式二：GitHub 网页编辑

直接在 GitHub 仓库页面点击文件 → Edit → Commit changes，效果相同。

## 本地预览

```bash
# Python（推荐）
cd vvvcxjvvv.github.io
python -m http.server 8888
# 访问 http://localhost:8888

# Node.js
npx serve -l 8888
# 访问 http://localhost:8888
```

修改文件后刷新浏览器即可看到变化，无需重启服务器。

## 修改样式

所有样式在 `css/style.css` 中：

- **改配色**：修改 `:root` 下的 CSS 变量
- **改字体**：修改 `body` 的 `font-family`，同时更新 `@import` 的 Google Fonts 链接
- **改布局宽度**：修改 `--max-width` 变量
- **改导航栏**：修改 `.nav` 相关样式
- **改文章排版**：修改 `.article` 下的样式

## 常见问题

**Q: 为什么不用 Hexo/Hugo？**
A: 手写 HTML 对当前规模（少量文章）更可控。没有构建步骤，改了即生效，没有依赖地狱。如果将来文章超过 20 篇再考虑迁移到 SSG。

**Q: 怎么添加自定义域名？**
A: 在仓库根目录创建 `CNAME` 文件，内容写你的域名（如 `blog.example.com`），然后在域名 DNS 添加 CNAME 记录指向 `vvvcxjvvv.github.io`。

**Q: 怎么让 Google 搜索到？**
A: 确保仓库是 Public，在 Google Search Console 提交站点地图。可以手动创建 `sitemap.xml` 列出所有页面 URL。
