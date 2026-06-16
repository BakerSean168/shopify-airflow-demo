# AirFlow Shopify DTC Demo - 产品需求文档 (PRD)

## 文档信息

- **项目名称**: AirFlow - Shopify DTC 独立站学习项目
- **版本**: v1.0
- **创建日期**: 2026-06-15
- **项目类型**: 学习型项目 / 面试作品集
- **开发时长**: 8 小时
- **目标**: 快速学习 Shopify + React 技术栈，构建可展示的 DTC 独立站原型

---

## 1. 项目背景

### 1.1 岗位需求分析

**目标岗位**: Fastlane - AI 全栈体验工程师

**岗位关键要求**:
- AI 原住民：会用 AI 辅助开发、设计、测试、文档
- Shopify 全栈：懂 Shopify 主题、Liquid、商品/购物车/结账链路
- UED + 前端：能实现页面，也能判断视觉层级、品牌调性、交互细节
- CRO：理解转化率优化，懂 PDP、CTA、信任背书、加购、结账漏斗
- Agentic Workflow：能自动化重复交付流程

**公司背景**:
- Fastlane 是 Shopify Platinum Partner
- 主要业务：DTC 品牌出海、独立站建设、CRO 优化
- 技术方向：Shopify Theme 定制 + 前端全栈 + AI 工作流

### 1.2 项目定位

**不是**: "完整的生产级 DTC 独立站"
**而是**: "AI 辅助的 8 小时快速学习与原型验证项目"

**核心价值**:
1. 展示 AI-native 学习能力（零基础 8 小时上手 Shopify）
2. 展示 Shopify 实操能力（Theme 定制、Liquid、CRO 理解）
3. 展示前端开发能力（可选 React 集成）
4. 展示商业理解（DTC、CRO、品牌定位）

### 1.3 品类选择：蓝牙耳机

**为什么选择蓝牙耳机**:
- 技术展示机会多：产品参数对比、规格筛选、兼容性查询
- AI 应用场景清晰：参数表、技术文案、FAQ 生成
- 国际化需求明显：电子产品在不同市场有参数差异
- 性能优化有抓手：产品图多、参数表复杂
- 符合出海趋势：安克、石头、大疆等中国品牌 DTC 出海典型案例

---

## 2. 项目目标

### 2.1 学习目标

- [ ] 理解 Shopify Theme 架构（layout、templates、sections、snippets）
- [ ] 掌握 Liquid 模板语言基础
- [ ] 学会 Shopify CLI 工具使用
- [ ] 了解 DTC 独立站的核心要素
- [ ] 理解 CRO（转化率优化）基本概念
- [ ] 体验 AI 辅助开发工作流

### 2.2 技术目标

**必须完成**:
- ✅ 搭建基于 Dawn 的 Shopify Theme
- ✅ 录入 2-3 个产品（AI 生成内容）
- ✅ 定制至少 1 个 Liquid Section
- ✅ 实现基础 CRO 元素（trust badges、库存提示）
- ✅ 响应式设计（移动端适配）

**可选完成**:
- 🔲 React 组件集成（Cart Drawer 或 Product Quick View）
- 🔲 产品对比工具
- 🔲 多语言支持

### 2.3 交付目标

- 可访问的 Shopify dev store
- GitHub 代码仓库（清晰的 README）
- 项目截图（首页、产品页、定制功能）
- 学习笔记文档
- 面试准备材料

---

## 3. 技术架构

### 3.1 技术栈

**Shopify 层**:
- 基础主题: Dawn (Shopify 官方)
- 开发工具: Shopify CLI 3.x
- 模板语言: Liquid
- 模板类型: JSON templates

**前端层**:
- 样式: Tailwind CSS (快速开发) 或 CSS Modules (结构化)
- 脚本: 原生 JavaScript (必须) + React (可选)
- 构建工具: Vite (如果使用 React)
- 类型系统: TypeScript (如果使用 React)

