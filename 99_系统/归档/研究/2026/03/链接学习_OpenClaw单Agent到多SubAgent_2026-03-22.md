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
tags: [research, link-learning, bilibili, openclaw, sub-agent, 多Agent]
---

# 链接学习：告别上下文丢失，从单 Agent 到多 Sub Agent

## 清理结论

- 当前状态：已归档，当前只保留来源索引与主来源补锚记录
- 归档理由：这条研究已经把“命名 Agent vs Sub-Agent” 的结构判断回写到项目主线，不再需要继续占活跃研究位
- 后续如要重启：等未来真的做 `1` 条慢任务 `Sub-Agent` 样本时，再从项目判断继续

## 基本信息

- 主题：OpenClaw 多 Sub Agent 配置，解决上下文丢失问题
- 平台：B站
- 原始链接：https://b23.tv/2rA2g8S
- 采集日期：2026-03-22

## 学习深度

- 当前学习深度：摘要级（标题 + 官方主来源补锚）
- 当前判断依据：
  - 只获取了标题，未获取视频正文
  - 已补到 OpenClaw 官方 `Sub-Agents`、`Channel Routing`、`Onboarding` 文档

## 主来源补锚

- OpenClaw 官方 `openclaw agents add <name>` 文档确认：
  - 命名 Agent 会创建独立的 `workspace`
  - 有独立的 `agentDir`
  - 有独立的 `sessions`
  - 有独立的 auth profiles
- OpenClaw 官方 `Channel Routing` 文档确认：
  - `bindings` 会把入站消息路由到某个命名 Agent
  - 不同频道 / 群 / 线程天然会形成不同 session key
  - 这类路由是“固定多 Agent / Persistent Agent”层，不是 Sub-Agent
- OpenClaw 官方 `Sub-Agents` 文档确认：
  - Sub-Agent 是从当前运行里临时派生的后台 run
  - 它有自己的 session：`agent:<agentId>:subagent:<uuid>`
  - 完成后会把结果回报给请求者
  - 默认拿不到 session/system 级工具
  - 每个 Sub-Agent 都有独立 token 与成本，不是零成本优化

## 核心内容

- 单 Agent 的上下文丢失问题
- 从单 Agent 扩展到多 Sub Agent 的配置方法
- OpenClaw 教程

## 分析判断

- 这条内容主要在讲什么：
  - 当主 Agent 一路承接所有任务时，容易把“长期角色分工”和“临时并行执行”混在一起
  - 视频标题里的“从单 Agent 到多 Sub Agent”，更适合被理解成：从单线程执行升级到“命名 Agent + 临时 Sub-Agent”的组合
- 当前最重要的结构判断：
  - **命名 Agent / Persistent Agent**：解决长期身份、工作区、凭据、渠道路由和上下文隔离
  - **Sub-Agent**：解决长任务、慢工具、并行子任务，不负责长期人格或渠道驻留
- 所以“上下文丢失”的第一层解法不是一上来狂加 Sub-Agent，而是：
  - 先把固定角色和渠道路由拆清楚
  - 再把需要并行的任务交给 Sub-Agent
- 当前更像：主来源补锚后的结构判断，而不是单纯教程收藏

## 与当前项目的关系

- **高度相关**：你的 [[20_项目/OpenClaw与Obsidian自动化/OpenClaw与Obsidian自动化]] 项目正在做多 Agent 路由和协作用
- 这条视频真正对你有价值的不是“再加更多 Agent”，而是帮你区分：
  - 现在这套 `moushi / diaoyan / jishu / shenhe...` 已经属于命名多 Agent 层
  - 后续要不要加 Sub-Agent，是执行层优化问题，不是主架构重做问题
- 与今日已学的 [[99_系统/归档/研究/2026/03/OpenClaw三大Agent深度解析_2026-03-22]] 可对照
- 和当前项目的最稳连接方式：
  - 继续保持 `谋士 -> 专家角色 -> 审核` 的固定路由
  - 只在“研究型 / 慢工具 / 长任务”里，择机补 1 条真实 Sub-Agent 样本

## 当前结论

- 这条研究不应该把你带回“要不要推倒重做多 Agent 架构”
- 更准确的结论是：
  - 当前主线已经完成命名多 Agent 的第一层
  - 下一步不是继续解释角色分工，而是未来找 1 条真实慢任务验证 Sub-Agent 是否真能减少主线程阻塞
- 对你当前项目最值的动作：
  - 先不新增角色
  - 先不把所有任务都拆成 Sub-Agent
  - 只在明确会卡住主线程的任务上，补 1 条真实 Sub-Agent 验证样本

## 最终结论

- 当前处理结果：已归档，保留为来源索引
- 主来源保留：[[20_项目/OpenClaw与Obsidian自动化/OpenClaw与Obsidian自动化]]
- 当前更像：已被项目判断吸收的结构分层研究

## 参考来源

- [Sub-Agents - OpenClaw](https://docs.openclaw.ai/tools/subagents)
- [Onboarding (CLI) - OpenClaw](https://docs.openclaw.ai/start/wizard)
- [Channel Routing - OpenClaw](https://docs.openclaw.ai/channels/channel-routing)
