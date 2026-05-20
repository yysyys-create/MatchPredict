# ✅ MatchPredict 部署检查清单

使用这个清单确保你的部署过程完整无误。

---

## 📋 部署前准备

### GitHub 账号

- [ ] 已有 GitHub 账号
- [ ] 已 Fork MatchPredict 项目
- [ ] 项目地址：https://github.com/yysyys-create/MatchPredict
- [ ] 项目设为 Public（必需）

### 本地环境

- [ ] 已安装 Python 3.8+
- [ ] 已安装 Git
- [ ] 已安装 pip 包管理器

### 生成必需的密钥

- [ ] 运行命令生成 SECRET_KEY：
  ```bash
  python3 -c "import secrets; print(secrets.token_hex(32))"
  ```
- [ ] 保存生成的密钥（记录在下面）：
  ```
  SECRET_KEY: ____________________________________
  ```

---

## 🌐 Vercel 注册和配置

### 账号设置

- [ ] 访问 https://vercel.com
- [ ] 用 GitHub 账号注册
- [ ] 完成邮箱验证
- [ ] 登录 Vercel

### 导入项目

- [ ] 点击 "Add New..." → "Project"
- [ ] 点击 "Import Git Repository"
- [ ] 输入项目 URL：
  ```
  https://github.com/yysyys-create/MatchPredict
  ```
- [ ] 点击 "Import"
- [ ] 项目成功加载（显示项目信息）

### 配置环境变量

#### 必需变量

- [ ] 添加 `SECRET_KEY`
  - 名称：`SECRET_KEY`
  - 值：[粘贴你生成的密钥]
  - 点击 "Add"

#### 可选变量（AI 功能）

- [ ] 添加 `GEMINI_API_KEY`（如需要）
  - 名称：`GEMINI_API_KEY`
  - 值：[你的 Gemini API 密钥]
  - 点击 "Add"

- [ ] 添加 `GEMINI_MODEL`（如需要）
  - 名称：`GEMINI_MODEL`
  - 值：`gemini-2.0-flash-exp`
  - 点击 "Add"

---

## 🚀 部署执行

### 部署前最后检查

- [ ] 确认所有环境变量已添加
- [ ] 确认项目 URL 正确
- [ ] 确认有 GitHub 写入权限

### 开始部署

- [ ] 滚动到页面底部
- [ ] 点击蓝色的 "Deploy" 按钮
- [ ] 部署开始（看到部署日志）
- [ ] 等待 2-3 分钟
- [ ] 看到 ✅ "Successfully deployed to production"

### 获取部署 URL

- [ ] 记录部署成功的 URL：
  ```
  https://matchpredict-_____________.vercel.app
  ```

---

## 🔍 部署验证

### 基本功能测试

- [ ] 访问主页：`https://matchpredict-xxxxx.vercel.app`
  - [ ] 页面加载成功
  - [ ] 看到 MatchPredict 界面
  - [ ] 没有错误信息

- [ ] 健康检查：`https://matchpredict-xxxxx.vercel.app/health`
  - [ ] 显示 "OK"

- [ ] 测试端点：`https://matchpredict-xxxxx.vercel.app/test`
  - [ ] 返回 JSON 格式的状态信息

### 功能测试

#### 经典预测模式

- [ ] 打开网站
- [ ] 选择 "经典模式"
- [ ] 选择联赛
- [ ] 选择两支球队
- [ ] 输入赔率
- [ ] 点击 "预测"
- [ ] 看到预测结果

#### AI 智能模式（如配置）

- [ ] 选择 "AI智能模式"
- [ ] 输入比赛信息
- [ ] 点击 "AI分析"
- [ ] 查看 AI 分析结果

---

## 🌐 自定义域名配置（可选）

### 域名购买

- [ ] 选择域名注册商（Namecheap、GoDaddy 等）
- [ ] 搜索和购买域名
- [ ] 记录域名：
  ```
  域名: _________________________________
  ```
- [ ] 完成支付

### Vercel 配置

- [ ] 进入 Vercel 项目
- [ ] 点击 "Settings" → "Domains"
- [ ] 点击 "Add" 按钮
- [ ] 输入你的域名
- [ ] 点击 "Add"

### DNS 配置

#### 方式 A：Nameservers（推荐）

- [ ] 复制 Vercel 提供的 4 个 Nameservers
- [ ] 登录域名注册商后台
- [ ] 找到 DNS/Nameserver 设置
- [ ] 替换为 Vercel 的 Nameservers：
  ```
  ns1.vercel.com
  ns2.vercel.com
  ns3.vercel.com
  ns4.vercel.com
  ```
