# OpenClaw 系统操作手册

> 最后更新：2026-03-20  
> 设备：川的 MacBook Pro

---

## 📋 目录

1. [技能总览](#技能总览)
2. [微信操作](#微信操作)
3. [抖音操作](#抖音操作)
4. [Mac 系统操作](#mac-系统操作)
5. [数据备份](#数据备份)
6. [常用命令](#常用命令)

---

## 技能总览

### 已安装技能（39个）

| 类别 | 技能 | 用途 |
|------|------|------|
| **自学习** | self-improving-agent | 自动记录错误/学习 |
| **电商-国内** | douyin-hot-trend | 抖音热榜 |
| | douyin-downloader | 抖音视频下载 |
| | douyin-publish | 抖音视频发布 |
| | taobao-query | 淘宝商品查询 |
| **电商-国际** | amazon-competitor-analyzer | 亚马逊竞品分析 |
| | clawpify | Shopify 店铺管理 |
| **小红书** | xiaohongshu-mcp | 小红书自动化 |
| | xiaohongshu-cn | 热门笔记/关键词/趋势 |
| | xiaohongshu-deep-research | 小红书深度研究 |
| **快手** | kuaishou | 视频检索/数据分析 |
| **视频号** | weixin-video-publish | 视频号发布 |
| **多平台** | vidu-video-publisher | 一键发4个平台 |
| **微信** | wechat-sender | 微信自动发消息 |
| | wechat-auto-reply | 微信自动回复 |
| **效率** | gog | Google 全家桶 |
| | cron-scheduling | 定时任务 |
| **内容** | best-image | AI 图片生成 |
| | aeo-content-free | SEO 文案优化 |
| **数据** | data-analyst | 数据分析报表 |
| | csv-pipeline | CSV/JSON 处理 |
| **Mac-控制** | airpoint | 自然语言控制Mac |
| | macos-desktop-control | 桌面自动化 |
| | desktop-control | 鼠标键盘控制 |
| **Mac-系统** | mac-system-control | 系统控制 |
| | macos-suite | 系统应用自动化 |
| | macos-audio | 音频蓝牙管理 |
| **Mac-优化** | mac-ai-optimizer | Mac AI 优化 |
| | macbook-optimizer | MacBook 优化 |
| **Mac-快捷指令** | shortcuts-skill | 生成快捷指令 |
| | openclaw-skill-shortcuts-automator | 管理快捷指令 |
| **Mac-其他** | camera | Mac 摄像头拍照 |

---

## 微信操作

### 发送消息（完美流程）

```bash
# 1. 聚焦微信
peekaboo window focus --app "微信"
sleep 0.3

# 2. ESC清空当前状态
peekaboo hotkey --keys "escape" --app "微信"
sleep 0.3

# 3. Cmd+F 打开搜索
peekaboo hotkey --keys "cmd,f" --app "微信"
sleep 0.5

# 4. 清空搜索框
peekaboo hotkey --keys "cmd,a" --app "微信"
sleep 0.1
peekaboo hotkey --keys "delete" --app "微信"
sleep 0.2

# 5. 输入联系人名字（中文用 peekaboo type）
peekaboo type "联系人名字" --app "微信"
sleep 1.5

# 6. 回车选中联系人
peekaboo hotkey --keys "return" --app "微信"
sleep 1

# 7. 输入消息
peekaboo type "消息内容" --app "微信"
sleep 0.5

# 8. 回车发送（微信Mac用回车，不是Cmd+Enter）
peekaboo hotkey --keys "return" --app "微信"
```

### 关键要点
- 中文输入用 `peekaboo type`（AppleScript 中文编码有问题）
- 搜索后等 1.5 秒再回车
- 选中联系人后等 1 秒再输入
- **发送用回车键**，不是 Cmd+Enter

### 自然语言示例
```
给糖糖发消息 在吗
给唐建刚发消息 这个牛逼了
帮我发微信给xxx 内容是xxx
```

---

## 抖音操作

### 查看热榜
```bash
cd ~/.openclaw/workspace/skills/douyin-hot-trend
node scripts/douyin.js hot        # 前50条
node scripts/douyin.js hot 10     # 前10条
```

### 下载视频
```bash
# 需要安装依赖，查看 SKILL.md
cd ~/.openclaw/workspace/skills/douyin-downloader
```

### 发布视频
```bash
# 需要先登录抖音创作者平台
cd ~/.openclaw/workspace/skills/douyin-publish
```

---

## Mac 系统操作

### 打开应用
```bash
open -a "应用名"
# 例：open -a "WeChat"
```

### 自然语言控制（airpoint）
```
帮我打开微信
把音量调到50%
截个图
打开备忘录
```

### 系统信息
```bash
# 音量/亮度/网络等
cd ~/.openclaw/workspace/skills/mac-system-control
```

### 快捷指令
```
帮我创建一个快捷指令xxx
运行xxx快捷指令
```

---

## 数据备份

### GitHub 仓库
- 地址：https://github.com/tanghaichuan0827-bot/openclaw
- 账号：tanghaichuan0827-bot

### 备份操作
```bash
cd ~/.openclaw/workspace
git add -A
git commit -m "提交说明"
git push
```

### 自动提交（我来操作）
```
备份一下
提交到GitHub
```

---

## 常用命令

### 通用
```bash
# 打开应用
open -a "应用名"

# 查看当前时间
date

# 查看系统信息
system_profiler SPHardwareDataType
```

### peekaboo 命令
```bash
# 聚焦窗口
peekaboo window focus --app "应用名"

# 调整窗口大小
peekaboo window set-bounds --app "应用名" --x 0 --y 0 --width 1200 --height 900

# 输入文字
peekaboo type "文字" --app "应用名"

# 快捷键
peekaboo hotkey --keys "cmd,f" --app "应用名"

# 点击坐标
peekaboo click --app "应用名" --coords "x,y"

# 查看UI元素
peekaboo see --app "应用名"
```

---

## 文件结构

```
~/.openclaw/
├── workspace/              # 工作目录
│   ├── AGENTS.md          # 个人信息
│   ├── SOUL.md            # 性格设定
│   ├── USER.md            # 用户信息
│   ├── IDENTITY.md        # 身份信息
│   ├── TOOLS.md           # 工具笔记
│   ├── SYSTEM.md          # ← 本文件
│   ├── .learnings/        # 学习日志
│   │   ├── LEARNINGS.md
│   │   ├── ERRORS.md
│   │   └── FEATURE_REQUESTS.md
│   ├── memory/            # 日常记忆
│   │   └── 2026-03-20.md
│   └── skills/            # 技能目录（39个）
│       ├── douyin-*/
│       ├── xiaohongshu-*/
│       ├── macos-*/
│       ├── wechat-*/
│       └── ...
└── skills/                # 全局技能（self-improving-agent）
```

---

## 注意事项

1. **微信发送**：用回车键，不是 Cmd+Enter
2. **中文输入**：用 `peekaboo type`，避免 AppleScript
3. **搜索后等待**：1.5 秒让结果加载
4. **防录屏**：微信有防录屏，但 peekaboo see 可以绕过
5. **深度休息**：23:00-08:00 非紧急不打扰

---

*此文档由猪儿虫🐛自动维护，如有更新会同步到 GitHub*
