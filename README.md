# html-showcase

HTML 页面 / 看板 / 演示生成器：给任何内容（数字、要点、主题），生成漂亮的单文件 HTML 页面，零依赖、浏览器直接打开、方向键翻页。

## What This Does

**html-showcase** 帮非设计师做出漂亮的网页演示、看板、报告页，不需要懂 CSS 或 JavaScript。它用「先展示、再选择」（show, don't tell）的方式：不让你用语言描述审美偏好，而是直接生成视觉预览，让你挑喜欢的。

可以用它做的例子：运营数据看板、项目调度大屏、周报 / 复盘、产品方案、年度回顾、活动海报……内置 20 套设计系统，覆盖商务、数据、极简、创意、东方审美等调性。

## Key Features

- **Zero Dependencies** — 单文件 HTML，内联 CSS/JS。无 npm、无构建工具、无框架。
- **Visual Style Discovery** — 说不清想要什么风格？没关系，从生成的视觉预览里挑。
- **20 套模板库** — `bold-template-pack/`，渐进加载：先出 3 张预览让你选，定稿后才读该模板完整设计规范。
- **PPT Conversion** — 把现成 PowerPoint 转成网页版，保留文字、图片、演讲者备注。
- **Fixed 16:9 Stage** — 1920×1080 固定舞台整体等比缩放，手机不重排。
- **Anti-AI-Slop** — 精选独特风格，拒绝千篇一律的 AI 审美（再见，白底紫渐变）。
- **CJK 适配** — 每套模板都有中文排版说明（字体配对 / 行距 / 标点）。

## Installation

### Claude Code 手动安装

把 skill 文件复制到 Claude Code 的 skills 目录：

```bash
# 创建目录
mkdir -p ~/.claude/skills/html-showcase/scripts

# 复制用户侧 skill 文件
cp SKILL.md STYLE_PRESETS.md viewport-base.css html-template.md animation-patterns.md ~/.claude/skills/html-showcase/
cp -R bold-template-pack ~/.claude/skills/html-showcase/
cp scripts/extract-pptx.py scripts/deploy.sh scripts/export-pdf.sh ~/.claude/skills/html-showcase/scripts/
```

或直接克隆：

```bash
git clone https://github.com/Yara918/html-showcase.git ~/.claude/skills/html-showcase
```

### WorkBuddy

```bash
git clone https://github.com/Yara918/html-showcase.git ~/.workbuddy/skills/html-showcase
```

### 其他编码 Agent

Codex、OpenCode、Gemini CLI 等本地编码助手可以用同一个核心 skill。最简路径：把仓库链接发给代理，让它从 `SKILL.md` 开始，按需加载引用的支持文件：

```text
https://github.com/Yara918/html-showcase
```

## Usage

### 新建演示

```
帮我做一份 5 页的 PPT：门店服务体验优化方案，给运营团队汇报。
第 1 页 封面：门店服务体验优化方案
第 2 页 现状：客诉率 0.8%→1.4% 连续 3 个月上升；高峰期响应超 3 小时占比 12%
第 3 页 数据：本月工单 320 单，解决率 95.3%，平均响应 2.1h
第 4 页 方案：弹性排班 / FAQ 自助入口 / 分诊模型优化
第 5 页 目标：解决率 97%、响应 1.8h、客诉率 0.5%
```

skill 会：

1. 问你的内容（页数 / 信息 / 图片）
2. 生成 **3 张风格预览** 让你对比（你没点名风格，就从需求推断调性）
3. 让你选视觉方向
4. 按你选的风格生成整套
5. 在浏览器打开

一句话开头也可以（如「帮我做个运营数据看板」），剩下的它会问你。

### 转换 PowerPoint

```
把 presentation.pptx 转成网页版
```

skill 会：

1. 提取 PPT 里所有文字、图片、备注
2. 展示提取内容给你确认
3. 让你选视觉风格
4. 生成带原始素材的 HTML 演示

## Template Gallery（20 套）

