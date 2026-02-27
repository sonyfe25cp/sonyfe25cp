# 📝 GitHub Blog 方案指南

本仓库包含多种在 GitHub 上发布博客的方案，适合不同需求。

---

## 🎯 方案对比

| 方案 | 难度 | 自动化 | 适合场景 |
|------|------|--------|----------|
| **RSS 自动同步** | ⭐ | ✅ 完全自动 | 已有博客，想同步到 GitHub |
| **GitHub Pages + Jekyll** | ⭐⭐ | ⚠️ 半自动 | 想要独立博客网站 |
| **GitHub Issues 博客** | ⭐ | ✅ 自动 | 轻量级，用 Issue 写文章 |
| **Markdown 静态博客** | ⭐⭐ | ⚠️ 手动推送 | 简单直接，纯 Markdown |

---

## 方案一：RSS 自动同步（已配置）⭐

**适合**：已有博客（Medium、Dev.to、个人博客等），想自动同步到 GitHub Profile

### 已配置的文件

```
.github/workflows/blog-posts.yml  # GitHub Action 工作流
```

### 支持的 RSS 源

```yaml
# Dev.to
https://dev.to/feed/你的用户名

# Medium
https://medium.com/feed/@你的用户名

# 知乎专栏
https://www.zhihu.com/rss

# 简书
https://www.jianshu.com/u/你的 ID/feed.xml

# WordPress
https://你的博客.com/feed/

# 自定义 RSS
任何标准 RSS/Atom 源
```

### 启用步骤

1. **修改工作流中的 RSS 源**
   ```bash
   cd /home/admin/.openclaw/workspace/sonyfe25cp
   # 编辑 .github/workflows/blog-posts.yml
   # 将 feed_list 改为你的 RSS 地址
   ```

2. **推送并启用 Action**
   ```bash
   git add .
   git commit -m "feat: enable blog sync"
   git push
   ```

3. **在 GitHub 上启用 Workflow**
   - 访问 https://github.com/sonyfe25cp/sonyfe25cp/actions
   - 点击 "I understand my workflows, go ahead and enable them"

### 效果

README 中的 `<!-- BLOG-POST-LIST:START -->` 和 `<!-- BLOG-POST-LIST:END -->` 之间会自动填充最新文章。

---

## 方案二：GitHub Pages + Jekyll 🌐

**适合**：想要一个完整的博客网站

### 快速开始

```bash
# 创建新的博客仓库
gh repo create sonyfe25cp/blog --public
cd blog

# 初始化 Jekyll
git remote add origin https://github.com/sonyfe25cp/blog.git
echo "# My Blog" > README.md
git add . && git commit -m "init" && git push -u origin main
```

### 访问地址

`https://sonyfe25cp.github.io/blog/`

### 优点

- ✅ 完整的博客功能（分类、标签、归档）
- ✅ 自定义域名
- ✅ 丰富的主题
- ✅ SEO 友好

---

## 方案三：GitHub Issues 博客 📋

**适合**：轻量级博客，用 Issue 写文章

### 设置方法

1. 创建一个专门的博客仓库
   ```bash
   gh repo create sonyfe25cp/blog-posts --public
   ```

2. 用 Issue 写文章
   - Title = 文章标题
   - Labels = 分类标签
   - Body = 文章内容（支持 Markdown）

3. 在 Profile README 中链接
   ```markdown
   ## 📝 Blog Posts
   
   - [文章标题](https://github.com/sonyfe25cp/blog-posts/issues/1)
   ```

### 优点

- ✅ 无需配置
- ✅ 支持评论
- ✅ 版本历史
- ✅ 移动端友好

---

## 方案四：Markdown 静态博客 📄

**适合**：简单直接，纯 Markdown 爱好者

### 目录结构

```
blog/
├── posts/
│   ├── 2026-01-01-hello-world.md
│   ├── 2026-01-15-my-project.md
│   └── 2026-02-01-tech-review.md
└── README.md
```

### 在 Profile 中展示

```markdown
## 📝 Recent Posts

- [Hello World](/blog/posts/2026-01-01-hello-world.md)
- [My Project](/blog/posts/2026-01-15-my-project.md)
```

---

## 🚀 推荐组合

### 最佳实践

```
┌─────────────────────────────────────────────────┐
│  主博客平台（Medium/Dev.to/个人博客）            │
│         ↓ (RSS 自动同步)                         │
│  GitHub Profile README（展示最新 5 篇）           │
│         ↓ (完整文章链接)                         │
│  GitHub Pages / 原平台（完整内容）               │
└─────────────────────────────────────────────────┘
```

### 工作流

1. **写文章** → 发布到主博客平台
2. **自动同步** → GitHub Action 每 6 小时检查更新
3. **展示摘要** → Profile README 显示最新 5 篇
4. **引流** → 读者点击链接阅读完整文章

---

## 📊 推荐平台

| 平台 | 特点 | RSS 支持 |
|------|------|----------|
| **Dev.to** | 开发者社区，SEO 好 | ✅ |
| **Medium** | 流量大，付费墙 | ✅ |
| **Hashnode** | 开发者友好，自定义域名 | ✅ |
| **Hugo/Hexo** | 静态博客，完全控制 | ✅ |
| **WordPress** | 功能强大，插件多 | ✅ |
| **Notion + Blog** | 笔记即博客 | ⚠️ 需工具 |

---

## 🔧 下一步行动

### 立即启用博客同步

```bash
cd /home/admin/.openclaw/workspace/sonyfe25cp

# 1. 编辑工作流，填入你的 RSS 源
# 2. 推送配置
git add .
git commit -m "feat: setup blog sync workflow"
git push

# 3. 访问 https://github.com/sonyfe25cp/sonyfe25cp/actions 启用 Workflow
```

### 选择你的博客平台

- **想快速开始** → Dev.to（开发者友好，注册即用）
- **想要流量** → Medium（用户基数大）
- **想要控制** → Hugo/Hexo + GitHub Pages（完全自定义）
- **已有博客** → 直接用现有 RSS 源

---

## 💡 小贴士

1. **首次运行**：推送后需要手动在 Actions 页面启用 Workflow
2. **测试运行**：可以手动触发 Workflow 测试（workflow_dispatch）
3. **更新频率**：默认每 6 小时检查，可修改 cron 表达式
4. **文章数量**：默认显示 5 篇，避免 README 过长
5. **时区设置**：已设置为 Asia/Shanghai（北京时间）

---

## 📚 资源

- [blog-post-workflow](https://github.com/gautamkrishnar/blog-post-workflow)
- [GitHub Pages 文档](https://pages.github.com/)
- [Jekyll 主题](https://jekyllthemes.io/)
- [Dev.to](https://dev.to/)
- [Hashnode](https://hashnode.com/)

---

**祝你写作愉快！** ✍️
