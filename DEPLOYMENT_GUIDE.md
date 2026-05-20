# 📖 MatchPredict 完整部署指南

这是 MatchPredict 足球比赛预测系统的完整部署指南。

---

## 📚 目录

- [环境要求](#环境要求)
- [Vercel 部署](#vercel-部署)
- [自定义域名](#自定义域名)
- [环境变量配置](#环境变量配置)
- [性能优化](#性能优化)
- [故障排除](#故障排除)

---

## 环境要求

### 必需条件

- ✅ GitHub 账号
- ✅ 互联网连接
- ✅ 浏览器（Chrome、Safari、Firefox 等）

### 可选条件

- 📧 Google 账号（用于 Gemini API）
- 💳 信用卡（购买自定义域名）
- 🗄️ PostgreSQL 数据库（用于数据存储）

---

## Vercel 部署

### 什么是 Vercel？

Vercel 是一个云平台，可以：
- 🚀 一键部署 Python/Node.js 应用
- 🌍 全球 CDN 加速
- 🔒 自动 HTTPS
- 📊 实时监控和日志
- 🆓 免费层足够个人使用

### 部署步骤

#### 1. 登录 Vercel

访问 https://vercel.com

- 点击 **"Sign Up"**
- 选择 **"Continue with GitHub"**
- 授权 Vercel 访问你的 GitHub 账号

#### 2. 导入项目

点击 **"Add New"** → **"Project"**

- 选择 **"Import Git Repository"**
- 搜索 `MatchPredict`
- 点击你的 fork 项目：`yysyys-create/MatchPredict`
- 点击 **"Import"**

#### 3. 配置项目

在项目配置页面：

**项目名称：**
```
matchpredict （或任何你想要的名称）
```

**根目录：**
```
./ （默认，不需要修改）
```

**框架预设：**
```
Python （应自动检测）
```

#### 4. 配置环境变量

点击 **"Environment Variables"** 部分，添加以下变量：

**必需：**
```
SECRET_KEY = [你生成的密钥]
```

**可选：**
```
GEMINI_API_KEY = [你的 API 密钥]
GEMINI_MODEL = gemini-2.0-flash-exp
DATABASE_URL = [你的数据库连接字符串]
```

#### 5. 部署

点击 **"Deploy"** 按钮。

Vercel 会：
1. 安装依赖（requirements.txt）
2. 构建应用
3. 部署到服务器
4. 生成 URL

部署通常需要 2-3 分钟。

#### 6. 获取 URL

部署完成后，你会看到：
```
https://matchpredict-xxxxx.vercel.app
```

这就是你的网站地址！

---

## 自定义域名

### 为什么需要自定义域名？

- 🎯 更专业的外观
- 🔍 更容易记住
- 📧 可以创建品牌邮箱
- 📊 更容易统计用户数据

### 购买域名

#### 选择域名注册商

| 服务商 | 网址 | 特点 |
|--------|------|------|
| Namecheap | https://www.namecheap.com | 便宜，支持中文 |
| GoDaddy | https://www.godaddy.com | 知名，功能全 |
| 阿里云 | https://wanwang.aliyun.com | 国内，支持中文 |
| Google Domains | https://domains.google | 简单易用 |

#### 搜索和购买

1. 打开注册商网站
2. 搜索你想要的域名
   - 示例：`football-predict.com`
   - 示例：`aifootball.cn`
   - 示例：`matchpredict.co`
3. 选择 1 年或多年的套餐
4. 完成支付

### 配置在 Vercel 中

#### 步骤 1：添加域名

1. 进入 Vercel 项目
2. 点击 **"Settings"** 标签
3. 选择 **"Domains"**
4. 点击 **"Add Domain"**
5. 输入你的域名
6. 点击 **"Add"**

#### 步骤 2：配置 DNS

Vercel 会显示 DNS 配置选项。有两种方式：

##### 方式 A：使用 Vercel Nameservers（推荐）

1. 复制 Vercel 提供的 4 个 Nameservers
2. 登录你的域名注册商
3. 进入 DNS 设置
4. 将 Nameservers 改为 Vercel 提供的
5. 等待 DNS 生效（通常 1-24 小时）

**示例 Vercel Nameservers：**
```
ns1.vercel-dns.com
ns2.vercel-dns.com
```

##### 方式 B：手动 CNAME 记录

如果你的域名已有其他 DNS 记录：

1. 不改变 Nameservers
2. 添加 CNAME 记录指向 Vercel
3. Vercel 会显示具体的 CNAME 值

**示例 CNAME 记录：**
```
Host: www
Type: CNAME
Value: cname.vercel-dns.com
TTL: 3600
```

#### 步骤 3：验证 DNS

- DNS 生效后，Vercel 会自动验证
- 通常需要 5-30 分钟
- 检查 Vercel Domains 页面上的状态

#### 步骤 4：HTTPS 证书

- Vercel 自动为你的域名配置 HTTPS
- 通常需要几分钟
- 看到 ✅ "Valid Certificate" 时完成

### 访问你的网站

DNS 生效后，你可以访问：
```
https://你的域名.com
```

---

## 环境变量配置

### 什么是环境变量？

环境变量是应用程序在运行时使用的配置参数。

### 常用变量

#### SECRET_KEY（必需）

用途：Flask 会话加密

生成方式：
```bash
python3 -c "import secrets; print(secrets.token_hex(32))"
```

示例：
```
a1b2c3d4e5f6g7h8i9j0k1l2m3n4o5p6
```

#### GEMINI_API_KEY（可选）

用途：Google Gemini AI 功能

获取方式：
1. 访问 https://ai.google.dev
2. 点击 **"Get API Key"**
3. 选择或创建项目
4. 点击 **"Create API Key"**
5. 复制生成的密钥

示例：
```
AIzaSyD_xxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

#### GEMINI_MODEL（可选）

用途：指定 Gemini 模型版本

示例值：
```
gemini-2.0-flash-exp
gemini-2.5-flash-lite-preview-06-17
gemini-pro
```

#### DATABASE_URL（可选）

用途：PostgreSQL 数据库连接

格式：
```
postgresql://user:password@host:port/database
```

示例：
```
postgresql://postgres:mypassword@db.example.com:5432/matchpredict
```

### 在 Vercel 中设置

1. 进入项目 → **"Settings"** → **"Environment Variables"**
2. 输入变量名
3. 输入变量值
4. 点击 **"Add"**
5. 重新部署（可选）

### 更新环境变量后

- 新变量对新部署立即生效
- 如果需要立即应用，点击 **"Redeploy"**

---

## 性能优化

### 部署后的优化建议

#### 1. 启用缓存

在 `vercel.json` 中配置缓存：

```json
{
  "headers": [
    {
      "source": "/static/:path*",
      "headers": [
        {
          "key": "Cache-Control",
          "value": "public, max-age=31536000, immutable"
        }
      ]
    }
  ]
}
```

#### 2. 启用 Gzip 压缩

Vercel 自动启用，无需配置。

#### 3. 监控性能

在 Vercel 仪表板上：
- 查看函数执行时间
- 查看数据库查询时间
- 查看 API 响应时间

#### 4. 优化数据库查询

- 添加索引到常用字段
- 使用分页获取大数据集
- 缓存频繁查询结果

#### 5. CDN 配置

Vercel 使用全球 CDN，自动为所有用户加速。

---

## 故障排除

### 部署失败

#### 错误：Build failed

**原因：** 代码有错误或依赖不兼容

**解决：**
1. 检查 Vercel 构建日志
2. 查看具体的错误信息
3. 修复代码错误
4. 提交到 GitHub
5. Vercel 会自动重新部署

#### 错误：Function payload too large

**原因：** 部署包太大（超过 50MB）

**解决：**
1. 删除不必要的文件
2. 更新 `.gitignore`
3. 清理缓存文件
4. 重新部署

### 网站访问问题

#### 问题：404 Not Found

**原因：** 路由不存在

**解决：**
1. 检查 URL 是否正确
2. 检查 Flask 路由定义
3. 查看 Vercel 日志

#### 问题：502 Bad Gateway

**原因：** 服务器出错

**解决：**
1. 检查应用日志
2. 重新部署
3. 检查环境变量配置
4. 检查数据库连接

#### 问题：HTTPS 证书错误

**原因：** 域名 DNS 未正确配置

**解决：**
1. 检查 DNS 记录
2. 等待 DNS 生效
3. 清除浏览器缓存
4. 尝试无痕模式

### 功能问题

#### 问题：AI 预测不工作

**原因：** 缺少 GEMINI_API_KEY

**解决：**
1. 获取 Google Gemini API 密钥
2. 在 Vercel 添加 GEMINI_API_KEY
3. 重新部署
4. 测试 AI 功能

#### 问题：数据库连接失败

**原因：** DATABASE_URL 不正确或数据库宕机

**解决：**
1. 检查 DATABASE_URL 格式
2. 检查数据库是否在线
3. 检查网络连接
4. 查看详细错误信息

#### 问题：会话/登录不工作

**原因：** Cookie 配置问题

**解决：**
1. 检查 SESSION_COOKIE_SAMESITE 设置
2. 确保 HTTPS 可用
3. 清除浏览器 Cookie
4. 尝试不同的浏览器

### 性能问题

#### 问题：网站响应慢

**原因：** 请求处理时间过长

**解决：**
1. 检查 Vercel 函数执行时间
2. 优化数据库查询
3. 添加缓存
4. 检查第三方 API 响应时间

#### 问题：数据库查询慢

**原因：** 缺少索引或表太大

**解决：**
1. 分析查询时间
2. 添加适当的索引
3. 使用查询优化
4. 考虑数据库升级

---

## 监控和维护

### 定期检查

- [ ] 每周检查 Vercel 日志
- [ ] 每月检查性能指标
- [ ] 定期更新依赖
- [ ] 备份数据库数据

### 日志查看

在 Vercel 仪表板：
1. 进入项目
2. 点击 **"Deployments"**
3. 选择一个部署
4. 查看 **"Logs"** 标签

### 错误追踪

可以集成 Sentry 或其他服务进行错误追踪。

---

## 常见问题

### Q: Vercel 部署是否免费？

**A:** 是的，免费层包括：
- 每月 100GB 流量
- 无限制函数执行
- 自动扩展
- 足够大多数个人项目使用

### Q: 域名续费时间？

**A:** 通常是每年续费一次，具体取决于你购买的时长。

### Q: 如何备份数据？

**A:**
1. 如果使用 PostgreSQL，定期导出数据库
2. 使用 GitHub 备份代码
3. 记录重要配置

### Q: 能否迁移到其他平台？

**A:** 可以，Vercel 不会锁定你的数据。

---

## 获取帮助

- 📖 [快速开始指南](./QUICK_START.md)
- ✅ [部署检查清单](./DEPLOYMENT_CHECKLIST.md)
- 🔗 [Vercel 文档](https://vercel.com/docs)
- 🐛 [项目 Issues](https://github.com/Scodive/MatchPredict/issues)
- 💬 [GitHub Discussions](https://github.com/Scodive/MatchPredict/discussions)

---

**祝你部署顺利！🚀**