**开发工具**:
- 包管理: pnpm
- 版本控制: Git + GitHub
- 代码编辑: VS Code

**AI 工具**:
- 代码辅助: Claude / Codex
- 内容生成: Claude API 或对话式生成

### 3.2 项目结构

```
shopify-airflow-demo/
├── theme/                    # Shopify Theme (Dawn)
│   ├── assets/              # CSS, JS, images
│   ├── config/              # Theme settings
│   ├── layout/              # Page layouts
│   ├── locales/             # i18n files
│   ├── sections/            # Reusable sections
│   │   └── product-specs.liquid  # 定制的规格对比 section
│   ├── snippets/            # Small code snippets
│   │   └── trust-badges.liquid   # 信任标识
│   ├── templates/           # Page templates (JSON)
│   └── config.yml           # Shopify CLI config
│
├── react-app/               # React 组件 (可选)
│   ├── src/
│   │   ├── cart-drawer/    # 购物车组件
│   │   └── shared/         # 共享组件
│   ├── package.json
│   ├── vite.config.ts
│   └── tsconfig.json
│
├── scripts/                 # AI 工具脚本
│   └── generate-content.js # 内容生成脚本
│
├── docs/                    # 项目文档
│   ├── PRD.md              # 本文档
│   ├── learning-notes.md   # 学习笔记
│   └── screenshots/        # 项目截图
│
├── .gitignore
├── package.json            # 根目录脚本
└── README.md               # 项目说明
```

### 3.3 架构决策

**Theme 选择: Dawn**
- 理由: Shopify 官方默认主题，代码质量高，性能优化到位，是行业最佳实践

**React 与 Liquid 分工 (混合方案 C)**
- **纯 Liquid**: Homepage sections、产品参数表、FAQ、trust badges
- **Liquid + 增强 JS**: 图片画廊、variant selector
- **完全 React** (可选): Cart Drawer、Product Comparison Tool
- 理由: 平衡性能、SEO 和开发体验，符合 Shopify Partner 真实业务

**样式方案: Tailwind CSS**
- 理由: 快速开发，原子化类名，易于 AI 生成和理解

---

## 4. 产品规划

### 4.1 产品线设计

**5 个核心 SKU** (实际项目可简化为 2-3 个):

| 产品名称 | 定位 | 价格 | 核心场景 | 差异化特性 |
|---------|------|------|---------|-----------|
| **AirFlow Lite** | 入门款 | $49 | 日常通勤 | 长续航、轻量化 |
| **AirFlow Sport** | 运动款 | $79 | 运动健身 | 防水 IPX7、运动挂耳 |
| **AirFlow Pro** | 主力款 | $129 | 全场景 | ANC 降噪、多设备切换 |
| **AirFlow Gaming** | 游戏款 | $119 | 游戏竞技 | 低延迟、EQ 定制 |
| **AirFlow Max** | 旗舰款 | $199 | 发烧友/商务 | Hi-Res 音质、空间音频 |

**8 小时版本**: 只做 **AirFlow Lite** 和 **AirFlow Pro** 两个产品

### 4.2 产品参数维度

**共同参数** (用于对比表):
- 价格
- 电池续航（单次 + 充电盒）
- 主动降噪（有/无）
- 防水等级（IPX4/IPX7/无）
- 蓝牙版本
- 编解码器（SBC/AAC/LDAC）
- 延迟（ms）
- 重量
- 充电接口（USB-C）
- 特殊功能（多点连接、空间音频、透明模式）

**使用场景标签**:
- 通勤、运动、游戏、办公、旅行、音乐发烧

### 4.3 内容需求

**每个产品需要** (用 AI 生成):
- 1 句 tagline
- 3-5 句产品描述
- 5 个卖点
- 3 个使用场景描述
- 8-10 个 FAQ
- SEO meta（title、description）

