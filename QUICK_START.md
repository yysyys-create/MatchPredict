# 🚀 MatchPredict - 快速开始指南

欢迎使用 MatchPredict 足球比赛预测系统！本指南将帮助你快速部署和使用这个应用。

---

## 📖 目录

- [什么是 MatchPredict?](#什么是-matchpredict)
- [快速部署](#快速部署-5-分钟)
- [部署后如何使用](#部署后如何使用)
- [常见问题](#常见问题)

---

## 什么是 MatchPredict?

MatchPredict 是一个基于深度学习和大模型的足球比赛预测工具，提供：

### 🏆 三种预测模式

1. **经典模式** - 基于五大联赛历史数据的统计分析
2. **彩票模式** - 接入中国体育彩票实时比赛数据
3. **AI智能模式** - 集成大模型进行智能分析预测

### 📊 预测功能

- ✅ 胜平负预测
- ✅ 半全场预测
- ✅ 进球数预测
- ✅ 比分预测
- ✅ 价值投注识别

---

## 快速部署（5 分钟）

### 前置条件

✅ 一个 GitHub 账号（已有）  
✅ 一个浏览器（Chrome、Safari、Firefox 等）

### 部署步骤

#### 步骤 1：打开 Vercel Deploy（30 秒）

访问：**https://vercel.com/new**

#### 步骤 2：导入 GitHub 项目（1 分钟）

1. 点击 **"Import Git Repository"**
2. 输入：`https://github.com/yysyys-create/MatchPredict`
3. 点击 **"Import"**

#### 步骤 3：配置环境变量（2 分钟）

在 "Environment Variables" 部分，添加：

```
SECRET_KEY = [运行下面的命令生成]
```

**生成 SECRET_KEY：**

打开终端，运行：
```bash
python3 -c "import secrets; print(secrets.token_hex(32))"
```

复制输出的值到 Vercel。

#### 步骤 4：部署（1 分钟）

1. 点击 **"Deploy"** 按钮
2. 等待 2-3 分钟
3. 看到 ✅ 绿色对勾

#### 步骤 5：获取 URL（30 秒）

部署完成后，你会看到：
```
Your app is live at: https://matchpredict-xxxxx.vercel.app
```

**保存这个 URL，你可以：**
- 分享给朋友
- 添加到浏览器书签
- 配置自定义域名

---

## 部署后如何使用

### 🌐 访问网站

打开你的 Vercel URL：
```
https://matchpredict-xxxxx.vercel.app
```

### 📝 基本功能

#### 1. 经典模式（无需登录）

1. 选择 **"经典模式"**
2. 选择联赛（英超、西甲、意甲、德甲、法甲）
3. 选择主队和客队
4. 输入赔率
5. 点击 **"预测"**

#### 2. AI 智能模式（需要 Gemini API）

1. 选择 **"AI智能模式"**
2. 输入比赛信息
3. 点击 **"AI分析"**
4. 查看 AI 提供的详细分析

#### 3. 彩票模式（如果配置了数据库）

1. 选择 **"彩票模式"**
2. 点击 **"刷新比赛"**
3. 选择要分析的比赛
4. 查看预测结果

### 💾 保存和分享

- 预测结果会自动保存
- 点击 **"分享"** 按钮分享给朋友
- 查看历史预测记录

---

## 添加 AI 功能（可选）

如果你想使用 AI 智能预测功能：

### 获取 Gemini API 密钥

1. 访问：https://ai.google.dev
2. 点击 **"Get API Key"**
3. 点击 **"Create API Key"**
4. 复制生成的密钥

### 配置到 Vercel

1. 进入 Vercel 项目 → **"Settings"** → **"Environment Variables"**
2. 添加新变量：
   - 名称：`GEMINI_API_KEY`
   - 值：[你的 API 密钥]
3. 添加另一个变量：
   - 名称：`GEMINI_MODEL`
   - 值：`gemini-2.0-flash-exp`
4. 点击 **"Save"** 和 **"Redeploy"**

### 验证 AI 功能

1. 在网站上选择 **"AI智能模式"**
2. 输入比赛信息
3. 点击 **"AI分析"**
4. 应该看到 AI 生成的分析

---

## 配置自定义域名（可选）

### 购买域名

选择一个域名注册商购买你的域名：

- **Namecheap**: https://www.namecheap.com
- **GoDaddy**: https://www.godaddy.com
- **阿里云**: https://wanwang.aliyun.com

### 添加到 Vercel

1. 进入 Vercel 项目 → **"Settings"** → **"Domains"**
2. 输入你的域名
3. 点击 **"Add"**
4. 按照指示配置 DNS

### 完成后

访问你的自定义域名：
```
https://你的域名.com
```

---

## 常见问题

### Q: 部署后网站打不开？

**A:** 
1. 检查 URL 是否正确（https:// 开头）
2. 等待 5 分钟，可能还在部署中
3. 刷新浏览器（Ctrl+F5 或 Cmd+Shift+R）
4. 检查 Vercel 的部署状态

### Q: 如何更新网站代码？

**A:**
1. 修改 GitHub 上的代码
2. 提交到你的 fork
3. Vercel 会自动检测并重新部署
4. 部署完成后刷新网站即可看到更新

### Q: 预测不准确怎么办？

**A:**
1. 这是正常现象，足球是圆的！
2. 预测仅基于历史数据，无法预测所有变量
3. 多尝试不同的联赛和比赛
4. 使用 AI 模式获得更准确的分析

### Q: 能否自定义域名？

**A:** 可以！但需要购买域名。按照 "[配置自定义域名](#配置自定义域名可选)" 部分的步骤操作。

### Q: 费用是多少？

**A:**
- **Vercel 部署**：免费（免费层足够使用）
- **自定义域名**：取决于域名注册商，通常 $10-50/年
- **Gemini API**：免费额度 + 付费（可选）

### Q: 如何重新部署？

**A:**
1. 进入 Vercel 项目
2. 点击 **"Deployments"**
3. 找到要重新部署的版本
4. 点击 **"Redeploy"**

### Q: 如何查看日志？

**A:**
1. 进入 Vercel 项目
2. 点击 **"Deployments"**
3. 点击最新的部署
4. 查看 **"Logs"** 标签

---

## 下一步

- [ ] 部署到 Vercel
- [ ] 测试各个预测模式
- [ ] 配置自定义域名（可选）
- [ ] 邀请朋友使用
- [ ] 反馈意见和建议

---

## 获取帮助

- 📖 [完整部署指南](./DEPLOYMENT_GUIDE.md)
- ✅ [部署检查清单](./DEPLOYMENT_CHECKLIST.md)
- 🌐 [Vercel 文档](https://vercel.com/docs)
- 🐍 [Flask 文档](https://flask.palletsprojects.com)
- 🐛 [项目 Issues](https://github.com/Scodive/MatchPredict/issues)

---

**祝你使用愉快！🎉**

如有任何问题，欢迎提交 Issue 或 Pull Request。
