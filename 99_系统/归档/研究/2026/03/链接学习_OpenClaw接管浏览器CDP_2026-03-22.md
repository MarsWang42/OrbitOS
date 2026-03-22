---
type: research
created: 2026-03-22
status: archived
source: feishu
source_role: moushi
applicable_roles: [diaoyan, moushi]
learning_depth: 摘要级（标题+官方主来源补锚）
confidence: B
platform: bilibili
thinking_mode: 深度学习
claim_type: 教程
evidence_level: A
validation_status: 已归档（项目判断已吸收）
tags: [research, link-learning, bilibili, openclaw, browser, CDP, chrome]
---

# 链接学习：让 OpenClaw 接管浏览器 — Chrome DevTools Protocol 实战

## 清理结论

- 当前状态：已归档，当前只保留来源索引与主来源补锚记录
- 归档理由：这条研究最关键的边界判断已经收成项目结论：当前先继续 `Web Clipper + 浏览器采样`，不急着扩浏览器接管
- 后续如要重启：等真的要做浏览器自动化时，再从这页和官方浏览器文档继续

## 基本信息

- 主题：OpenClaw 通过 Chrome DevTools Protocol (CDP) 接管浏览器
- 平台：B站
- 时长：37:29
- 原始链接：https://b23.tv/Iw5yvih
- 采集日期：2026-03-22

## 学习深度

- 当前学习深度：**摘要级**（标题 + 官方主来源补锚）
- 当前判断依据：
  - 只获取了标题和频道相关推荐，未观看视频正文
  - 已补到 OpenClaw 官方浏览器文档、Chrome Extension 文档、沙箱文档和远程 CDP 故障排查文档
- 当前能确认什么：
  - OpenClaw 的“接管浏览器”并不是单一模式，而至少有 4 条通道：
    - `openclaw` 专用隔离浏览器
    - `user` / `existing-session` 已登录本机浏览器会话
    - Chrome extension relay 显式附着当前标签页
    - raw remote CDP 远程浏览器
  - 当前最安全的默认路径仍是专用隔离浏览器，不该默认理解成“直接接管你正在用的个人 Chrome”
  - 如果要控制当前 Chrome 标签页，必须显式点扩展附着，而且只控制被附着的 tab
  - 沙箱浏览器默认带 `--disable-extensions`，扩展依赖型流程默认并不会自动工作
- 当前还不能确认什么：
  - 这条视频里实际演示的是哪条浏览器控制通道
  - 视频中是否用了扩展接管、existing-session，还是 raw remote CDP

## 分析判断

- 这条内容主要在讲什么：
  - 用 Chrome DevTools Protocol 让 OpenClaw 接管浏览器
  - 实现 7x24 AI 浏览器助手
- 为什么值得学：
  - 它能纠正一个很常见的误解：`Web Clipper`、浏览器采样、OpenClaw `browser` 工具并不是一回事
  - 可以帮你把“浏览器能力”拆成隔离态、已登录态、显式接管态、远程态 4 类边界
- 当前更像：主来源补锚后的结构判断
- 建议下一步：
  - 当前主线先把“哪种模式对应哪种风险”记清楚，不急着再扩浏览器自动化
  - 如果后续真要让 OpenClaw 操作当前 Chrome，就优先考虑 extension relay，并明确只附着特定 tab

## 主来源补锚

- OpenClaw 官方浏览器文档确认：
  - 默认 `openclaw` profile 是专用隔离浏览器
  - `user` profile 是通过 Chrome DevTools MCP 附着本机已登录浏览器会话
  - remote CDP 适合显式接远端 Chromium，不是同一回事
- OpenClaw 官方 Chrome Extension 文档确认：
  - 扩展接管是单独一条通道，不是自动“接管你当前浏览器”
  - 只有你手动点击扩展附着的 tab 才会被控制
  - 扩展接管会访问该 tab 当前登录态，风险高于隔离浏览器
- OpenClaw 官方沙箱文档确认：
  - 沙箱浏览器默认 `--disable-extensions`
  - 需要扩展的流程不能默认假设沙箱浏览器会直接支持
- OpenClaw 远程 CDP 排障文档确认：
  - 跨主机 / 跨命名空间时，更适合 raw remote CDP
  - `existing-session` / `user` 更适合同机、用户在场批准附着的场景

## 同频道发现的相关推荐

| 标题 | 时长 |
|------|------|
| 从零搭一个 Clawdbot：7x24 AI 助手 | 01:04:38 |
| Clawdbot 在智星云 GPU 的独立旅行记 | 23:19 |
| 用 OpenClaw 喂猫：扩展 Agent 能力边界 | 41:26 |
| OpenClaw 养猫 | 03:01 |
| 7分钟做一个新闻订阅 | 07:16 |
| 让 Clawdbot 赚钱，Token 耗光 | 03:27 |
| OpenClaw 写安卓应用 | 04:34 |
| VisionClaw：OpenClaw 视觉 | 10:12 |
| OpenClaw 的"我"的意识 | 07:28 |

> 这批视频是同一个创作者，内容覆盖 OpenClaw 的浏览器自动化、AI Agent 能力扩展、实际应用场景。是高质量的 OpenClaw 学习来源池。

## 最终结论

- 当前处理结果：已归档，保留为来源索引
- 主来源保留：[[20_项目/OpenClaw与Obsidian自动化/OpenClaw与Obsidian自动化]]
- 当前更像：已被项目判断吸收的边界研究

## 参考来源

- [Browser - OpenClaw](https://docs.openclaw.ai/tools/browser)
- [Chrome Extension - OpenClaw](https://docs.openclaw.ai/tools/chrome-extension)
- [Sandboxing - OpenClaw](https://docs.openclaw.ai/gateway/sandboxing)
- [WSL2 + Windows + remote Chrome CDP troubleshooting - OpenClaw](https://docs.openclaw.ai/tools/browser-wsl2-windows-remote-cdp-troubleshooting)
