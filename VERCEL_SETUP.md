# ⚡ Vercel 快速部署指南（5 分钟）

只需 5 分钟，将 MatchPredict 部署到全球！

---

## 🚀 5 步快速部署

### 步骤 1: 生成安全密钥（1 分钟）

打开终端，运行以下命令生成 SECRET_KEY：

```bash
python3 -c "import secrets; print(secrets.token_hex(32))"
```

**复制输出的值**（看起来像这样）：
```
abc123def456ghi789jkl012mno345pqr678stu901vwx234yz
```

---

### 步骤 2: 打开 Vercel Deploy（30 秒）

访问这个链接：

👉 **https://vercel.com/new**

---

### 步骤 3: 导入 GitHub 项目（1 分钟）

1. 在 Vercel 页面上，点击 **"Import Git Repository"**
2. 在输入框中粘贴：
   ```
   https://github.com/yysyys-create/MatchPredict
   ```
3. 点击 **"Import"** 按钮

**你会看到项目信息自动加载。**

---

### 步骤 4: 配置环境变量（1 分钟）

向下滚动到 **"Environment Variables"** 部分。

添加一个新变量：

| 名称 | 值 |
|------|----|
| `SECRET_KEY` | 粘贴你在步骤 1 生成的密钥 |

**示例：**
```
NAME: SECRET_KEY
VALUE: abc123def456ghi789jkl012mno345pqr678stu901vwx234yz
```

✅ 点击 **"Add"** 按钮确认添加。

---

### 步骤 5: 部署（1 分钟）

1. 滚动到页面底部
2. 点击蓝色的 **"Deploy"** 按钮
3. **等待 2-3 分钟** - 你会看到部署进度条
4. 看到 ✅ **绿色对勾** = 部署成功！

---

## 🎉 部署完成！

部署完成后，你会看到这样的页面：

```
✅ Successfully deployed to production

Your app is live at:
https://matchpredict-xxxxx.vercel.app
```

### 保存你的 URL！

```
https://matchpredict-xxxxx.vercel.app
```

**你现在可以：**
- 📱 在浏览器中打开这个链接
- 🔗 分享给朋友
- 💾 添加到浏览器书签

---

## ✅ 验证部署成功

### 方法 1: 访问网站

打开你的 Vercel URL，应该看到 MatchPredict 的主页。

### 方法 2: 检查健康状态

访问：`https://matchpredict-xxxxx.vercel.app/health`

应该显示：
```
OK
```

### 方法 3: 查看测试端点

访问：`https://matchpredict-xxxxx.vercel.app/test`

应该返回 JSON：
```json
{
  "status": "ok",
  "message": "服务正常运行",
  "timestamp": "2026-05-20T08:33:52Z"
}
```

---

## 🎯 就这样！你已经完成了！

| 项目 | 状态 |
|------|------|
| ✅ 部署 | 完成 |
| ✅ 获得 URL | 完成 |
| ✅ 可以使用 | 完成 |

---

## 🚀 下一步（可选）

### 添加 AI 功能（10 分钟）

想让预测更准确？添加 Gemini AI：

1. 访问 https://ai.google.dev
2. 点击 "Get API Key"
3. 复制你的 API 密钥
4. 在 Vercel 项目中添加：
   - `GEMINI_API_KEY` = 你的 API 密钥
   - `GEMINI_MODEL` = `gemini-2.0-flash-exp`
5. 点击 "Redeploy"

### 配置自定义域名（15 分钟）

想用 `你的网站.com` 代替 `vercel.app`？

1. 购买域名（Namecheap、GoDaddy 等）
2. 在 Vercel 项目中进入 Settings → Domains
3. 添加你的域名
4. 配置 DNS 记录
5. 完成！

---

## ⚠️ 故障排除

### 问题：部署失败

**解决方案：**
1. 检查 SECRET_KEY 是否正确粘贴
2. 确保项目 URL 正确：`https://github.com/yysyys-create/MatchPredict`
3. 在 Vercel 的 "Deployments" 标签查看详细错误

### 问题：网站打不开

**解决方案：**
1. 检查 URL 是否正确
2. 等待 5 分钟，可能仍在部署
3. 刷新浏览器（Ctrl+F5）
4. 在 Vercel 项目中点击 "Redeploy"

### 问题：看不到我的更改

**解决方案：**
1. 更改代码后提交到 GitHub
2. Vercel 会自动检测并重新部署
3. 等待部署完成（通常 1-3 分钟）
4. 硬刷新浏览器：Ctrl+Shift+R（或 Cmd+Shift+R）

---

## 📞 需要帮助？

- 📖 完整指南：查看 DEPLOYMENT_GUIDE.md
- ✅ 检查清单：查看 DEPLOYMENT_CHECKLIST.md  
- 🐛 Vercel 文档：https://vercel.com/docs
- 💬 项目问题：https://github.com/yysyys-create/MatchPredict/issues

---

**恭喜！🎉 你现在拥有一个在线的足球预测网站！**