**视觉素材需求**:
- 3-5 张产品图（纯白背景）
- 2-3 张场景图（使用中）
- 来源: Unsplash/Pexels 免费素材 或 AI 生成

---

## 5. 功能需求

### 5.1 核心页面

**必做页面**:

**1. Homepage (首页)**
- Hero section: 主视觉 + 品牌 slogan + CTA
- Featured products: 展示 2-3 个主打产品
- Image with text: 品牌故事或核心卖点
- Trust badges: 30 天退换、包邮、官方保修

**2. Product Listing Page (PLP - 集合页)**
- 产品网格展示
- 基础筛选（价格区间、使用场景）
- 排序（价格、新品）
- 产品卡片: 图片、名称、价格、快速查看

**3. Product Detail Page (PDP - 商品详情页)** - 重点
- 产品图片画廊（3-5 张图）
- 产品名称和价格
- Variant selector（如有不同颜色/容量）
- Add to cart 按钮
- **定制的规格参数 section** ⭐
- 产品描述
- 使用场景图文
- FAQ accordion
- Trust badges
- 推荐商品（Related products）

**4. Cart (购物车)**
- 基础版: Shopify 默认 cart page
- 进阶版 (可选): React Cart Drawer

### 5.2 定制功能 (至少做 1 个)

**选项 A: 产品规格对比 Section** (推荐)
- Liquid section
- 展示产品技术参数表格
- 可在 theme editor 配置参数
- 响应式表格设计

**选项 B: React Cart Drawer** (可选)
- 侧边滑出式购物车
- 实时更新数量
- 删除商品
- 小计金额
- 去结账按钮

**选项 C: Product Quick View Modal** (可选)
- 快速查看产品信息
- 不跳转直接加购

### 5.3 CRO 元素

**Trust Badges (信任标识)**:
- ✓ 30 天无理由退换
- ✓ 全球包邮
- ✓ 官方质保 1 年
- ✓ 安全支付

**紧迫感元素**:
- 库存提示: "仅剩 X 件"
- 限时优惠标签 (可选)

**社交证明**:
- 用户评价星级 (可用 Shopify Product Reviews app)
- "XX 人正在浏览此商品" (可选)

---

## 6. 开发计划

### 6.1 时间分配 (8 小时)

**Hour 0-1: 学习 + 环境搭建**
- ⏰ 30 分钟: AI 辅助学习 Shopify 核心概念
- ⏰ 30 分钟: 注册账号、安装 CLI、初始化 Dawn theme

**Hour 1-3: 产品录入 + Theme 定制**
- ⏰ 1-2 小时: 录入 2-3 个产品 (AI 生成内容)
- ⏰ 1 小时: Homepage 定制、品牌信息修改

**Hour 3-5: 定制功能开发**
- ⏰ 2 小时: 开发 1 个定制 Section 或 React 组件

**Hour 5-6: 视觉优化 + CRO 元素**
- ⏰ 30 分钟: 美化样式、响应式检查
- ⏰ 30 分钟: 添加 trust badges、库存提示

**Hour 6-7: 文档 + 截图**
- ⏰ 30 分钟: 整理项目结构、截图
- ⏰ 30 分钟: 写 README

**Hour 7-8: 复盘 + 面试准备**
- ⏰ 1 小时: 学习笔记整理
- ⏰ 1 小时: 面试问题准备

### 6.2 详细任务清单

#### Phase 1: 环境搭建 (1 小时)

**学习任务**:
- [ ] 让 AI 讲解: Shopify Theme 结构、Liquid 语法、Sections 概念
- [ ] 快速浏览 Dawn theme 文件结构

**环境任务**:
- [ ] 注册 Shopify Partner 账号
- [ ] 创建 development store
- [ ] 安装 Shopify CLI: `npm install -g @shopify/cli @shopify/theme`
- [ ] 初始化项目: `shopify theme init`，选择 Dawn
- [ ] 启动开发服务器: `shopify theme dev`
- [ ] 浏览器验证能访问

