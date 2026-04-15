# 网站性能优化指南

本指南将帮助您优化网站的性能，提升加载速度和用户体验。

## 图片优化

### 1. 图片压缩

**问题**：发现一些大图片文件：
- `prof_pic_color.png` (14.4 MB)
- `prof_pic.jpg` (2.3 MB)
- `rhino.png` (1.6 MB)

**解决方案**：
- 使用图片压缩工具（如 TinyPNG、Squoosh）压缩图片
- 将 PNG 格式转换为 WebP 格式
- 对于头像等图片，建议大小控制在 200KB 以下

### 2. 响应式图片

**实现**：使用 `<picture>` 标签或 `srcset` 属性提供不同尺寸的图片：

```html
<picture>
  <source srcset="image.webp" type="image/webp">
  <source srcset="image.jpg" type="image/jpeg">
  <img src="image.jpg" alt="Image description">
</picture>
```

## CSS 优化

### 1. CSS 清理

**配置**：项目已配置 PurgeCSS，会自动清理未使用的 CSS：

```js
// purgecss.config.js
module.exports = {
  content: ["_site/**/*.html", "_site/**/*.js"],
  css: ["_site/assets/css/*.css"],
  output: "_site/assets/css/"
};
```

### 2. CSS 压缩

**实现**：Jekyll 配置中已启用 CSS 压缩：
- `jekyll-minifier` 插件会自动压缩 CSS
- `jekyll-terser` 插件会压缩 JavaScript

## JavaScript 优化

### 1. 脚本压缩

**实现**：`jekyll-terser` 插件会自动压缩 JavaScript 文件。

### 2. 脚本延迟加载

**建议**：对于非关键脚本，使用 `defer` 或 `async` 属性：

```html
<script defer src="script.js"></script>
<script async src="analytics.js"></script>
```

## 缓存策略

### 1. 浏览器缓存

**配置**：GitHub Pages 会自动设置适当的缓存头。

### 2. 资源版本控制

**实现**：项目使用 `cache-bust.rb` 插件为静态资源添加版本号，避免缓存问题。

## 构建优化

### 1. 构建过程

**部署脚本**：`bin/deploy` 脚本会：
1. 切换到部署分支
2. 构建网站（`bundle exec jekyll build`）
3. 清理未使用的 CSS（`purgecss`）
4. 推送到 GitHub Pages

### 2. 构建缓存

**建议**：本地开发时，Jekyll 会缓存构建结果，加快后续构建速度。

## 性能测试

### 1. 工具推荐

- **Google PageSpeed Insights**：https://developers.google.com/speed/pagespeed/insights/
- **Lighthouse**：https://developers.google.com/web/tools/lighthouse/
- **WebPageTest**：https://www.webpagetest.org/

### 2. 测试指标

关注以下核心指标：
- **LCP (Largest Contentful Paint)**：首屏最大内容绘制时间
- **FID (First Input Delay)**：首次输入延迟
- **CLS (Cumulative Layout Shift)**：累积布局偏移
- **TTI (Time to Interactive)**：可交互时间

## 优化建议

### 1. 图片优化

- [ ] 压缩所有图片文件
- [ ] 转换 PNG 为 WebP 格式
- [ ] 为不同设备提供响应式图片

### 2. 代码优化

- [ ] 检查并移除未使用的 JavaScript
- [ ] 确保 CSS 选择器简洁高效
- [ ] 减少 DOM 元素数量

### 3. 资源加载

- [ ] 优先加载关键 CSS
- [ ] 延迟加载非关键资源
- [ ] 合理使用 CDN 资源

### 4. 服务器优化

- [ ] 启用 GZIP 压缩（GitHub Pages 已默认启用）
- [ ] 确保适当的缓存策略
- [ ] 优化 DNS 解析

## 常见问题

### 1. 页面加载慢

**解决方案**：
- 压缩图片
- 减少 HTTP 请求
- 优化 CSS 和 JavaScript

### 2. 移动端性能差

**解决方案**：
- 提供针对移动设备的图片
- 简化移动端页面结构
- 避免大型 JavaScript 库

### 3. 首次加载时间长

**解决方案**：
- 实现渐进式加载
- 优化首屏内容
- 使用预加载关键资源

## 监控建议

定期使用性能测试工具监控网站性能，及时发现并解决性能问题。

---

**提示**：性能优化是一个持续的过程，定期检查和优化可以保持网站的良好性能。