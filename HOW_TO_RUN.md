# 🚀 项目运行指南

## 重要说明

**这个项目包含两种运行方式**：

1. **完整运行** - 部署到真实 Shopify 环境（推荐用于演示）
2. **本地预览** - 查看代码和文档（立即可用）

---

## 方式 1: 部署到 Shopify（完整运行）

### 前置要求

**必需**:
- Shopify Partner 账号（免费）
- Node.js 18+ 
- pnpm 或 npm

**可选**:
- Git（已有）
- VS Code（代码编辑）

---

### Step 1: 注册 Shopify Partner 账号

**时间**: 5-10 分钟

1. 访问 https://www.shopify.com/partners
2. 点击 "Join now" 注册
3. 填写信息：
   - Email
   - 密码
   - 国家/地区
   - Partner 类型：选择 "Development"
4. 验证邮箱
5. 登录 Partner Dashboard

✅ **完成标志**: 能访问 Partner Dashboard

---

### Step 2: 创建 Development Store

**时间**: 3-5 分钟

1. 在 Partner Dashboard 中
2. 点击 "Stores" → "Add store"
3. 选择 "Development store"
4. 填写信息：
   ```
   Store name: airflow-demo (或其他名称)
   Store purpose: Test an app or theme
   Password: 设置管理员密码
   ```
5. 点击 "Create development store"
6. 等待创建完成（1-2 分钟）
7. 记录 store URL: `your-store-name.myshopify.com`

✅ **完成标志**: Store 创建成功，能访问 Admin

---

### Step 3: 安装 Shopify CLI

**时间**: 2-3 分钟

```powershell
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

✅ **完成标志**: `shopify version` 能正常显示版本号

---

### Step 4: 下载并准备项目

**时间**: 2 分钟

```powershell
# 如果还没克隆
git clone https://github.com/BakerSean168/shopify-airflow-demo.git
cd shopify-airflow-demo

# 初始化 Shopify Theme（基于 Dawn）
cd theme
shopify theme init
# 选择 Dawn theme
```

**或者使用现有项目**:
```powershell
cd D:\home\projects\shopify-airflow-demo\theme
```

---

### Step 5: 复制代码到 Theme

**时间**: 5 分钟

我们的自定义组件需要复制到 Dawn theme 中：

```powershell
# 假设你初始化的 theme 在 theme/ 目录

# 复制 Product Specs Section
Copy-Item sections\product-specs.liquid -Destination .\sections\

# 复制 Trust Badges Snippet  
Copy-Item snippets\trust-badges.liquid -Destination .\snippets\
```

**或者手动**:
1. 打开 `theme/sections/product-specs.liquid`
2. 复制全部内容
3. 在 Dawn theme 的 `sections/` 目录创建同名文件
4. 粘贴内容
5. 对 `trust-badges.liquid` 重复操作

---

### Step 6: 登录并连接 Store

**时间**: 2 分钟

```powershell
# 在 theme/ 目录
shopify auth login

# 浏览器会打开，用 Partner 账号登录

# 启动开发服务器（连接到你的 dev store）
shopify theme dev --store your-store-name

# 例如：
# shopify theme dev --store airflow-demo
```

✅ **完成标志**: 终端显示本地预览 URL，通常是 `http://127.0.0.1:9292`

---

### Step 7: 录入产品

**时间**: 10-15 分钟

**方式 A: 手动录入（推荐，学习过程）**

1. 打开 `your-store-name.myshopify.com/admin`
2. 登录（用你设置的密码）
3. 进入 Products → Add product

**产品 1: AirFlow Lite**
- 打开 `products/airflow-lite.json`
- 复制以下内容：
  ```
  Title: AirFlow Lite
  Price: $49
  Description: [复制 content.description]
  ```
- 上传 2-3 张产品图（从 Unsplash 搜索 "wireless earbuds"）
- 点击 Save

**产品 2: AirFlow Pro**
- 打开 `products/airflow-pro.json`
- 同样流程
- Price: $129

**方式 B: CSV 导入（快速）**

1. 转换 JSON 为 CSV（需要手动或用脚本）
2. Products → Import → 上传 CSV

---

### Step 8: 添加 Sections 到页面

**时间**: 5 分钟

1. 在开发服务器运行时，浏览器打开本地 URL
2. 点击右下角的 "Customize" 按钮（或在 Admin 中进入 Theme Editor）
3. 进入任一 Product 页面
4. 点击 "Add section"
5. 找到 "Product Specifications" section
6. 添加并配置：
   ```
   Heading: Technical Specifications
   添加 blocks:
   - Battery: 🔋 | Battery Life | 40 hours
   - Bluetooth: 📡 | Bluetooth | 5.3
   - Waterproof: 💧 | Waterproof | IPX4
   - Weight: ⚖️ | Weight | 4.2g
   - Codec: 🎵 | Codec | AAC, SBC
   - Charging: 🔌 | Charging | USB-C
   ```
7. 保存

**添加 Trust Badges**:

需要编辑产品模板：
1. 在 Theme Editor 左侧 Sections 列表中
2. 找到 Product information section
3. 在其下方添加 "Custom Liquid" section
4. 输入：`{% render 'trust-badges' %}`
5. 保存

---

### Step 9: 查看效果

**时间**: 即时

1. 在浏览器中访问本地预览 URL
2. 浏览产品页面
3. 查看：
   - ✅ Product Specs Section 显示
   - ✅ Trust Badges 显示
   - ✅ 响应式布局工作
   - ✅ Hover 效果正常

**测试响应式**:
- 按 F12 打开 DevTools
- 点击 "Toggle device toolbar"
- 切换到手机视图
- 验证 2 列布局