**验收标准**: 能在浏览器看到默认的 Dawn theme

---

#### Phase 2: 产品录入 (1-2 小时)

**产品 1: AirFlow Lite**
- [ ] 在 Shopify Admin 创建产品
- [ ] 用 AI 生成内容:
  ```
  Prompt: "为入门级蓝牙耳机 AirFlow Lite ($49) 写：
  - 1 句 tagline
  - 3 句产品描述（强调性价比、长续航、轻便）
  - 5 个产品卖点
  - 1 段通勤场景描述
  - 10 个 FAQ
  风格：简洁专业，面向年轻上班族"
  ```
- [ ] 复制内容到 Shopify
- [ ] 找/生成产品图 (Unsplash 搜索 "white wireless earbuds")
- [ ] 上传 2-3 张图片
- [ ] 设置价格 $49、库存 50

**产品 2: AirFlow Pro**
- [ ] 同样流程，定位主力款 ($129)
- [ ] AI prompt 强调: ANC 降噪、音质、多设备切换
- [ ] 目标客户: 音质要求高的用户

**产品 3 (可选): AirFlow Max**
- [ ] 旗舰款 ($199)
- [ ] 如果时间不够可以跳过

**验收标准**: 2 个产品在店铺中可浏览，内容完整专业

---

#### Phase 3: Theme 基础定制 (1 小时)

**品牌信息**:
- [ ] Theme settings → Store details
- [ ] Logo 文字改为 "AirFlow"
- [ ] Tagline: "Premium Audio Experience"
- [ ] 主色调: 选择科技蓝或高级黑
- [ ] 字体: 选择现代简洁字体

**Homepage 定制**:
- [ ] Customize theme → Homepage
- [ ] Hero section:
  - 标题: "Premium Audio Experience"
  - 副标题: (用 AI 生成品牌文案)
  - 按钮: "Shop Now" → 链接到 products collection
- [ ] Featured products section: 展示 2-3 个产品
- [ ] Image with text: 品牌故事 (用 AI 生成)
- [ ] 启用 Newsletter signup (邮件订阅)

**PDP 优化**:
- [ ] 进入产品模板编辑
- [ ] 确保有这些 sections: Product info, Related products
- [ ] 调整布局: 图片在左，信息在右

**验收标准**: Homepage 有品牌感，PDP 布局清晰

---

#### Phase 4: 定制功能开发 (2 小时)

**选项 A: 产品规格 Section** (推荐)

- [ ] 创建 `sections/product-specs.liquid`
- [ ] 用 AI 生成代码:
  ```
  Prompt: "写一个 Shopify Liquid section，展示蓝牙耳机规格参数表。
  要求:
  - 包含 schema，可在 theme editor 配置参数
  - 参数包括: 电池续航、蓝牙版本、重量、防水等级、编解码器
  - 使用表格布局，响应式设计
  - 样式用 Tailwind classes
  - 代码要有注释"
  ```
- [ ] 将代码保存到文件
- [ ] 在 product template 添加这个 section
- [ ] 在 theme editor 中配置参数
- [ ] 调试样式，确保移动端显示正常

**选项 B: React Cart Drawer** (可选，难度较大)

- [ ] 创建 `react-app/` 目录
- [ ] 初始化: `pnpm init` + 安装依赖
- [ ] 用 AI 生成 Cart Drawer 组件
- [ ] 配置 Vite 打包到 `theme/assets/`
- [ ] 在 theme.liquid 中引入和挂载

**验收标准**: 至少 1 个定制功能可见且能正常工作

---

#### Phase 5: CRO 元素添加 (1 小时)

**Trust Badges**:
- [ ] 创建 `snippets/trust-badges.liquid`
- [ ] 用 AI 生成代码:
  ```
  Prompt: "写一个 Shopify snippet，显示 4 个信任标识:
  - 30 天无理由退换
  - 全球免费配送
  - 官方质保 1 年
  - 安全加密支付
  使用 icon + 文字布局，响应式网格，简洁现代风格"
  ```
