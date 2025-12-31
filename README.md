# 2026跨年倒计时 - GitHub Pages部署指南

这是一个精美的2026跨年倒计时静态网页，支持自定义昵称、烟花特效、音效、截图分享等功能，可直接部署到GitHub Pages。

## 功能特性

- 🎉 实时倒计时显示（天/时/分/秒）
- 🎨 动态背景和粒子效果
- 🎆 点击屏幕触发烟花特效
- 📸 生成并下载倒计时卡片
- 🔊 倒计时音效和庆祝音效（通过Web Audio API生成）
- 🎤 自动语音播报最后10秒
- 📱 响应式设计，适配移动端
- ✨ 支持自定义昵称参数
- 💌 随机祝福语生成
- 🔧 可配置目标日期

## 快速开始

### 部署到GitHub Pages

#### 方法一：直接Fork部署（推荐）

1. 点击页面右上角的 **Fork** 按钮，将仓库复制到你的GitHub账户
2. 进入你Fork的仓库，点击 **Settings** → **Pages**
3. 在 **Source** 选项中选择 **main** 分支，点击 **Save**
4. 等待几分钟，访问 `https://你的GitHub用户名.github.io/2026-countdown/` 查看效果

#### 方法二：手动创建仓库部署

1. 克隆或下载本仓库到本地
2. 初始化Git仓库：
   ```bash
   git init
   git add .
   git commit -m "Add 2026 countdown page"
   ```
3. 创建GitHub仓库（需要安装GitHub CLI）：
   ```bash
   gh repo create 2026-countdown --public --source=. --remote=origin --push
   ```
4. 开启GitHub Pages：
   - 进入仓库 **Settings** → **Pages**
   - 选择 **main** 分支，点击 **Save**
5. 访问 `https://你的GitHub用户名.github.io/2026-countdown/` 查看效果

### 本地预览

1. 下载或克隆本仓库到本地
2. 在项目根目录启动本地服务器：
   ```bash
   # 使用Python
   python -m http.server 8080
   
   # 使用Node.js
   npx serve .
   
   # 使用PHP
   php -S localhost:8080
   ```
3. 在浏览器中访问 `http://localhost:8080`

## 使用说明

### 基本用法

直接访问部署后的链接即可查看倒计时效果。

### 自定义昵称

通过URL参数 `name` 可以自定义显示的昵称：

| 参数类型 | 示例链接 | 显示效果 |
|---------|---------|---------|
| 无参数 | `https://username.github.io/2026-countdown/` | 显示"亲爱的，距离2026年还有XX天" |
| 中文昵称 | `https://username.github.io/2026-countdown/?name=小明` | 显示"小明，距离2026年还有XX天" |
| 英文昵称 | `https://username.github.io/2026-countdown/?name=Alice` | 显示"Alice，距离2026年还有XX天" |
| 特殊字符 | `https://username.github.io/2026-countdown/?name=张三_2026` | 显示"张三_2026，距离2026年还有XX天" |

### 功能说明

1. **倒计时显示**：实时显示距离2026年元旦的剩余时间
2. **烟花特效**：点击页面任意位置触发烟花效果
3. **截图功能**：点击"生成我的祝福卡片"按钮，可生成并下载倒计时卡片
4. **音效功能**：倒计时最后10秒自动语音播报和提示音效，零点触发铃声和庆祝音效（通过Web Audio API生成）
5. **祝福语**：零点后随机显示不同的元旦祝福语

## 代码结构

```
├── index.html          # 主页面文件
├── README.md          # 项目说明文档
└── .gitignore         # Git忽略文件配置
```

### 核心代码说明

#### 目标日期配置

修改 `index.html` 中的 `TARGET_DATE` 常量可以自定义倒计时目标日期：

```javascript
const TARGET_DATE = new Date('2026-01-01T00:00:00').getTime();
```

#### 主要功能函数

| 函数名 | 功能说明 |
|-------|---------|
| `updateCountdown()` | 更新倒计时显示 |
| `playCountdownVoice()` | 播放倒计时音效 |
| `showNewYear()` | 显示新年祝福 |
| `launchFireworks()` | 发射烟花特效 |
| `createSnowflake()` | 创建雪花粒子 |
| `createConfetti()` | 创建彩带粒子 |
| `getRandomGreeting()` | 获取随机祝福语 |