---

### Step 10: 部署到线上

**时间**: 2 分钟

```powershell
# 在 theme/ 目录
shopify theme push

# 确认后，Theme 会部署到你的 dev store
```

现在可以访问 `your-store-name.myshopify.com` 查看线上版本！

---

## 方式 2: 本地预览（快速查看）

如果只想查看代码和文档，无需 Shopify 环境：

### 查看代码

```powershell
# 打开项目
cd D:\home\projects\shopify-airflow-demo

# 用 VS Code 查看
code .

# 主要文件：
# - theme/sections/product-specs.liquid
# - theme/snippets/trust-badges.liquid
# - products/airflow-lite.json
# - products/airflow-pro.json
```

### 查看文档

```powershell
# 在浏览器中打开 README
start README.md

# 查看完整文档
start docs\
```

**关键文档**:
- `README.md` - 项目概览
- `FINAL_SUMMARY.md` - 最终总结
- `docs/PRD.md` - 完整需求文档
- `docs/learning-notes.md` - 学习笔记
- `docs/screenshots/README.md` - 视觉说明

### 查看组件效果说明

打开 `docs/screenshots/README.md`，里面有详细的：
- 组件布局图
- 响应式行为
- 代码渲染示例
- 预期视觉效果

---

## 常见问题

### Q: 必须部署到 Shopify 才能运行吗？

**A**: 不是。有两种方式：

1. **查看代码和文档** - 立即可用，无需任何设置
2. **部署到 Shopify** - 看到实际运行效果，需要 30-40 分钟设置

对于面试展示，方式 1（展示代码）+ `docs/screenshots/README.md`（视觉说明）已经足够。

### Q: 我没有产品图片怎么办？

**A**: 三个方案：

1. **Unsplash** (推荐): https://unsplash.com/s/photos/wireless-earbuds
2. **Pexels**: https://www.pexels.com/search/bluetooth-headphones/
3. **占位图**: https://via.placeholder.com/1200x1200

### Q: 开发服务器启动失败？

**A**: 检查：

```powershell
# 确认在 theme/ 目录
pwd

# 确认已登录
shopify auth logout
shopify auth login

# 确认 store 名称正确
shopify theme dev --store your-exact-store-name
```

### Q: Section 没有出现在 Theme Editor？

**A**: 检查：

1. 文件是否在正确位置（`sections/product-specs.liquid`）
2. 文件名是否正确
3. Liquid 语法是否有错误
4. 刷新 Theme Editor 页面

### Q: 可以用真实 Shopify 账号吗？

**A**: 可以，但不推荐。Development Store 是免费的，专门用于测试。

### Q: 需要付费吗？

**A**: 不需要。Shopify Partner 账号和 Development Store 都是免费的。

---

## 快速启动命令总结

### 完整部署（首次）

```powershell
# 1. 安装 CLI
npm install -g @shopify/cli @shopify/theme

# 2. 克隆项目
git clone https://github.com/BakerSean168/shopify-airflow-demo.git
cd shopify-airflow-demo\theme

# 3. 登录
shopify auth login

# 4. 启动开发服务器
shopify theme dev --store your-store-name

# 5. 浏览器打开显示的 URL
```

### 后续开发

```powershell
# 进入 theme 目录
cd D:\home\projects\shopify-airflow-demo\theme

# 启动开发服务器
shopify theme dev --store your-store-name

# 修改代码 → 浏览器自动刷新
```

### 部署到线上

```powershell
cd D:\home\projects\shopify-airflow-demo\theme
shopify theme push
```

---

## 面试演示建议

### 选项 1: 代码演示（无需 Shopify）

**时间**: 即时
**难度**: 简单

1. 打开 VS Code 展示项目结构
2. 打开 `product-specs.liquid` 讲解代码
3. 打开 `docs/screenshots/README.md` 展示效果
4. 打开 `products/airflow-lite.json` 展示内容

**优点**: 无需设置，随时可用

### 选项 2: 实际运行（有 Shopify）

**时间**: 需提前设置
**难度**: 中等

1. 提前部署到 dev store
2. 面试时打开线上链接
3. 实际操作 Theme Editor
4. 展示响应式效果

**优点**: 更有说服力，展示实际运行

### 推荐方案

**面试前**:
- 代码 + 文档准备好
- 如果有时间，部署一个 demo

**面试中**:
- 先展示代码（讲技术）
- 如果有 demo，再展示运行（讲效果）
- 两种方式都有说服力

---

## 时间投入估算

| 任务 | 首次 | 后续 |
|------|------|------|
| 注册账号 | 10 min | - |
| 创建 Store | 5 min | - |
| 安装 CLI | 3 min | - |
| 下载项目 | 2 min | - |
| 启动服务器 | 2 min | 1 min |
| 录入产品 | 15 min | - |
| 配置 Sections | 5 min | - |
| **首次总计** | **~40 min** | |
| **后续启动** | | **1 min** |

---

## 下一步

### 如果你想实际运行

1. 按照 "方式 1" 的步骤执行
2. 遇到问题参考"常见问题"
3. 40 分钟后你就能看到实际效果

### 如果只是查看代码

1. 打开 VS Code 查看代码文件
2. 阅读 `docs/screenshots/README.md` 了解效果
3. 这已经足够面试展示

### 如果准备面试

1. 熟悉代码结构
2. 练习讲解思路
3. 准备 demo（可选但加分）

---

**🎯 选择适合你的方式，祝你成功！**

**有问题随时查阅本文档或 `docs/` 目录下的其他指南。**