- [ ] 在产品页引入: `{% render 'trust-badges' %}`

**库存提示**:
- [ ] 创建 `snippets/stock-indicator.liquid`
- [ ] 根据库存数量显示: "仅剩 X 件" 或 "库存充足"
- [ ] 添加颜色提示（红色/绿色）

**样式优化**:
- [ ] 检查移动端显示
- [ ] 优化产品卡片 hover 效果
- [ ] 确保 CTA 按钮突出

**验收标准**: 产品页有明显的信任元素和紧迫感

---

#### Phase 6: 文档与截图 (1 小时)

**项目结构整理**:
- [ ] 创建 `docs/screenshots/` 目录
- [ ] 清理临时文件
- [ ] 确保代码有适当注释

**截图清单**:
- [ ] 首页 - 桌面版
- [ ] 首页 - 移动版
- [ ] 产品列表页
- [ ] 产品详情页 - 完整长截图
- [ ] 定制的 section 特写
- [ ] Theme editor 配置界面

**README 编写**:
- [ ] 项目简介
- [ ] 技术栈
- [ ] 学到了什么
- [ ] 项目亮点
- [ ] Demo 链接
- [ ] 截图展示
- [ ] AI 辅助说明
- [ ] 下一步计划
- [ ] 本地开发指南

**验收标准**: README 清晰专业，截图完整

---

#### Phase 7: 学习笔记 (1 小时)

**创建 `docs/learning-notes.md`**:

内容结构:
- Shopify 核心概念理解
  - Liquid 语言
  - Sections 机制
  - Theme 架构
- DTC 独立站关键点
  - CRO 策略
  - 产品页设计
  - 信任建立
- 遇到的问题和解决方案
- AI 辅助开发的收获和反思

**验收标准**: 体现学习思考过程，不是流水账

---

#### Phase 8: 面试准备 (1 小时)

**准备 5 分钟项目介绍脚本**:
- 开场: 项目背景和目标
- 技术选择和架构
- 核心功能演示
- AI 辅助开发说明
- 收获和下一步计划

**准备常见问题回答**:
- [ ] "介绍一下这个项目"
- [ ] "你对 Shopify 的理解？"
- [ ] "为什么选择蓝牙耳机品类？"
- [ ] "你用 AI 做了什么？如何保证质量？"
- [ ] "如果再给你一周时间？"
- [ ] "DTC 独立站最重要的是什么？"
- [ ] "遇到的最大挑战是什么？"
- [ ] "Shopify Theme 和 Hydrogen 的区别？"

**创建面试材料清单**:
- [ ] Demo 链接 (Shopify dev store)
- [ ] GitHub repo 链接
- [ ] README 快速导览
- [ ] 关键代码片段准备
- [ ] 截图 PDF (可选)

**验收标准**: 能流畅讲解项目，回答准备充分

---

## 7. AI 辅助工作流

### 7.1 内容生成流程

**产品文案生成**:
```
输入: 产品基础信息 (名称、定位、价格、核心特性)
↓
AI 生成: 
- Tagline
- 产品描述
- 卖点列表
- 使用场景描述
- FAQ
- SEO meta
↓
人工审核优化: 调整语气、补充细节、删除不合适内容
↓
输出: 完整产品内容包
```

**推荐 Prompt 模板**:
```
为 [产品定位] 的蓝牙耳机 [产品名称] ($[价格]) 生成营销内容：

产品核心特性:
- [特性 1]
- [特性 2]
- [特性 3]

目标客户: [客户画像]

请生成:
1. 一句简短的 tagline (不超过 8 个词)
2. 产品描述 (3-5 句话)
3. 5 个产品卖点 (每个 1 句话)
4. 3 个使用场景描述 (通勤/运动/办公，每个 2-3 句话)
5. 10 个常见问题和答案
6. SEO meta description (不超过 160 字符)

风格: 简洁专业，面向 [目标市场]，强调 [核心价值]
```

