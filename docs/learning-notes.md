# AirFlow 学习笔记

**项目**: Shopify DTC 独立站学习项目  
**时间**: 2026-06-15  
**学习时长**: 6 小时（实际开发时间）  
**技术栈**: Shopify Theme (Dawn), Liquid, Product Management

---

## 📚 学习目标回顾

### 原始目标
8 小时内从零学习 Shopify Theme 开发，搭建蓝牙耳机品牌 DTC 独立站原型。

### 实际完成
- ✅ 理解 Shopify Theme 架构
- ✅ 掌握 Liquid 模板语言基础
- ✅ 开发了 2 个生产级组件
- ✅ 创建了 2 个完整产品数据包
- ✅ 实践了 AI-native 开发工作流
- ✅ 理解了 DTC 电商核心要素

---

## 💡 核心概念理解

### 1. Shopify Theme 架构

**我的理解**:
Shopify Theme 是一个**模块化的页面构建系统**，核心思想是"配置优于代码"。

**类比**:
- `layout/theme.liquid` → 房子的地基和框架
- `templates/` → 房间的布局图纸（JSON 格式）
- `sections/` → 可移动的家具模块
- `snippets/` → 小装饰品

**为什么这样设计？**
让非技术的商家能在 Theme Editor 中拖拽配置，不需要写代码。

**关键洞察**:
- Sections 是 Shopify 的核心抽象
- Schema 让代码变成可视化工具
- Blocks 机制让 sections 更灵活

---

### 2. Liquid 模板语言

**三种语法**:
- `{{ variable }}` - 输出
- `{% logic %}` - 逻辑控制
- `{% comment %}` - 注释

**最有用的功能**:
1. Filters: `{{ price | money }}`
2. 对象访问: `{{ product.title }}`
3. 循环: `{% for block in section.blocks %}`

**踩过的坑**:
- Liquid 是服务端渲染
- 变量有作用域限制
- 需要理解 Shopify 对象模型

---

### 3. Sections 机制

Section = Liquid 模板 + JSON schema 配置

**我开发的 Product Specs Section**:
- 用 blocks 让用户添加多个规格
- Presets 提供默认值
- 响应式网格布局

**Blocks 的威力**:
商家可以在 Theme Editor 中添加/删除/排序，无需写代码。

---

## 🤖 AI 使用心得

### AI 擅长什么
- 生成结构化内容
- 代码模板生成
- 概念快速解释

### AI 不擅长什么
- 理解业务上下文
- 第一次就完美
- 调试复杂逻辑

### 最佳实践
- ✅ 明确需求，分步提问
- ✅ 理解生成的每行代码
- ✅ 多次迭代优化
- ❌ 不要盲目复制

---

## 🎯 关键收获

### 技术层面
1. Sections 是核心抽象
2. 响应式设计至关重要
3. 性能优化有具体方法

### AI 使用层面
1. AI 是加速器，不是替代品
2. Prompt 工程很重要
3. 迭代是关键

### 商业理解
1. DTC 独立站核心是 PDP
2. 信任建立至关重要
3. 产品差异化策略

---

## 💭 反思与感悟

**最大收获**: 快速学习不是天赋，是方法。

**关键方法**:
1. 明确目标
2. 分解任务
3. 快速执行（边做边学）
4. 充分利用 AI
5. 反思总结

---

**作者**: AI-native 学习者  
**完成时间**: 2026-06-15  
**一句话总结**: 用 AI 辅助，6 小时从零到有，证明快速学习能力。
