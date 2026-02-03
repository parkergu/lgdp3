# LGDP3 学术项目网站 - Copilot 开发指南

## 项目概述
这是一个静态学术研究项目网站，用于展示论文《LGDP3：用于稳健机器人操作的局部几何感知 3D 扩散策略》。该网站展示了论文的摘要、方法论和演示视频。

## 架构与文件结构

### HTML 页面
- [index.html](../index.html) - **匿名评审版本**（当前主页，无作者信息）
- [index_for_nonanonymous.html](../index_for_nonanonymous.html) - 带作者的完整版本（论文被录用后使用）

### 技术栈
- **CSS 框架**: [Bulma](https://bulma.io/) (`static/css/bulma.min.css`)
- **图标**: FontAwesome + Academicons
- **JavaScript**: jQuery 3.5.1 + 自定义轮播/滑块插件
- **字体**: Google Sans, Noto Sans, Castoro (通过 Google Fonts CDN)

### 关键目录
- `static/images/` - 方法图解、GIF 演示（例如 `dp_fail_pin_x2.gif`）
- `static/videos/` - 演示用的 MP4 视频
- `static/css/index.css` - 自定义样式（出版物特定类）
- `static/js/index.js` - 轮播/滑块初始化，插值图像处理

## 编码规范

### HTML 结构模式
使用 Bulma 的语义类层级进行内容分区：
```html
<section class="section">
  <div class="container is-max-desktop">
    <div class="columns is-centered">
      <div class="column is-full-width">
        <h2 class="title is-3 has-text-centered">章节标题</h2>
        <!-- 在此添加内容 -->
      </div>
    </div>
  </div>
</section>
```

### 图片/视频嵌入
- 图片：使用内联 `style` 设置大小，居中对齐 `display: block; margin-left/right: auto`
- 视频：使用带有 `controls` 属性的 `<video>` 标签，宽度设置为 90-100%
- GIF：直接通过 `<img>` 标签嵌入

### CSS 命名
- 自定义类以 `publication-` 为前缀（例如 `publication-title`, `publication-authors`, `publication-video`）
- 使用 Bulma 工具类：`has-text-centered`, `has-text-justified`, `is-full-width`

### 中文注释
HTML 包含中文注释（例如 `<!--声明了文档类型-->`）。添加解释性注释时请保持此惯例。

## 常见任务

### 添加新内容章节
1. 复制现有的 `<section class="section">` 块
2. 更新 `<h2>` 标题
3. 添加内容（正文使用 `<p class="has-text-justified">`）

### 切换到非匿名版本
论文被录用后，用 `index_for_nonanonymous.html` 的内容替换 `index.html` 以显示作者信息。

### 添加新媒体
1. 将文件放置在相应的 `static/` 子目录中
2. 使用相对路径引用：`static/videos/filename.mp4` 或 `static/images/filename.png`

## 外部依赖 (CDN)
- Google Analytics: `G-PYVRSFMDRL`
- Google Fonts API
- Academicons (通过 jsDelivr)

## 备注
- 无需构建系统 - 纯静态 HTML/CSS/JS
- 直接在浏览器中打开 `index.html` 进行本地测试
- `index.js` 中的插值功能（Interpolation）预期图片路径为 `static/interpolation/stacked/`（当前主页未使用）