### 7.2 代码生成流程

**Liquid Section 生成**:
```
需求描述 → AI 生成 Section 代码 → 保存到文件 → 测试调试 → 优化样式
```

**推荐 Prompt 模板**:
```
写一个 Shopify Liquid section，实现 [功能描述]。

要求:
- 包含完整的 schema，可在 theme editor 配置
- 响应式设计，移动端友好
- 使用 Tailwind CSS classes
- 代码有清晰注释
- 遵循 Shopify 最佳实践

请提供完整的 .liquid 文件代码。
```

### 7.3 学习辅助流程

**概念学习**:
```
提问: "解释 Shopify 的 Sections 和 Blocks 的区别，并举例说明"
↓
AI 讲解
↓
追问细节
↓
要求示例代码
↓
自己实践
```

**调试辅助**:
```
遇到错误 → 复制错误信息 → 询问 AI 原因和解决方案 → 尝试解决 → 理解根本原因
```

### 7.4 AI 使用原则

**Do's (应该做)**:
- ✅ 用 AI 快速生成内容和代码骨架
- ✅ 用 AI 学习陌生概念
- ✅ 用 AI 优化文案和样式
- ✅ 用 AI 生成测试数据
- ✅ 理解 AI 生成的每一行代码
- ✅ 人工审核和优化 AI 输出

**Don'ts (不应该做)**:
- ❌ 盲目复制粘贴不理解的代码
- ❌ 期望 AI 一次生成完美代码
- ❌ 遇到错误不看就让 AI 再生成
- ❌ 不记录 AI 生成过程（面试时要讲）

---

## 8. 交付标准

### 8.1 必须交付

**1. Shopify Dev Store**
- ✅ 可访问的在线链接
- ✅ 至少 2 个产品，内容完整
- ✅ Homepage 有品牌定制
- ✅ PDP 功能完整
- ✅ 至少 1 个定制功能可见

**2. GitHub Repository**
- ✅ 清晰的目录结构
- ✅ 完整的 README.md
- ✅ 代码有适当注释
- ✅ Commit history 清晰（不是一次性提交）

**3. 文档**
- ✅ README.md（项目说明）
- ✅ PRD.md（本文档）
- ✅ learning-notes.md（学习笔记）

**4. 截图**
- ✅ 首页（桌面 + 移动）
- ✅ 产品详情页
- ✅ 定制功能特写

### 8.2 可选交付

**5. React 组件**
- 🔲 Cart Drawer 或其他交互组件
- 🔲 组件文档说明

**6. 视频 Demo**
- 🔲 3-5 分钟操作演示
- 🔲 上传到 YouTube/Loom

**7. 作品集 PDF**
- 🔲 2-3 页精美展示
- 🔲 技术架构图
- 🔲 AI 工作流图

### 8.3 质量标准

**代码质量**:
- 代码结构清晰，易于理解
- Liquid 代码遵循 Shopify 最佳实践
- CSS 类名语义化
- 没有明显 bug

**内容质量**:
- 产品文案专业，无语法错误
- 图片清晰，尺寸合适
- 品牌一致性

**用户体验**:
- 移动端适配良好
- 页面加载速度可接受
- 导航清晰，路径顺畅

**文档质量**:
- README 清晰专业
- 截图完整有代表性
- 学习笔记体现思考

---

## 9. 风险与应对

### 9.1 技术风险

**风险 1: Shopify 学习曲线陡峭**
- 概率: 高
- 影响: 时间超支，无法完成基础功能
- 应对: 
  - 充分利用 AI 辅助学习
  - 先跑通基础流程，再做定制
  - 优先用配置而非代码

**风险 2: React 集成调试困难**
- 概率: 中
- 影响: React 部分无法完成
- 应对:
  - React 作为可选项
  - 如果 2 小时内搞不定，改做 Liquid section

