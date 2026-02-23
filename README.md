# 🦞 OpenClaw 多 Agent 实战配置模板

**免费送你一份跑通了的 OpenClaw 配置，三个 AI 助理同时在线，Telegram + Discord 双平台。**

> 这是我花了数周打磨的生产环境配置，脱敏后开源分享。你不需要从零摸索，直接在这个基础上改就行。

---

## ⬇️ 下载方式（选一种就行）

### 方式一：一键下载 ZIP（推荐小白用）

👉 **点击这个绿色按钮下载：**

[![Download ZIP](https://img.shields.io/badge/⬇️_点击下载_ZIP-238636?style=for-the-badge&logo=github&logoColor=white)](https://github.com/chancheuklap/openclaw-starter-kit/archive/refs/heads/main.zip)

下载后解压，你会得到这些文件：

```
openclaw-starter-kit/
├── openclaw.json       ← 配置文件，复制到 ~/.openclaw/ 目录
├── 配置详解.md          ← 每个参数的中文解释
└── 参考链接.md          ← 精选学习资源
```

### 方式二：用命令下载（适合有终端经验的同学）

```bash
git clone https://github.com/chancheuklap/openclaw-starter-kit.git
```

---

## 🚀 三步用起来

### 第一步：确保你已经安装了 OpenClaw

如果还没装，先跑这行命令：

```bash
npx openclaw@latest
```

跟着引导走完就行。详细教程看 👉 [OpenClaw 101 中文指南](https://openclaw101.dev/zh)

### 第二步：备份你的旧配置（重要！）

```bash
cp ~/.openclaw/openclaw.json ~/.openclaw/openclaw.json.backup
```

### 第三步：复制新配置 + 替换占位符

```bash
cp openclaw.json ~/.openclaw/openclaw.json
```

然后用任意文本编辑器打开 `~/.openclaw/openclaw.json`，搜索 `YOUR_` ，把所有占位符替换成你自己的：

| 要替换的内容 | 是什么 | 去哪里拿 |
|---|---|---|
| `YOUR_GOOGLE_API_KEY` | Google AI 密钥 | [点这里申请（免费）](https://aistudio.google.com/apikey) |
| `YOUR_BRAVE_SEARCH_API_KEY` | 网页搜索密钥 | [点这里申请（免费）](https://brave.com/search/api/) |
| `YOUR_TELEGRAM_BOT_TOKEN_*` | Telegram 机器人令牌 | Telegram 搜 @BotFather，按提示创建 |
| `YOUR_DISCORD_BOT_TOKEN_*` | Discord 机器人令牌 | [Discord 开发者后台](https://discord.com/developers/applications) |
| `YOUR_GATEWAY_TOKEN` | 网关令牌 | 运行 `openclaw onboard` 时自动生成 |
| `YOUR_TELEGRAM_USER_ID` | 你的 Telegram 数字 ID | Telegram 搜 @userinfobot，它会告诉你 |
| `YOUR_DISCORD_USER_ID` | 你的 Discord 用户 ID | Discord 设置 → 高级 → 开启开发者模式 → 右键自己头像 → 复制用户 ID |
| `YOUR_GUILD_ID_*` | Discord 服务器 ID | 右键服务器图标 → 复制服务器 ID |
| `YOUR_CHANNEL_ID_*` | Discord 频道 ID | 右键频道名 → 复制频道 ID |

替换完保存，然后重启：

```bash
openclaw gateway restart
```

搞定！🎉

---

## 🏗️ 这个配置有什么

```
┌─────────────────────────────────────────────┐
│              OpenClaw Gateway                │
├────────────┬──────────────┬─────────────────┤
│  main 🦞   │  coach 👨‍🏫   │  info 🔍        │
│  日常助理   │  专项顾问     │  信息采集        │
├────────────┴──────────────┴─────────────────┤
│       Telegram  ←  路由  →  Discord          │
└─────────────────────────────────────────────┘
```

**三个 AI Agent，各有分工：**
- 🦞 **main** — 你的日常万能助理
- 👨🏻‍🏫 **coach** — 某个领域的专项顾问
- 🔍 **info** — 信息采集和内容处理

**每个 Agent 独立运行：**
- 各自有专属的 Telegram Bot 和 Discord Bot
- 各自有独立的记忆和工作空间
- 各自有心跳巡检（每小时自动 check-in）

**五个 AI 模型混合使用：**
- Claude Opus — 主力推理（最聪明）
- Claude Sonnet — 心跳巡检（性价比高）
- Gemini Flash — 定时脚本（最便宜）
- Gemini Pro — 复杂分析备选
- GPT Codex — 写代码专用

**还有这些已调好的功能：**
- ✅ 消息分块输出（像人一样一段一段打字）
- ✅ 本地语音转写（零 API 费用，用 Whisper）
- ✅ 命令执行安全审批（危险操作需要你点批准）
- ✅ 长对话自动压缩（不会 token 爆炸）
- ✅ Brave 网页搜索集成

---

## 📖 想了解每个参数的含义？

👉 看 [**配置详解.md**](配置详解.md) — 每一块都有中文注释，解释「是什么」和「为什么这么设」。

## 📚 从零开始学 OpenClaw？

👉 看 [**参考链接.md**](参考链接.md) — 精选的中英文教程，从安装到进阶。

👉 特别推荐 [**OpenClaw 101**](https://openclaw101.dev/zh) — 7 天系统学习路径，293+ 篇教程聚合。

---

## ❓ 常见问题

**Q：我只用 Telegram / 只用 Discord，不需要双平台怎么办？**
> 删掉你不用的 channel 配置就行。比如只用 Discord，就把 `channels.telegram` 整块删掉，对应的 bindings 里 telegram 的条目也删掉。

**Q：我不需要三个 Agent，一个就够了怎么办？**
> `agents.list` 里只保留 `main` 那一个，删掉 coach 和 info。bindings 里也只保留 main 的。

**Q：我没有 Mac，Whisper 语音转写能用吗？**
> 配置里的 `afconvert` 是 macOS 专属命令。Linux 用户需要把它换成 `ffmpeg`，或者直接关掉 `media.audio`（设 `enabled: false`）。

**Q：这些 API Key 要花钱吗？**
> Google API Key 和 Brave Search API Key 都有免费额度，个人使用基本够。AI 模型（Claude / Gemini）的费用取决于你的使用量和订阅方式。

**Q：替换占位符的时候引号要不要删？**
> 不要删！只替换引号里面的内容。比如 `"YOUR_GOOGLE_API_KEY"` 改成 `"AIzaSy..."` 。

---

## ⭐ 觉得有用？

给个 Star ⭐ 就是最好的支持！有问题欢迎开 Issue。

---

## 💬 最后说一句

如果你已经知道龙虾，那么你并没有被时代抛弃；如果最后我行了，你也一定行。

关于我漏掉的细节，可以直接粘贴该网页网址，问问你手上任何的 AI 助手——我们一起主动起来，学习起来，干起来。

Peace ✌️

---

> 📌 基于 OpenClaw `2026.2.21-2` 版本 | [官方文档](https://docs.openclaw.ai/) | [OpenClaw 101](https://openclaw101.dev/zh) | [GitHub 源码](https://github.com/openclaw/openclaw)
