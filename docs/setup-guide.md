# 环境搭建指南

## 前置准备

### 1. 注册 Shopify Partner 账号

1. 访问 https://www.shopify.com/partners
2. 点击 "Join now" 注册
3. 填写信息：
   - Email
   - 密码
   - 国家/地区：选择你所在地区
   - Partner 类型：选择 "Developer" 或 "Designer"
4. 验证邮箱
5. 登录 Partner Dashboard

### 2. 创建 Development Store

在 Partner Dashboard:
1. 点击 "Stores" → "Add store"
2. 选择 "Development store"
3. 填写信息：
   - Store name: `airflow-demo` (或其他名称)
   - Store purpose: "Test an app or theme"
   - Password: 设置管理员密码
4. 点击 "Create development store"
5. 等待创建完成（约 1-2 分钟）
6. 记录下 store URL: `your-store-name.myshopify.com`

### 3. 安装 Shopify CLI

**Windows (PowerShell)**:
```powershell
# 确保已安装 Node.js (v18+)
node --version

# 安装 Shopify CLI
npm install -g @shopify/cli @shopify/theme

# 验证安装
shopify version
```

**如果遇到权限问题**:
```powershell
# 以管理员身份运行 PowerShell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```

---

## 初始化项目

### Step 1: 初始化 Theme

```powershell
# 进入项目目录
cd D:\home\projects\shopify-airflow-demo

# 初始化 Shopify theme（选择 Dawn）
shopify theme init theme

# 提示选择 theme 时，选择 "Dawn"
```

### Step 2: 登录并连接 Store

```powershell
cd theme

# 登录 Shopify
shopify auth login

# 这会打开浏览器，使用你的 Partner 账号登录
```

### Step 3: 启动开发服务器

```powershell
# 启动本地开发服务器
shopify theme dev --store your-store-name

# 终端会显示本地预览 URL，通常是:
# http://127.0.0.1:9292
```

### Step 4: 验证环境

1. 在浏览器打开显示的本地 URL
2. 应该能看到 Dawn theme 的默认首页
3. 修改任何文件，浏览器应自动刷新

---

## 项目结构说明

初始化后的目录结构:
```
shopify-airflow-demo/
├── theme/                    # Shopify Theme
│   ├── assets/              # CSS, JS, images
│   ├── config/              # Theme settings
│   ├── layout/              # Page layouts (theme.liquid)
│   ├── locales/             # Translation files
│   ├── sections/            # Reusable sections
│   ├── snippets/            # Small code snippets
│   ├── templates/           # Page templates (JSON)
│   └── .shopifyignore       # Git-like ignore file
└── docs/                    # 文档
    ├── PRD.md
    └── setup-guide.md       # 本文件
```

---

## 快速 Shopify 概念学习

### Liquid 模板语言

**基础语法**:
```liquid
<!-- 输出变量 -->
{{ product.title }}
{{ product.price | money }}

<!-- 控制流 -->
{% if product.available %}
  <button>Add to cart</button>
{% else %}
  <p>Sold out</p>
{% endif %}

<!-- 循环 -->
{% for product in collection.products %}
  <h3>{{ product.title }}</h3>
{% endfor %}

<!-- 注释 -->
{% comment %} This is a comment {% endcomment %}
```

**常用对象**:
- `product`: 当前产品
- `collection`: 产品集合
- `cart`: 购物车
- `shop`: 店铺信息
- `customer`: 客户信息

**常用过滤器**:
- `{{ price | money }}`: 格式化价格
- `{{ image | img_url: 'large' }}`: 生成图片 URL
- `{{ text | truncate: 100 }}`: 截断文本

### Sections

Sections 是可复用的页面模块，有两部分：
1. **Liquid 代码**: 渲染逻辑
2. **Schema**: 配置界面

示例 section 结构:
```liquid
<!-- sections/hero.liquid -->
<div class="hero">
  <h1>{{ section.settings.title }}</h1>
  <p>{{ section.settings.subtitle }}</p>
</div>

{% schema %}
{
  "name": "Hero",
  "settings": [
    {
      "type": "text",
      "id": "title",
      "label": "Title",
      "default": "Welcome"
    },
    {
      "type": "textarea",
      "id": "subtitle",
      "label": "Subtitle"
    }
  ]
}
{% endschema %}
```

### Templates

Templates 定义页面使用哪些 sections。

JSON template 示例 (`templates/index.json`):
```json
{
  "sections": {
    "hero": {
      "type": "hero",
      "settings": {
        "title": "Premium Audio Experience"
      }
    },
    "featured_products": {
      "type": "featured-collection"
    }
  },
  "order": ["hero", "featured_products"]
}
```

---

## 常用命令

```powershell
# 启动开发服务器
shopify theme dev

# 推送到线上 store (发布)
shopify theme push

# 拉取线上 theme
shopify theme pull

# 分享预览链接
shopify theme share

# 检查 theme 代码质量
shopify theme check
```

---

## 故障排查

### 问题 1: `shopify` 命令找不到
**解决**: 
```powershell
# 检查 npm global bin 路径
npm config get prefix

# 确保该路径在系统 PATH 中
# 或重新安装
npm install -g @shopify/cli @shopify/theme --force
```

### 问题 2: 无法连接到 store
**解决**:
```powershell
# 重新登录
shopify auth logout
shopify auth login

# 确保 store 名称正确
shopify theme dev --store your-exact-store-name
```

### 问题 3: 文件修改不生效
**解决**:
- 检查是否在 `theme/` 目录下运行命令
- 尝试手动刷新浏览器
- 重启开发服务器

---

## 下一步

环境搭建完成后，进入 Phase 2: 产品录入

查看 `docs/product-content-guide.md` 了解如何用 AI 生成产品内容。