**风险 3: 时间不足**
- 概率: 高
- 影响: 部分功能无法完成
- 应对:
  - 严格按优先级执行
  - 砍掉可选功能
  - 用文档说明"下一步计划"

### 9.2 内容风险

**风险 4: AI 生成内容质量不稳定**
- 概率: 中
- 影响: 产品文案不专业
- 应对:
  - 多生成几次，选最好的
  - 人工润色和补充
  - 准备 prompt 模板

**风险 5: 产品图素材难找**
- 概率: 低
- 影响: 视觉效果差
- 应对:
  - 提前准备好搜索关键词
  - 用 AI 生成图片（Midjourney）
  - 实在不行用占位图

### 9.3 项目风险

**风险 6: 项目定位不清**
- 概率: 中
- 影响: 面试时讲不清项目价值
- 应对:
  - 明确定位: 学习项目 + 快速原型
  - 强调 AI 辅助能力
  - 准备"下一步计划"展示完整思维

---

## 10. 面试准备策略

### 10.1 项目介绍话术

**5 分钟版本**:

"这是我为准备 Fastlane AI 全栈体验工程师岗位，8 小时内完成的 Shopify 学习项目。

我选择了蓝牙耳机这个品类，因为研究了 Fastlane 的业务后发现，消费电子出海是重点方向，而且这个品类有很好的技术展示机会——产品参数对比、规格筛选、多语言适配等。

技术上，项目基于 Shopify 官方的 Dawn theme，我定制了产品规格对比 section，添加了 CRO 关键元素如 trust badges 和库存提示。整个开发过程充分利用了 AI 辅助——用 AI 生成产品内容、section 代码初稿、学习 Shopify 概念。

虽然时间有限，但这个项目展示了我的快速学习能力和 AI-native 工作方式。如果有更多时间，我会加入 React Cart Drawer、产品对比工具、自动化测试，以及完整的性能优化。

这个项目是我设计的 30 天完整学习计划的第一阶段 POC，展示了我对 Shopify DTC 独立站和 CRO 的理解。"

### 10.2 核心问题准备

**Q1: "你对 Shopify 了解多少？"**
→ "我是从零开始学习 Shopify 的，8 小时内理解了核心概念：
- Liquid 模板语言用于动态渲染
- Sections 是可复用的页面模块，带 schema 可配置
- Theme 架构分为 layout、templates、sections、snippets
- 产品、集合、购物车等核心对象的数据流
虽然经验有限，但我展示了快速学习和产出的能力。"

**Q2: "你用 AI 做了什么？如何保证质量？"**
→ "AI 在三个层面帮助了我：
1. 学习辅助：快速理解 Shopify 概念和 Liquid 语法
2. 内容生成：产品文案、FAQ、使用场景描述
3. 代码生成：Section 代码骨架、CSS 样式优化

质量保证方面，我的原则是：
- AI 生成初稿，人工必须审核
- 理解每一行代码在做什么，不盲目复制
- 测试所有功能，确保实际可用
- 多次迭代优化，不接受第一次输出"

**Q3: "如果再给你一周时间会做什么？"**
→ "我会按照 30 天计划的优先级推进：
Week 1: 完成完整的 5 个产品，优化 PDP 和 PLP
Week 2: 开发 React Cart Drawer 和产品对比工具
Week 3: 加入 AI 内容生成脚本和自动化测试
Week 4: 性能优化（Lighthouse 90+）、文档完善

这个一周版本会是一个完整可交付的 MVP，展示完整的 Shopify + React 技术栈和 AI 工作流。"

**Q4: "你觉得 DTC 独立站最重要的是什么？"**
→ "我认为有三个层次：
1. 基础层：产品详情页的转化能力——清晰的产品信息、信任建立、流畅的加购流程
2. 体验层：移动端体验和加载速度——大部分 DTC 流量来自移动端
3. 增长层：SEO、内容营销、邮件召回——持续获客和复购

