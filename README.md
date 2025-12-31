# 2026跨年倒计时 - GitHub Pages部署指南

## 📋 项目简介

这是一个精美的2026跨年倒计时静态网页，支持自定义昵称、烟花特效、音效、截图分享等功能，可直接部署到GitHub Pages。

## ✨ 核心功能

- ✅ 精准倒计时（天/时/分/秒）
- ✅ URL参数自定义昵称（如 `?name=小明`）
- ✅ 雪花飘落特效
- ✅ 彩带飘落特效（跨年后）
- ✅ 烟花特效（点击触发 + 跨年自动触发）
- ✅ 倒计时数字动效（弹跳/渐变/闪烁）
- ✅ 倒计时音效（倒数10秒语音 + 零点钟声）
- ✅ 零点祝福弹窗（带昵称）
- ✅ 截图生成功能（html2canvas）
- ✅ 响应式布局（完美适配移动端）

## 🚀 GitHub Pages部署步骤

### 方法一：通过GitHub仓库部署

1. **创建GitHub仓库**
   - 登录GitHub，点击右上角 "+" → "New repository"
   - 仓库名称：`2026-countdown`
   - 选择 "Public" 或 "Private"
   - 勾选 "Add a README file"
   - 点击 "Create repository"

2. **上传index.html文件**
   - 进入仓库页面，点击 "Add file" → "Upload files"
   - 将 `index.html` 文件拖拽到上传区域
   - 在 "Commit changes" 中填写提交信息（如 "Add countdown page"）
   - 点击 "Commit changes"

3. **启用GitHub Pages**
   - 进入仓库设置：点击仓库顶部的 "Settings"
   - 左侧菜单找到 "Pages"
   - 在 "Build and deployment" 下的 "Source" 选择 "Deploy from a branch"
   - "Branch" 选择 "main"（或 "master"），文件夹选择 "/ (root)"
   - 点击 "Save"

4. **访问网站**
   - 等待1-2分钟，GitHub会自动部署
   - 在Pages设置页面会显示访问地址，格式为：`https://你的用户名.github.io/仓库名/`
   - 例如：`https://username.github.io/2026-countdown/`

### 方法二：使用GitHub CLI（推荐开发者）

```bash
# 1. 初始化Git仓库
git init

# 2. 添加index.html文件
git add index.html

# 3. 提交更改
git commit -m "Add 2026 countdown page"

# 4. 创建GitHub仓库并推送
gh repo create 2026-countdown --public --source=. --remote=origin --push
```

### 方法三：使用GitHub Desktop（推荐新手）

1. 下载并安装 [GitHub Desktop](https://desktop.github.com/)
2. 登录GitHub账号
3. 点击 "File" → "Add Local Repository" → 选择项目文件夹
4. 点击 "Publish repository"
5. 在仓库设置中启用GitHub Pages（同方法一步骤3）

## 📱 测试用例

### URL传参测试

| 测试场景 | URL示例 | 预期结果 |
|---------|---------|---------|
| 无参数 | `https://username.github.io/2026-countdown/` | 显示"亲爱的，距离2026年还有XX天" |
| 中文昵称 | `https://username.github.io/2026-countdown/?name=小明` | 显示"小明，距离2026年还有XX天" |
| 英文昵称 | `https://username.github.io/2026-countdown/?name=Alice` | 显示"Alice，距离2026年还有XX天" |
| 特殊字符 | `https://username.github.io/2026-countdown/?name=张三_2026` | 显示"张三_2026，距离2026年还有XX天" |

### 跨浏览器测试要点

#### 移动端浏览器
- ✅ 微信内置浏览器（iOS/Android）
- ✅ QQ内置浏览器（iOS/Android）
- ✅ Safari（iOS）
- ✅ Chrome（Android）
- ✅ UC浏览器
- ✅ 百度浏览器

#### 桌面端浏览器
- ✅ Chrome（最新版）
- ✅ Firefox（最新版）
- ✅ Safari（最新版）
- ✅ Edge（最新版）

#### 功能测试清单
- [ ] 倒计时数字正常更新
- [ ] 数字变化时有弹跳动画
- [ ] 最后10秒数字闪烁并播放语音
- [ ] 点击"点击放烟花"按钮触发烟花
- [ ] 雪花持续飘落
- [ ] 跨年后彩带飘落
- [ ] 跨年后自动播放钟声和祝福音乐
- [ ] 跨年后弹出祝福弹窗
- [ ] 点击"生成我的倒计时卡片"生成截图
- [ ] 截图可下载
- [ ] 移动端响应式布局正常
- [ ] 横屏/竖屏切换正常

## 🎨 自定义配置

如需修改倒计时目标日期，编辑 `index.html` 文件第277行：

```javascript
const TARGET_DATE = new Date('2026-01-01T00:00:00').getTime();
```

修改为其他日期，例如：
```javascript
const TARGET_DATE = new Date('2027-01-01T00:00:00').getTime();
```

## 📊 性能优化

- 使用CDN加载html2canvas库（jsdelivr）
- Canvas烟花渲染优化
- 雪花/彩带粒子自动清理
- 音频使用Web Audio API（无需外部音频文件）
- 纯CSS动画，无JavaScript动画库依赖

## 🔧 常见问题

### Q: 部署后页面无法访问？
A: 检查以下几点：
1. 确认GitHub Pages已启用
2. 等待1-2分钟让部署完成
3. 检查仓库是否为Public（Private仓库需升级GitHub Pro）
4. 确认index.html文件在仓库根目录

### Q: 音效无法播放？
A: 浏览器需要用户交互才能播放音频：
1. 先点击页面任意位置
2. 或点击"点击放烟花"按钮
3. 检查浏览器是否禁用了自动播放

### Q: 截图生成失败？
A: 检查以下几点：
1. 确保网络正常（需要加载html2canvas库）
2. 检查浏览器是否支持Canvas API
3. 尝试刷新页面后重试

### Q: 移动端显示异常？
A: 检查以下几点：
1. 确认使用HTTPS访问
2. 清除浏览器缓存
3. 尝试其他浏览器

## 📄 许可证

MIT License - 可自由使用和修改

## 🎯 更新日志

### v1.0.0 (2025-12-31)
- 初始版本发布
- 实现所有核心功能
- 完成移动端适配
- 添加音效和动画

---

**祝您2026新年快乐！** 🎉🎊