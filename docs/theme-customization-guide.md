# Theme 定制开发指南

## Phase 3-5: Theme 定制、功能开发、CRO 元素

---

## Part 1: 品牌基础定制 (30 分钟)

### 修改品牌信息

**在 Shopify Admin**:
1. Online Store → Themes → Customize
2. Theme settings (左下角齿轮图标)

**要修改的内容**:

**Logo & Brand**:
- Store name: "AirFlow"
- Tagline: "Premium Audio Experience"
- Favicon: (可选) 上传一个简单的 icon

**Colors**:
```
推荐配色方案 (科技感):
- Primary: #0066FF (科技蓝)
- Secondary: #000000 (黑色)
- Accent: #00D4FF (亮蓝)
- Background: #FFFFFF
- Text: #1A1A1A
```

或

```
推荐配色方案 (高级感):
- Primary: #1A1A1A (深灰黑)
- Secondary: #4A4A4A (中灰)
- Accent: #FF6B35 (橙色点缀)
- Background: #FFFFFF
- Text: #1A1A1A
```

**Typography**:
- Heading font: "Inter" 或 "DM Sans" (现代简洁)
- Body font: "Inter" 或 "System"

### 定制 Homepage

**在 Theme Customize 界面**:

**Hero Section**:
1. 选择 "Image banner" section
2. 设置:
   - Heading: "Premium Audio Experience"
   - Subheading: "High-quality wireless earbuds for every moment"
   - Button text: "Shop Now"
   - Button link: `/collections/all`
   - 上传一张主视觉图（可用产品图或找一张大图）

**Featured Products**:
1. 添加 "Featured collection" section
2. 选择 collection: "All products"
3. Heading: "Our Products" 或 "Discover AirFlow"
4. 显示 2-3 个产品

**Image with Text** (品牌故事):
1. 添加 "Image with text" section
2. Heading: "Designed for Life"
3. Text: (用 AI 生成品牌故事，2-3 段)
   ```
   Prompt: "为蓝牙耳机品牌 AirFlow 写一段品牌故事 (2-3 段)，
   强调：为日常生活设计、注重性价比、简约设计哲学。
   风格：简洁、真诚、不浮夸"
   ```

---

## Part 2: 定制 Product Specs Section (2 小时)

这是核心定制功能，展示你的 Shopify 开发能力。

### Step 1: 创建 Section 文件

在 `theme/sections/` 目录创建 `product-specs.liquid`

### Step 2: 用 AI 生成代码

**AI Prompt**:
```
写一个 Shopify Liquid section，展示蓝牙耳机的技术规格参数表。

要求:
1. 包含完整的 schema，可以在 theme editor 中配置以下参数:
   - 标题 (heading)
   - 多个规格项，每个包含:
     - 图标/emoji
     - 参数名 (如 "电池续航")
     - 参数值 (如 "40 小时")

2. 布局:
   - 使用网格布局，桌面 3 列，移动端 2 列
   - 每个参数项显示图标 + 名称 + 值
   - 简洁现代的设计

3. 样式:
   - 使用 Tailwind-like 的 utility classes
   - 或内联 CSS
   - 响应式设计

4. 代码要有清晰注释

请给出完整的 .liquid 文件代码。
```

### Step 3: 保存并测试

将 AI 生成的代码保存到文件后:

```powershell
# 在 theme/ 目录下
# 文件会自动同步到开发服务器
```

### Step 4: 添加到产品模板

1. 在 Theme Customize 界面
2. 打开任一产品页
3. 点击 "Add section"
4. 找到你的 "Product Specs" section
5. 添加并配置参数

### 示例 Section 代码结构

如果 AI 生成的不理想，这是一个参考模板:

```liquid
<!-- sections/product-specs.liquid -->
<div class="product-specs">
  <h2>{{ section.settings.heading }}</h2>
  
  <div class="specs-grid">
    {% for block in section.blocks %}
      <div class="spec-item">
        <span class="spec-icon">{{ block.settings.icon }}</span>
        <p class="spec-name">{{ block.settings.name }}</p>
        <p class="spec-value">{{ block.settings.value }}</p>
      </div>
    {% endfor %}
  </div>
</div>

<style>
  .product-specs {
    padding: 3rem 1rem;
    max-width: 1200px;
    margin: 0 auto;
  }
  
  .product-specs h2 {
    text-align: center;
    margin-bottom: 2rem;
    font-size: 1.875rem;
    font-weight: 600;
  }
  
  .specs-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
    gap: 2rem;
  }
  
  .spec-item {
    text-align: center;
    padding: 1.5rem;
    border: 1px solid #e5e5e5;
    border-radius: 8px;
  }
  
  .spec-icon {
    font-size: 2rem;
    display: block;
    margin-bottom: 0.5rem;
  }
  
  .spec-name {
    font-weight: 600;
    margin-bottom: 0.25rem;
    color: #4a4a4a;
  }
  
  .spec-value {
    font-size: 1.125rem;
    color: #1a1a1a;
  }
  
  @media (max-width: 768px) {
    .specs-grid {
      grid-template-columns: repeat(2, 1fr);
      gap: 1rem;
    }
  }
</style>

{% schema %}
{
  "name": "Product Specifications",
  "settings": [
    {
      "type": "text",
      "id": "heading",
      "label": "Heading",
      "default": "Technical Specifications"
    }
  ],
  "blocks": [
    {
      "type": "spec",
      "name": "Specification",
      "settings": [
        {
          "type": "text",
          "id": "icon",
          "label": "Icon (emoji)",
          "default": "🔋"
        },
        {
          "type": "text",
          "id": "name",
          "label": "Spec Name",
          "default": "Battery Life"
        },
        {
          "type": "text",
          "id": "value",
          "label": "Spec Value",
          "default": "40 hours"
        }
      ]
    }
  ],
  "presets": [
    {
      "name": "Product Specifications",
      "blocks": [
        {
          "type": "spec",
          "settings": {
            "icon": "🔋",
            "name": "Battery Life",
            "value": "40 hours"
          }
        },
        {
          "type": "spec",
          "settings": {
            "icon": "📡",
            "name": "Bluetooth",
            "value": "5.3"
          }
        },
        {
          "type": "spec",
          "settings": {
            "icon": "💧",
            "name": "Waterproof",
            "value": "IPX4"
          }
        },
        {
          "type": "spec",
          "settings": {
            "icon": "⚖️",
            "name": "Weight",
            "value": "4.2g"
          }
        },
        {
          "type": "spec",
          "settings": {
            "icon": "🎵",
            "name": "Codec",
            "value": "AAC, SBC"
          }
        },
        {
          "type": "spec",
          "settings": {
            "icon": "🔌",
            "name": "Charging",
            "value": "USB-C"
          }
        }
      ]
    }
  ]
}
{% endschema %}
```

---

## Part 3: Trust Badges (30 分钟)

### Step 1: 创建 Snippet

在 `theme/snippets/` 创建 `trust-badges.liquid`

### Step 2: 用 AI 生成代码

**AI Prompt**:
```
写一个 Shopify snippet，显示 4 个信任标识（trust badges）：

1. 30 天无理由退换
2. 全球免费配送
3. 官方质保 1 年
4. 安全加密支付

要求:
- 使用图标（emoji 或 SVG）+ 文字
- 响应式网格布局，桌面 4 列，移动端 2 列
- 简洁现代风格
- 适合放在产品详情页

请给出完整的 snippet 代码。
```

### Step 3: 引入到产品页

在产品模板中添加:

**方法 1: 通过 Theme Customize**
1. 打开产品页编辑
2. 添加 "Custom Liquid" section
3. 输入: `{% render 'trust-badges' %}`

**方法 2: 编辑产品模板**
编辑 `sections/main-product.liquid`，在合适位置添加:
```liquid
{% render 'trust-badges' %}
```

### 示例 Snippet 代码

