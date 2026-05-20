# 📖 MatchPredict 完整部署指南

本指南提供 Vercel 部署、自定义域名配置和故障排除的完整步骤。

---

## 📚 目录

1. [前置要求](#前置要求)
2. [Vercel 部署](#vercel-部署)
3. [自定义域名配置](#自定义域名配置)
4. [环境变量详解](#环境变量详解)
5. [部署后配置](#部署后配置)
6. [监控和维护](#监控和维护)
7. [故障排除](#故障排除)

---

## 前置要求

### 必需

- ✅ GitHub 账号（已有）
- ✅ Vercel 账号（免费注册）
- ✅ 浏览器（Chrome、Safari、Firefox）
- ✅ 终端/命令行工具

### 可选

- Google 账号（用于 Gemini API）
- 自定义域名（用于自定义网址）
- PostgreSQL 数据库（用于数据存储）

---

## Vercel 部署

### 步骤 1：注册 Vercel

1. 访问 https://vercel.com
2. 点击 "Sign Up"
3. 选择 "Continue with GitHub"
4. 授权访问你的 GitHub 账户
5. 完成注册

### 步骤 2：导入项目

1. 进入 Vercel 仪表板
2. 点击 "Add New..." → "Project"
3. 选择 "Import Git Repository"
4. 输入：`https://github.com/yysyys-create/MatchPredict`
5. 点击 "Import"

### 步骤 3：配置项目

Vercel 会自动检测项目配置，你会看到：

```
Framework Preset: Other
Root Directory: ./
Build Command: [自动检测]
Output Directory: [自动检测]
```

**保持默认设置即可。**

### 步骤 4：设置环境变量

在 "Environment Variables" 部分添加：

#### 必需变量

| 变量名 | 值 | 说明 |
|--------|----|---------|
| `SECRET_KEY` | [生成的密钥] | Flask 会话密钥 |

#### 可选变量

| 变量名 | 值 | 说明 |
|--------|----|---------|
| `GEMINI_API_KEY` | [你的 API 密钥] | Google Gemini AI |
| `GEMINI_MODEL` | `gemini-2.0-flash-exp` | 使用的模型 |
| `DATABASE_URL` | [PostgreSQL 连接] | 数据库连接 |
| `SESSION_COOKIE_SAMESITE` | `None` | Cookie 配置 |

### 步骤 5：部署

1. 点击 "Deploy" 按钮
2. 等待 2-3 分钟
3. 看到 ✅ 绿色对勾
4. 获得你的 URL：`https://matchpredict-xxxxx.vercel.app`

---

## 自定义域名配置

### 步骤 1：购买域名

选择一个域名注册商：

| 服务商 | 网址 | 特点 |
|--------|------|------|
| **Namecheap** | https://www.namecheap.com | 便宜、可靠 |
| **GoDaddy** | https://www.godaddy.com | 功能全面 |
| **阿里云** | https://wanwang.aliyun.com | 国内服务 |
| **Cloudflare** | https://www.cloudflare.com | 免费域名注册 |

### 步骤 2：在 Vercel 添加域名

1. 进入 Vercel 项目
2. 点击 "Settings" → "Domains"
3. 点击 "Add" 按钮
4. 输入你的域名（例如：matchpredict.com）
5. 点击 "Add"

Vercel 会提示两种配置方式。

### 步骤 3：配置 DNS（选择一种方式）

#### 方式 A：使用 Vercel Nameservers（推荐）

1. Vercel 会提供 4 个 Nameservers
2. 复制这些 Nameservers
3. 登录你的域名注册商后台
4. 找到 "Nameservers" 或 "DNS" 设置
5. 将你的域名的 DNS 指向这 4 个 Nameservers
6. 等待 DNS 生效（通常 1-24 小时）

**示例：**
```
Nameserver 1: ns1.vercel.com
Nameserver 2: ns2.vercel.com
Nameserver 3: ns3.vercel.com
Nameserver 4: ns4.vercel.com
```

#### 方式 B：手动 CNAME 配置

如果你的域名已有其他 DNS 记录：

1. Vercel 会提示 CNAME 记录
2. 登录你的域名注册商后台
3. 进入 DNS/CNAME 设置
4. 添加 CNAME 记录：
   ```
   主机: www
   值: cname.vercel-dns.com
   ```
5. 等待 DNS 生效

### 步骤 4：验证域名

1. DNS 生效后（通常 1-24 小时），Vercel 会自动验证
2. 状态从 "Pending" 变为 "Valid"
3. HTTPS 证书会自动生成

### 步骤 5：访问你的域名

现在你可以通过自定义域名访问你的网站：

```
https://你的域名.com
```

---

## 环境变量详解

### SECRET_KEY

**用途：** Flask 会话加密密钥

**生成方法：**
```bash
# 方法 1：Python
python3 -c "import secrets; print(secrets.token_hex(32))"

# 方法 2：OpenSSL
openssl rand -hex 32

# 方法 3：Online 生成器
# https://randomkeygen.com/
```

**示例：**
```
abc123def456ghi789jkl012mno345pqr678stu901vwx234yz
```

### GEMINI_API_KEY

**用途：** Google Gemini AI 预测功能

**获取方法：**
1. 访问 https://ai.google.dev
2. 点击 "Get API Key"
3. 创建新项目
4. 复制 API 密钥
5. 在 Vercel 中配置

**格式：**
```
sk-proj-xxxxxxxxxxxxxxxxxxxxxxxxxxxxx
```

### DATABASE_URL

**用途：** PostgreSQL 数据库连接（可选）

**格式：**
```
postgresql://username:password@hostname:5432/database_name
```

**示例：**
```
postgresql://user:mypassword@db.example.com:5432/matchpredict
```

---

## 部署后配置

### 配置 AI 功能

1. 在 Vercel 项目 Settings → Environment Variables
2. 添加 `GEMINI_API_KEY`
3. 添加 `GEMINI_MODEL`（值为 `gemini-2.0-flash-exp`）
4. 点击 "Redeploy"

### 配置数据库

1. 创建或获得 PostgreSQL 数据库
2. 在 Vercel 中添加 `DATABASE_URL`
3. 运行初始化脚本
4. 点击 "Redeploy"

### 配置自动部署

Vercel 默认会自动检测 GitHub 更新：

1. 在 GitHub 修改代码
2. 提交到 main 分支
3. Vercel 自动检测并部署（1-3 分钟）
4. 部署完成后刷新网站

---

## 监控和维护

### 查看部署历史

1. 进入 Vercel 项目
2. 点击 "Deployments" 标签
3. 查看所有部署记录
4. 可以回滚到之前的版本

### 查看日志

1. 进入 "Deployments"
2. 点击一个部署
3. 查看 "Logs" 标签

### 性能监控

1. 进入 "Analytics" 标签
2. 查看访问量、响应时间等

### 自动回滚

如果部署失败：

1. 进入 "Deployments"
2. 点击之前成功的版本
3. 点击 "Redeploy"

---

## 故障排除

### 部署失败

**症状：** 看到红色的 ❌ 标记

**解决方案：**

1. 点击部署查看详细错误
2. 常见原因：
   - 环境变量配置错误
   - requirements.txt 有问题
   - Python 版本不兼容

3. 修复问题后提交到 GitHub
4. Vercel 会自动重新部署

### 网站打不开

**症状：** 访问 URL 显示 404 或 502 错误

**解决方案：**

1. 检查部署状态（绿色对勾 = 成功）
2. 等待 5 分钟（可能仍在部署）
3. 硬刷新浏览器：
   - Windows: Ctrl+Shift+R
   - Mac: Cmd+Shift+R
4. 清空浏览器缓存
5. 在隐私浏览模式测试

### 环境变量未生效

**症状：** 设置了环境变量但不工作

**解决方案：**

1. 确保正确添加了环境变量
2. 点击 "Redeploy" 重新部署
3. 等待部署完成
4. 刷新网站

### 数据库连接失败

**症状：** 看到数据库错误信息

**解决方案：**

1. 检查 `DATABASE_URL` 是否正确
2. 确保数据库服务运行
3. 检查防火墙/网络设置
4. 确认数据库凭证正确

### AI 功能不工作

**症状：** AI 预测返回错误

**解决方案：**

1. 检查 `GEMINI_API_KEY` 是否设置
2. 验证 API 密钥是否有效
3. 检查 API 配额是否用尽
4. 确保 `GEMINI_MODEL` 设置正确

### 域名无法访问

**症状：** 自定义域名无法连接

**解决方案：**

1. 检查 DNS 配置是否正确
2. 等待 DNS 生效（通常 1-24 小时）
3. 使用 DNS 检查工具验证：https://mxtoolbox.com/
4. 确保 Vercel 中的域名状态为 "Valid"
5. 检查 HTTPS 证书是否生成

---

## 📞 获取帮助

- 📖 官方文档：https://vercel.com/docs
- 🐛 GitHub Issues：https://github.com/Scodive/MatchPredict/issues
- 💬 Vercel 支持：https://vercel.com/support
- 🌐 社区论坛：https://github.com/Scodive/MatchPredict/discussions

---

**祝你部署顺利！🚀**