## 自定义配置

### 修改目标日期

1. 打开 `index.html` 文件
2. 找到第119行的 `TARGET_DATE` 常量
3. 修改为你想要的目标日期，格式为 `YYYY-MM-DDTHH:MM:SS`

### 修改祝福语

1. 打开 `index.html` 文件
2. 找到 `greetings` 数组（大约第126行）
3. 添加或修改祝福语内容

### 修改背景色

1. 打开 `index.html` 文件
2. 找到 `body` 标签的CSS样式（大约第18行）
3. 修改 `background` 属性值

## 浏览器兼容性

| 浏览器 | 兼容性 |
|-------|-------|
| Chrome | ✅ 支持 |
| Firefox | ✅ 支持 |
| Safari | ✅ 支持 |
| Edge | ✅ 支持 |
| 移动端浏览器 | ✅ 支持 |

## 技术栈

- HTML5
- CSS3
- JavaScript (ES6+)
- Canvas API
- Web Speech API
- Web Audio API
- html2canvas（用于截图功能）

## 性能优化

- 使用 `requestAnimationFrame` 优化动画性能
- 粒子系统采用对象池管理
- 图片懒加载
- 响应式设计，适配不同屏幕尺寸
- 代码压缩和优化

## 无障碍支持

- 支持键盘导航
- 支持屏幕阅读器
- 高对比度设计
- 清晰的视觉层次

## 安全说明

- 本项目不收集任何用户数据
- 所有资源均使用HTTPS协议
- 无第三方跟踪代码
- 代码开源，可自行审计

## 许可证

本项目采用MIT许可证，详见 `LICENSE` 文件。

## 贡献指南

欢迎提交Issue和Pull Request来帮助改进这个项目！

1. Fork本仓库
2. 创建特性分支：`git checkout -b feature/AmazingFeature`
3. 提交更改：`git commit -m 'Add some AmazingFeature'`
4. 推送到分支：`git push origin feature/AmazingFeature`
5. 打开Pull Request

## 更新日志

### v1.0.0 (2024-12-31)

- 初始版本发布
- 添加基本倒计时功能
- 支持自定义昵称
- 添加烟花特效
- 添加音效和语音播报
- 支持生成祝福卡片

### v1.1.0 (2024-12-31)

- 优化移动端适配
- 增强烟花特效
- 添加更多祝福语
- 优化性能
- 修复已知问题

### v1.2.0 (2024-12-31)

- 添加雪花粒子效果
- 增强响应式设计
- 优化音频体验
- 添加更多自定义选项

### v2.0.0 (2025-12-31)

- 将目标日期从2025年更新为2026年
- 更新所有相关文本和示例
- 优化代码结构

### v2.0.1 (2025-12-31)

- 优化音效描述，更准确地反映实际实现
- 清理代码中未使用的音频变量
- 更新文档中关于音效功能的说明

## 常见问题

### Q: 如何修改页面标题？
A: 打开 `index.html` 文件，修改第7行的 `<title>` 标签内容。

### Q: 如何修改倒计时的颜色？
A: 打开 `index.html` 文件，修改 `.time-value` 类的CSS样式（大约第69-73行）。

### Q: 如何关闭音效？
A: 目前不支持直接关闭音效，但可以通过浏览器的声音设置关闭标签页声音。

### Q: 为什么截图功能不能使用？
A: 截图功能需要浏览器支持 `html2canvas` 库，请确保你的浏览器是最新版本。

### Q: 如何修改烟花效果？
A: 打开 `index.html` 文件，修改 `Firework` 和 `Particle` 类的代码（大约第616-683行）。

## 相关资源

- [html2canvas文档](https://html2canvas.hertzen.com/)
- [Web Speech API](https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Speech_API)
- [Canvas API](https://developer.mozilla.org/zh-CN/docs/Web/API/Canvas_API)
- [Web Audio API](https://developer.mozilla.org/zh-CN/docs/Web/API/Web_Audio_API)

## 联系方式

如有问题或建议，欢迎通过以下方式联系：

- GitHub Issues: [提交Issue](https://github.com/你的用户名/2025-countdown/issues)
- 邮箱: your-email@example.com

---

**祝您2026元旦快乐！** 🎉🎊