```liquid
<!-- snippets/trust-badges.liquid -->
<div class="trust-badges">
  <div class="badge">
    <span class="badge-icon">🔄</span>
    <p class="badge-text">30 Day Returns</p>
  </div>
  <div class="badge">
    <span class="badge-icon">🚚</span>
    <p class="badge-text">Free Shipping</p>
  </div>
  <div class="badge">
    <span class="badge-icon">✅</span>
    <p class="badge-text">1 Year Warranty</p>
  </div>
  <div class="badge">
    <span class="badge-icon">🔒</span>
    <p class="badge-text">Secure Payment</p>
  </div>
</div>

<style>
  .trust-badges {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 1rem;
    padding: 2rem 0;
    margin: 2rem 0;
    border-top: 1px solid #e5e5e5;
    border-bottom: 1px solid #e5e5e5;
  }
  
  .badge {
    text-align: center;
  }
  
  .badge-icon {
    font-size: 2rem;
    display: block;
    margin-bottom: 0.5rem;
  }
  
  .badge-text {
    font-size: 0.875rem;
    font-weight: 500;
    color: #4a4a4a;
  }
  
  @media (max-width: 768px) {
    .trust-badges {
      grid-template-columns: repeat(2, 1fr);
    }
  }
</style>
```

---

## Part 4: 库存提示 (可选，20 分钟)

### 创建 `snippets/stock-indicator.liquid`

**AI Prompt**:
```
写一个 Shopify snippet，根据产品库存数量显示提示信息：

- 库存 < 10: 显示 "仅剩 X 件" (红色警示)
- 库存 10-50: 显示 "库存有限" (橙色)
- 库存 > 50: 显示 "库存充足" (绿色)

要求:
- 自动读取 product.variants.first.inventory_quantity
- 有颜色和图标
- 简洁设计

请给出完整代码。
```

### 引入到产品页

在 Add to Cart 按钮附近添加:
```liquid
{% render 'stock-indicator', product: product %}
```

---

## Part 5: FAQ Accordion (可选，30 分钟)

### 创建 `sections/product-faq.liquid`

**AI Prompt**:
```
写一个 Shopify section，展示产品 FAQ（常见问题），使用 accordion 折叠效果。

要求:
1. Schema 可以添加多个问答
2. 点击问题展开答案
3. 使用纯 JavaScript (不依赖外部库)
4. 简洁动画效果
5. 响应式设计

请给出完整代码 (Liquid + CSS + JS)。
```

---

## Part 6: 响应式检查 (30 分钟)

### 测试清单

使用 Chrome DevTools (F12 → Toggle device toolbar):

**桌面端** (1920x1080):
- [ ] Hero banner 清晰完整
- [ ] 产品网格 3-4 列
- [ ] 导航栏不换行
- [ ] 产品详情页图片和信息左右布局

**平板** (768x1024):
- [ ] 产品网格 2 列
- [ ] 导航栏收起为汉堡菜单
- [ ] 所有文字可读

**手机** (375x667, iPhone SE):
- [ ] 产品网格 1-2 列
- [ ] 图片不超出屏幕
- [ ] 按钮大小适合点击（最小 44x44px）
- [ ] 文字大小不小于 14px

### 常见问题修复

**问题 1: 图片太大超出屏幕**
```liquid
<!-- 使用 Shopify 图片过滤器 -->
{{ product.featured_image | img_url: 'large' | img_tag }}

<!-- 或添加 CSS -->
<style>
  img {
    max-width: 100%;
    height: auto;
  }
</style>
```

**问题 2: 文字太小**
```css
/* 确保基础字体大小 */
body {
  font-size: 16px;
}

@media (max-width: 768px) {
  body {
    font-size: 14px;
  }
  
  h1 {
    font-size: 1.75rem;
  }
}
```

---

## 时间检查点

到这里，你应该完成了:
- ✅ 环境搭建 (1 小时)
- ✅ 产品录入 (1-1.5 小时)
- ✅ 品牌定制 (0.5 小时)
- ✅ Product Specs Section (1-2 小时)
- ✅ Trust Badges (0.5 小时)
- ✅ 响应式检查 (0.5 小时)

**总计**: 约 5-6 小时

**剩余时间**: 2-3 小时用于文档、截图、面试准备

---

## 下一步

1. **截图**: 关键页面的桌面和移动端截图
2. **部署**: 推送到线上 store
3. **文档**: 写 README 和学习笔记

查看 `docs/documentation-guide.md`
