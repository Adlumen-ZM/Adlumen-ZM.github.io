# 网站信息维护指南

本指南将帮助您了解如何更新和维护您的个人GitHub Pages网站。

## 目录结构

```
Adlumen-ZM.github.io/
├── _bibliography/     # 出版物引用文件
├── _books/            # 书籍评论
├── _data/             # 数据文件（简历、社交链接等）
├── _includes/         # 页面组件
├── _layouts/          # 页面布局模板
├── _news/             # 新闻和公告
├── _pages/            # 主要页面
├── _posts/            # 博客文章
├── _projects/         # 项目展示
├── _sass/             # SCSS样式文件
├── assets/            # 静态资源（图片、CSS、JS等）
├── _config.yml        # 网站配置文件
└── README.md          # 项目说明
```

## 如何更新内容

### 1. 个人信息

**文件**: `_config.yml`

```yaml
# 基本信息
first_name: Your
last_name: Name
title: Your Title  # 职位/头衔
alumni: false      # 是否为校友
affiliation: Your Affiliation  # 所属机构
email: your.email@example.com
```

### 2. 导航栏

**文件**: `_pages/` 目录下的各个页面文件

每个页面文件的顶部都有Front Matter配置，例如：

```yaml
---
title: About  # 页面标题
layout: page  # 页面布局
permalink: /  # 页面URL
nav: true     # 是否在导航栏显示
nav_order: 1  # 导航栏顺序
---
```

### 3. 博客文章

**目录**: `_posts/`

文件名格式: `YYYY-MM-DD-title.md`

示例：

```yaml
---
title: "文章标题"
date: 2026-04-15  # 发布日期
description: "文章描述"
tags: [tag1, tag2]  # 标签
---

文章内容，使用Markdown语法...
```

### 4. 项目展示

**目录**: `_projects/`

示例：

```yaml
---
title: "项目名称"
description: "项目描述"
date: 2026-04-15  # 项目日期
image: /assets/img/project.jpg  # 项目图片
links:
  - name: GitHub
    url: https://github.com/username/project
  - name: Demo
    url: https://project-demo.com
---

项目详细描述...
```

### 5. 出版物

**文件**: `_bibliography/papers.bib`

使用BibTeX格式添加出版物：

```bibtex
@article{your_paper,
  title={论文标题},
  author={作者1 and 作者2},
  journal={期刊名称},
  year={2026},
  volume={1},
  pages={1-10},
  doi={10.1234/example}
}
```

### 6. 简历

**文件**: `_data/cv.yml` 或 `assets/json/resume.json`

使用YAML或JSON格式添加简历内容。

### 7. 新闻和公告

**目录**: `_news/`

示例：

```yaml
---
title: "新闻标题"
date: 2026-04-15  # 发布日期
---

新闻内容...
```

### 8. 书籍评论

**目录**: `_books/`

示例：

```yaml
---
title: "书籍标题"
author: "作者"
image: /assets/img/book_covers/book.jpg  # 书籍封面
rating: 5  # 评分（1-5）
date: 2026-04-15  # 评论日期
---

书籍评论内容...
```

## Markdown语法基础

### 标题

```markdown
# 一级标题
## 二级标题
### 三级标题
```

### 文本格式

```markdown
**粗体**
*斜体*
***粗斜体***
~~删除线~~
`代码`
```

### 列表

```markdown
- 无序列表项1
- 无序列表项2
  - 嵌套列表项

1. 有序列表项1
2. 有序列表项2
```

### 链接

```markdown
[链接文本](https://example.com)
```

### 图片

```markdown
![图片描述](/assets/img/image.jpg)
```

### 引用

```markdown
> 这是一段引用
```

### 代码块

```markdown
```python
print("Hello, world!")
```
```

### 表格

```markdown
| 表头1 | 表头2 |
|-------|-------|
| 内容1 | 内容2 |
| 内容3 | 内容4 |
```

## 常见问题

### 1. 网站不更新

**解决方案**:
- 确保文件已提交到GitHub
- 等待GitHub Pages重新构建（通常需要1-2分钟）
- 清除浏览器缓存

### 2. 图片不显示

**解决方案**:
- 确保图片路径正确
- 图片文件已上传到`assets/img/`目录
- 检查文件名大小写（GitHub区分大小写）

### 3. 导航栏不显示页面

**解决方案**:
- 确保页面文件中有`nav: true`配置
- 检查`nav_order`值是否正确

### 4. 博客文章不显示

**解决方案**:
- 确保文件名格式为`YYYY-MM-DD-title.md`
- 检查Front Matter配置是否正确
- 确保文章日期格式正确

## 部署流程

1. **本地修改**：编辑相应文件
2. **预览**：使用Jekyll本地服务器预览（可选）
   ```bash
   bundle exec jekyll serve
   ```
3. **提交**：将更改提交到GitHub
   ```bash
   git add .
   git commit -m "更新内容"
   git push origin main
   ```
4. **等待构建**：GitHub Pages会自动构建网站
5. **验证**：访问您的GitHub Pages网站确认更改生效

## 高级功能

### 1. 主题切换

网站支持浅色/深色模式，无需额外配置。

### 2. 搜索功能

**配置**：在`_config.yml`中设置：
```yaml
search_enabled: true
```

### 3. 新闻通讯

**配置**：在`_config.yml`中设置：
```yaml
newsletter:
  enabled: true
  provider: mailchimp
  mailchimp:
    list_id: your_list_id
```

### 4. 谷歌分析

**配置**：在`_config.yml`中设置：
```yaml
google_analytics: UA-XXXXXXXX-X
```

## 设计系统

本网站使用融合了Notion和Claude风格的设计系统：

- **配色**：温暖的中性色和强调色
- **字体**：Georgia（标题）和Inter（正文）
- **布局**：响应式设计，适配不同设备
- **动画**：平滑的过渡和交互效果

## 联系支持

如果您在维护网站过程中遇到问题，可以：

1. 查看项目的[README.md](README.md)文件
2. 查阅[GitHub Pages文档](https://docs.github.com/en/pages)
3. 参考[Jekyll文档](https://jekyllrb.com/docs/)

---

**提示**：定期备份您的网站文件，以防止意外丢失数据。