- [ ] 保存更改
- [ ] 等待 DNS 生效（1-24 小时）

#### 方式 B：CNAME（如已有其他 DNS 记录）

- [ ] 获取 Vercel 提供的 CNAME 值
- [ ] 登录域名注册商 DNS 管理
- [ ] 添加 CNAME 记录：
  ```
  Type: CNAME
  Name: www
  Value: cname.vercel-dns.com
  ```
- [ ] 保存更改
- [ ] 等待 DNS 生效（1-24 小时）

### DNS 验证

- [ ] 等待 1-24 小时
- [ ] 检查 Vercel 中的域名状态
- [ ] 状态变为 "Valid" ✅
- [ ] HTTPS 证书自动生成
- [ ] 访问 `https://你的域名.com` 测试

---

## 🔧 Gemini AI 配置（可选）

### 获取 API 密钥

- [ ] 访问 https://ai.google.dev
- [ ] 登录 Google 账号
- [ ] 点击 "Get API Key"
- [ ] 创建新项目
- [ ] 复制 API 密钥
- [ ] 记录密钥：
  ```
  GEMINI_API_KEY: _________________________
  ```

### 配置到 Vercel

- [ ] 进入 Vercel 项目 Settings
- [ ] 进入 Environment Variables
- [ ] 添加 `GEMINI_API_KEY`
- [ ] 添加 `GEMINI_MODEL`
- [ ] 点击 "Redeploy"
- [ ] 等待部署完成
- [ ] 测试 AI 功能

---

## 📊 部署后维护

### 日常检查

每周检查一次：

- [ ] 访问网站验证可用性
- [ ] 检查 Vercel 的 Analytics（访问量等）
- [ ] 查看 Deployments 历史
- [ ] 检查是否有错误日志

### 代码更新

有新代码时：

- [ ] 修改本地代码
- [ ] 提交到 GitHub（`git push`）
- [ ] Vercel 自动检测
- [ ] 等待自动部署（1-3 分钟）
- [ ] 验证新版本在线

### 监控和回滚

- [ ] 定期检查部署状态
- [ ] 如有问题，进入 Deployments
- [ ] 选择之前成功的版本
- [ ] 点击 "Redeploy" 回滚

---

## 🐛 常见问题排查

### 部署失败

- [ ] 查看 Vercel 的详细错误日志
- [ ] 检查 Python 代码是否有语法错误
- [ ] 检查环境变量是否正确
- [ ] 检查 requirements.txt 是否完整

### 网站打不开

- [ ] 确认 URL 正确
- [ ] 检查部署状态（✅ 绿色）
- [ ] 硬刷新浏览器：Ctrl+Shift+R
- [ ] 清除浏览器缓存
- [ ] 用隐私模式测试

### 功能不工作

- [ ] 检查浏览器控制台有无错误
- [ ] 查看 Vercel 日志
- [ ] 验证所有环境变量已正确设置
- [ ] 尝试重新部署：Redeploy

### 性能问题

- [ ] 检查 Vercel Analytics
- [ ] 查看响应时间
- [ ] 检查数据库连接
- [ ] 优化代码或升级计划

---

## 📝 记录表

### 部署信息

| 项目 | 值 |
|------|----|
| GitHub URL | https://github.com/yysyys-create/MatchPredict |
| Vercel URL | https://matchpredict-xxxxx.vercel.app |
| 自定义域名 | [可选] |
| 部署日期 | _____________ |
| 部署者 | _____________ |

### 环境变量

| 变量名 | 已配置 | 说明 |
|--------|--------|------|
| SECRET_KEY | [ ] | Flask 会话密钥 |
| GEMINI_API_KEY | [ ] | AI 功能 |
| GEMINI_MODEL | [ ] | AI 模型 |
| DATABASE_URL | [ ] | 数据库 |

### 验证结果

| 测试项 | 结果 | 日期 |
|--------|------|------|
| 主页加载 | [ ] ✅ [ ] ❌ | _____ |
| 健康检查 | [ ] ✅ [ ] ❌ | _____ |
| 经典预测 | [ ] ✅ [ ] ❌ | _____ |
| AI 预测 | [ ] ✅ [ ] ❌ | _____ |
| 自定义域名 | [ ] ✅ [ ] ❌ | _____ |

---

## 🎉 完成！

所有项目都检查完毕后，你可以：

- ✅ 自信地使用你的网站
- ✅ 分享给朋友和家人
- ✅ 监控网站统计数据
- ✅ 不断优化和改进

**恭喜部署成功！🚀**
