# MQ's Portfolio - 个人职业网站

一个基于 Decap CMS + Git Gateway 的零代码管理个人职业网站，采用 Apple 官网深空灰极简美学设计。

## 设计特点

- **色彩系统**：深空灰蓝 (#0f172a) 主背景，冰蓝 (#7ec8e3) 强调色
- **字体系统**：中文优先，最小 font-weight: 400，确保可读性
- **布局风格**：极端留白，玻璃态卡片，直角设计
- **动画效果**：滚动触发 reveal 动画，stagger 延迟

## 部署到 Netlify（推荐）

### 步骤 1：上传到 GitHub

1. 在 GitHub 创建新仓库，命名为 `my-portfolio`
2. 将所有文件上传到仓库根目录：
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/yourusername/my-portfolio.git
   git push -u origin main
   ```

### 步骤 2：连接到 Netlify

1. 登录 [netlify.com](https://netlify.com)，点击 "Add new site" → "Import an existing project"
2. 选择 GitHub，授权并选择你的仓库
3. 构建设置保持默认：
   - Build command:（留空，纯静态网站）
   - Publish directory: `/`

### 步骤 3：开启身份认证（CMS登录）

1. 在 Netlify 后台进入 **Site settings → Identity**
2. 点击 **Enable Identity**
3. 进入 **Settings & options → Registration**，选择 **"Invite only"**（安全）
4. 进入 **Services → Git Gateway**，点击 **Enable Git Gateway**
5. 在 **Identity** 标签页添加你的邮箱作为用户，设置密码

### 步骤 4：访问网站

- **网站地址**：`https://xxx.netlify.app`
- **后台地址**：`https://xxx.netlify.app/admin`
- 使用步骤 3 设置的邮箱密码登录后台

## 使用说明

### 修改内容

1. 访问 `/admin` 进入 CMS 后台
2. 选择要编辑的栏目（研究案例、投资观点、职业经历等）
3. 点击内容项进行编辑
4. 点击 "Publish" 发布更改

### 上传图片

- 在编辑器中直接拖拽上传图片
- 图片自动保存到 `assets/uploads/` 目录

### 添加新的研究案例

1. 进入 CMS → Research Lab
2. 点击 "New Research Lab"
3. 填写标题、问题、洞察、数据等字段
4. 设置排序数字（越大越靠前显示）
5. 点击 "Publish"

### 添加新的职业经历

1. 进入 CMS → Experience
2. 点击 "New Experience"
3. 填写公司、职位、时间、描述
4. 设置排序数字（建议按时间倒序）
5. 点击 "Publish"

## 文件结构

```
my-portfolio/
├── index.html              # 主页面（动态渲染引擎）
├── admin/
│   ├── index.html         # CMS 登录界面
│   └── config.yml         # CMS 字段配置
├── content/               # 所有可编辑内容
│   ├── hero.json          # 首页介绍
│   ├── research/          # 研究案例（支持多个）
│   ├── thesis/            # 投资观点
│   ├── experience/        # 职业经历
│   ├── education/         # 教育背景
│   ├── notes/             # 研究随笔
│   ├── personal.json      # 工作之外
│   └── contact.json       # 联系方式
├── assets/
│   └── uploads/           # 图片上传目录
└── README.md              # 本文件
```

## 本地预览

由于使用本地文件读取（fetch），需要在本地服务器预览：

```bash
# 使用 Python
python -m http.server 8000

# 或使用 Node.js
npx serve .

# 然后访问 http://localhost:8000
```

## 自定义配置

### 修改网站标题

编辑 `index.html` 中的 `<title>` 标签。

### 修改配色

编辑 `index.html` 中的 CSS 变量：

```css
:root {
  --bg-primary: #0f172a;      /* 主背景 */
  --accent: #7ec8e3;           /* 强调色 */
  /* ... */
}
```

### 修改 CMS 字段

编辑 `admin/config.yml`，添加或修改字段配置。

## 技术栈

- **前端**：原生 HTML + Tailwind CSS CDN
- **CMS**：Decap CMS (原 Netlify CMS) v3.0
- **Markdown 解析**：marked.js
- **部署**：Netlify（免费托管 + 身份认证）

## 注意事项

1. **浏览器兼容性**：建议使用 Chrome、Firefox、Safari 最新版本
2. **图片格式**：推荐 JPG/PNG，大小控制在 2MB 以内
3. **内容备份**：所有内容保存在 Git 仓库中，天然有版本控制
4. **隐私保护**：CMS 设置为 Invite only，避免未授权访问

## 故障排除

### CMS 登录失败

1. 确认 Netlify Identity 已启用
2. 确认 Git Gateway 已启用
3. 确认用户已添加到 Identity

### 内容不显示

1. 检查浏览器控制台是否有 404 错误
2. 确认 JSON 文件格式正确（无语法错误）
3. 确认文件路径正确（区分大小写）

### 图片上传失败

1. 确认 media_folder 配置正确
2. 检查文件大小是否超过限制
3. 确认 Git Gateway 有写入权限

## 许可证

MIT License - 可自由使用和修改。

---

**作者**：李梦琪 / Mengqi Li  
**联系方式**：mengqili1024@qq.com
