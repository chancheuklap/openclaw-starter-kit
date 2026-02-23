# 🦞 OpenClaw 多 Agent 实战配置模板

> 如果你已经知道龙虾，那么你并没有被时代抛弃；如果最后我行了，你也一定行。
>
> 关于我漏掉的细节，可以直接粘贴该网页网址，问问你手上任何的 AI 助手——我们一起主动起来，学习起来，干起来。Peace ✌️

---

**这是什么？** 一份已经调好的 OpenClaw 配置文件，拿回去改几个地方就能用。

**能干嘛？** 让你同时拥有三个 AI 助理，分别负责日常杂事、专业咨询和信息收集，在 Telegram 和 Discord 上随时找它们聊天、下指令。

**要花钱吗？** OpenClaw 本身免费开源。AI 模型需要付费（按量计费或订阅制），但配置里也包含了免费模型的方案。

---

## ⬇️ 第一步：下载

**什么都不用装，点一下就行：**

[![点击下载](https://img.shields.io/badge/⬇️_点击这里下载-238636?style=for-the-badge&logo=github&logoColor=white)](https://github.com/chancheuklap/openclaw-starter-kit/archive/refs/heads/main.zip)

下载后**解压**，你会看到这些文件：

| 文件 | 干嘛用的 |
|------|----------|
| `openclaw.json` | **配置文件**（最重要的，就是它） |
| `配置详解.md` | 每个参数是什么意思（当字典查） |
| `参考链接.md` | 学习资源合集 |

---

## 🔧 第二步：安装 OpenClaw

如果你还没装过 OpenClaw，打开电脑的**终端**（Terminal），粘贴这行命令：

```bash
npx openclaw@latest
```

它会问你几个问题，跟着选就行。

> 💡 **不知道"终端"在哪？** 
> - Mac：按 `Cmd + 空格`，输入"终端"，回车
> - Windows：按 `Win + R`，输入 `cmd`，回车
>
> **装不上？报错了？** 别慌——把报错信息截图，发给你的任意 AI 助手（ChatGPT、Kimi、豆包都行），问它怎么解决。或者来小红书直播间问我，我帮你看。

---

## 📝 第三步：填你自己的信息

用记事本（或任何文本编辑器）打开下载的 `openclaw.json`，你会看到很多 `YOUR_` 开头的内容——这些是占位符，需要换成你自己的。

**别被数量吓到！** 下面一个一个教你拿：

### 🤖 创建你的 Telegram 机器人

1. 打开 Telegram，搜索 **@BotFather**
2. 发送 `/newbot`
3. 它会问你机器人叫什么名字，随便起
4. 创建成功后它会给你一串 **token**（长这样：`123456789:ABCdefGHI...`）
5. 复制这个 token，替换配置文件里的 `YOUR_TELEGRAM_BOT_TOKEN_1`

> 这个配置用了三个机器人（三个 AI 助理各一个），所以你要重复三次，分别替换 `_1`、`_2`、`_3`。
>
> **只想先用一个？** 没问题。怎么简化配置，来小红书问我，或者直接把这个页面网址丢给 AI 助手，让它帮你改。

### 🎮 创建你的 Discord 机器人

1. 打开 [Discord 开发者后台](https://discord.com/developers/applications)
2. 点 **New Application** → 起个名字 → 左边点 **Bot** → 点 **Reset Token** → 复制 token
3. 替换配置里的 `YOUR_DISCORD_BOT_TOKEN_1`

> 同样需要三个。流程一样，重复三次。
>
> ⚠️ **Bot 需要邀请到你的服务器才能用。** 这一步有点绕——建议直接把这个页面网址粘贴给你的 AI 助手，让它手把手教你生成邀请链接。

### 🔑 申请免费的 API 密钥

| 替换内容 | 去哪里拿 | 要钱吗 |
|----------|----------|--------|
| `YOUR_GOOGLE_API_KEY` | [Google AI Studio](https://aistudio.google.com/apikey) → 创建 API 密钥 | 免费 |
| `YOUR_BRAVE_SEARCH_API_KEY` | [Brave Search API](https://brave.com/search/api/) → 注册 → Free 计划 | 免费 |

### 🆔 找到你自己的 ID

| 替换内容 | 怎么拿 |
|----------|--------|
| `YOUR_TELEGRAM_USER_ID` | Telegram 搜索 **@userinfobot**，它会自动告诉你 |
| `YOUR_DISCORD_USER_ID` | Discord 设置 → 高级 → 打开**开发者模式** → 回到聊天界面，右键点自己头像 → **复制用户 ID** |
| `YOUR_GUILD_ID_*` | 右键点 Discord **服务器图标** → 复制服务器 ID |
| `YOUR_CHANNEL_ID_*` | 右键点 Discord **频道名** → 复制频道 ID |

> 💡 Discord 的"开发者模式"打开后，右键菜单才会出现"复制 ID"选项。找不到的话问 AI 助手。

### 剩下两个不用自己填

| 替换内容 | 说明 |
|----------|------|
| `YOUR_GATEWAY_TOKEN` | 安装 OpenClaw 时**自动生成**的，去 `~/.openclaw/openclaw.json` 里找现有的值，复制过来 |
| `your_email@gmail.com` | 你的 Google 邮箱，用于 Gemini 模型登录 |

---

## 🚀 第四步：放进去，启动

```bash
# 先备份你现在的配置（万一要改回来）
cp ~/.openclaw/openclaw.json ~/.openclaw/openclaw.json.backup

# 把你改好的新配置放进去
cp openclaw.json ~/.openclaw/openclaw.json

# 重启
openclaw gateway restart
```

> ⚠️ **这一步操作的是系统文件。** 如果你不确定自己改得对不对，**强烈建议把你改好的 `openclaw.json` 发给 AI 助手**，让它帮你检查一遍再放进去。稳一点不丢人。

搞定！🎉 现在去 Telegram 或 Discord 找你的机器人说句话试试。

---

## 🏗️ 你会得到什么

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

**三个 AI 助理，各管一摊：**
- 🦞 **main** — 万能助手，啥都能聊、啥都能干
- 👨🏻‍🏫 **coach** — 某个领域的专属顾问（你自己定它懂什么）
- 🔍 **info** — 帮你收集和整理信息

**已经调好的能力：**
- ✅ 像真人一样一段一段打字（不是一坨丢过来）
- ✅ 语音消息自动转文字（本地处理，不花钱）
- ✅ 危险操作需要你手动批准（不会乱删东西）
- ✅ 每小时自动巡查一次（帮你看邮件、看日历）
- ✅ 聊太久也不会崩（自动压缩历史对话）
- ✅ 能上网搜索

---

## ❓ 可能遇到的问题

**"我只想用一个助理，不需要三个"**
> 可以。把多余的删掉就行。不确定删哪些——把这个页面发给 AI 助手，告诉它"我只要保留一个 agent，帮我精简配置"。

**"我只用 Telegram / 只用 Discord"**
> 同上。让 AI 助手帮你删掉不需要的平台配置。

**"我没有 Mac"**
> 配置里有一项语音转写功能是 macOS 专属的。Linux/Windows 用户让 AI 助手帮你改成 ffmpeg 方案，或者直接关掉它。

**"报错了 / 机器人没反应"**
> 截图报错信息 → 发给 AI 助手。如果 AI 也搞不定，来小红书找我，直播间里帮你看。

**"想了解每个参数具体是什么意思"**
> 打开 [**配置详解.md**](配置详解.md)，里面有逐行中文注释。

---

## 📚 学习资源

刚接触 OpenClaw？推荐按顺序看：

1. 👉 [**OpenClaw 101 — 7 天入门**](https://openclaw101.dev/zh)（中文，从零开始，最适合新手）
2. 👉 [**官方文档**](https://docs.openclaw.ai/)（查具体参数用）
3. 👉 [**更多资源**](参考链接.md)（视频教程、部署指南、深度文章）

---

## 🦞 关于我

我是一个正在用 AI 搭建自己工作系统的人。这个配置是我实际在用的，不是教程里抄的。

如果你也在摸索 OpenClaw，欢迎来**小红书**找我——我会不定期直播搭建过程，踩过的坑、调过的参数、犯过的错，全都现场聊。

> **小红书搜索：** `（你的小红书名字）`

---

## ⭐ 觉得有用？

点个 Star ⭐ 让更多人看到。有问题欢迎开 Issue。

---

> 📌 基于 OpenClaw `2026.2.21-2` 版本 | [官方文档](https://docs.openclaw.ai/) | [OpenClaw 101](https://openclaw101.dev/zh)