| 模板 | 调性 | 适合 |
|---|---|---|
| Blue Professional | 米色纸 + 电光蓝 | 方案、汇报、投资人材料 |
| Signal | 深海军蓝 + 哑金 | 董事材料、咨询交付、政策简报 |
| Monochrome | 奶油纸全墨排版 | 研究报告、白皮书、学术材料 |
| Cobalt Grid | 坐标纸 + 钴蓝衬线 | 设计研究、趋势报告、机构年刊 |
| Neo-Grid Bold | 米白纸 + 霓虹黄 | 数据页、对比、流程 |
| Raw Grid | 粗边框新粗野主义 | 路演、品牌、创业者 pitch |
| Swiss Grid | 12 栏网格 + 信号红 | 运营周报、方法论、制度说明 |
| Data Wall | 密集数据看板 + 注释 | 数据分析、复盘、BI 报告 |
| Glass Panel | 磨砂玻璃 + 柔和渐变 | 产品介绍、方案演示、团队介绍 |
| Aurora | 全幅渐变 + 超大白字 | 品牌发布、年度战略、开场收尾 |
| Departure Board | 橙字黑底翻牌屏 | 项目调度、运营大屏、倒计时 |
| Ticker Console | 绿色 CRT 扫描线 | 技术周报、系统状态、发布日志 |
| Bauhaus | 几何形 + 三原色 | 创意提案、品牌概念、文化活动 |
| Gallery Label | 白墙 + 衬线小字 | 作品展示、产品美学、品牌画册 |
| Riso Print | 双色套印 + 网点 | 活动海报、社群内容、创意运营 |
| Washi | 暖纸 + 朱印 + 留白 | 极简品牌、年度复盘、东方审美 |
| Metro Map | 45° 线路节点图 | 流程、组织架构、路径规划 |
| Kanban | 便签 + 和纸胶带 | 项目进度、运营日常、复盘 |
| Scoreboard | 七段 LED 大数字 | KPI 冲刺、目标竞赛、大促倒计时 |
| Blueprint | 蓝底白线工程图 | 方案图纸、规划蓝图、技术架构 |

渲染效果预览：打开 [examples/template-gallery.html](examples/template-gallery.html)（20 套缩略图）和 [examples/demo-deck-blue-professional.html](examples/demo-deck-blue-professional.html)（8 页完整演示）。

## Architecture

`SKILL.md` 驱动整个流程：

1. **Phase 1 内容收集** — 问用途 / 页数 / 内容 / 密度（演讲向 or 阅读向）
2. **Phase 2 风格发现** — 生成 3 张真实标题页预览（安全款 / 模板库款 / 大胆款），**预览门禁：用户选定前禁止生成整套**
3. **Phase 3 生成** — 读选中模板的 `design.md`，按固定 16:9 舞台生成单文件 HTML
4. **Phase 4 PPT 转换** — `scripts/extract-pptx.py` 提取内容后走同样的风格流程
5. **Phase 5 交付** — 清理预览、浏览器打开、告知用法

模板库在 `bold-template-pack/`：先读 `selection-index.json`（轻量元数据）→ 预览用 `preview.md` → 定稿才读 `design.md`。

## Philosophy

- **Show, don't tell** — 用视觉预览代替语言描述，人靠眼睛挑风格。
- **拒绝 AI slop** — 不默认字体、不白底紫渐变、不千篇一律的卡片布局。
- **固定 16:9 舞台** — 内容在 1920×1080 画布上排版，整幅等比缩放，不做移动端重排。
- **内容真实** — 只放用户给的内容，不编造数据。

## Sharing Your Presentation

### Deploy to a live URL

```bash
bash scripts/deploy.sh <filename.html>
```

生成可分享链接，任何设备（含手机）可打开。

### Export to PDF

```bash
bash scripts/export-pdf.sh <filename.html>
```

导出 PDF 用于离线分发。

## Requirements

- Python 3.10+（PPT 转换 / 部署 / PDF 导出脚本需要）
- 联网（页面使用 Google Fonts 字体加载）

## 模型差异说明

- **不同模型产出的结果会有差异**：排版质量、风格还原度、稳定性随模型能力波动，属正常现象（如个别模型可能出现文字溢出、布局变形，换模型重试或让模型按反馈修正即可）。
- 建议**自己实测几轮，找到最适合你的模型与生成方式**（哪类内容配哪个模型效果最好）。
- 生成页面为固定 1920×1080 舞台，内容偏**低密度、演讲型**；高密度文字场景请分页或精简内容。

## License

MIT — 见 [LICENSE](LICENSE)。