这个项目重点展示了第一层，因为 PDP 是转化的核心战场。"

### 10.3 展示策略

**展示顺序**:
1. **快速浏览 Demo** (30 秒): 给面试官一个整体印象
2. **讲项目背景** (1 分钟): 为什么做、怎么定位
3. **技术实现** (2 分钟): 架构选择、核心功能
4. **AI 工作流** (1 分钟): 具体怎么用 AI
5. **收获和计划** (30 秒): 学到了什么、下一步

**演示技巧**:
- 准备好页面链接，快速切换
- 提前打开浏览器标签页
- 准备移动端演示（用 Chrome DevTools）
- 准备代码片段（GitHub 链接或 IDE）

**加分项**:
- 展示 AI 生成前后对比
- 展示 commit history（体现开发过程）
- 展示 learning notes（体现思考）
- 展示 30 天完整计划（体现系统性）

---

## 11. 成功标准

### 11.1 项目成功标准

- ✅ 在 8 小时内完成可演示的 Shopify 独立站
- ✅ 至少 1 个定制功能展示技术能力
- ✅ 完整的文档体现学习过程
- ✅ 能流畅讲解项目（5 分钟版本）

### 11.2 学习成功标准

- ✅ 理解 Shopify Theme 核心架构
- ✅ 会写基础 Liquid 代码
- ✅ 理解 DTC 独立站关键要素
- ✅ 建立 AI 辅助开发工作流

### 11.3 面试成功标准

- ✅ 项目能引起面试官兴趣
- ✅ 技术问题能自信回答
- ✅ 展示 AI-native 能力
- ✅ 体现快速学习能力和商业理解

---

## 12. 下一步计划

### 12.1 如果通过面试

**入职前准备 (2-4 周)**:
- 深入学习 Shopify Theme 开发
- 完成 React Cart Drawer
- 学习 Hydrogen 基础
- 补充 DTC 运营知识
- 了解 Fastlane 已有项目

### 12.2 如果项目继续迭代

**30 天完整版路线图**:

**Week 1: Shopify 深化**
- 完整的 5 个产品
- PLP 筛选和排序
- 多语言支持 (en + zh-CN)
- FAQ 页面

**Week 2: React 集成**
- Cart Drawer
- Product Quick View
- Product Comparison Tool
- 性能优化

**Week 3: AI 工具链**
- 内容生成脚本
- Section schema 生成工具
- 测试用例生成
- CI/CD pipeline

**Week 4: 质量与文档**
- Lighthouse 90+ 优化
- 自动化测试
- 完整文档
- 作品集 PDF

---

## 13. 附录

### 13.1 参考资源

**Shopify 官方文档**:
- Theme architecture: https://shopify.dev/docs/themes
- Liquid reference: https://shopify.dev/docs/api/liquid
- Dawn theme: https://github.com/Shopify/dawn

**学习资源**:
- Shopify Theme Development 教程
- Liquid 速查表
- DTC 运营最佳实践

### 13.2 工具清单

**开发工具**:
- Shopify CLI
- VS Code + Shopify Liquid 插件
- Git + GitHub
- pnpm

**设计工具**:
- Figma (可选)
- Unsplash/Pexels (免费图片)

**AI 工具**:
- Claude / Codex (代码辅助)
- ChatGPT (内容生成)
- Midjourney (图片生成，可选)

**测试工具**:
- Chrome DevTools
- Lighthouse
- Theme Check (Shopify 官方)

### 13.3 Prompt 模板库

见 `scripts/prompts/` 目录 (待项目开始后创建)

---

## 文档变更记录

| 版本 | 日期 | 变更内容 | 作者 |
|------|------|---------|------|
| v1.0 | 2026-06-15 | 初始版本创建 | AI 辅助生成 |

---

**文档结束**

祝项目顺利！记住：这不是做一个完美的产品，而是展示你的学习能力和 AI-native 工作方式。加油！🚀
