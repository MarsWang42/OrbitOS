---
type: research
created: 2026-03-22
status: archived
source: feishu
source_role: moushi
applicable_roles: [diaoyan, moushi]
learning_depth: 摘要级
confidence: A
platform: bilibili+official-docs+local-vault
thinking_mode: 主来源补锚
claim_type: 综合研究
evidence_level: A
validation_status: 已归档（判断已提炼为知识卡）
archive_mode: evidence
tags: [research, obsidian, bases, dataview, plugins, 知识管理, 合集]
---

# Obsidian 生态研究合集：Bases 与插件

> 合并自 5 条 B站 视频，并已补 Obsidian 官方帮助文档与本机 Vault 状态，2026-03-22

## 视频清单

| # | 标题 | 链接 | 核心内容 |
|---|------|------|---------|
| 1 | Obsidian+OpenClaw重构知识管理 | https://b23.tv/V6hjyCU | OpenClaw 联动、AI 自动整理、生成知识图谱 |
| 2 | Obsidian必备5个插件 | https://b23.tv/XDfLNOL | Calendar/QuickAdd/Dataview/Templater/Minimal+StyleSettings |
| 3 | Obsidian Bases数据库功能 | https://b23.tv/pRI18A8 | Bases 可替代 Dataview |
| 4 | Bases打造个人图书馆 | https://b23.tv/60P19tU | 用 Bases 管理读书笔记 |
| 5 | Bases组织项目和任务 | https://b23.tv/hrgXNAq | 用 Bases 管理项目和任务 |
| 6 | NotebookLM+Obsidian结合 | https://b23.tv/bqq72xo | NotebookLM AI笔记工具与Obsidian联动 |

## 当前最关键的纠偏

- 这批内容最容易把人带到“先装一堆插件”
- 但你当前 Vault 的真实情况不是“缺 Bases”，而是“Bases 已启用，但还没有把它稳稳用进当前主线”
- 所以当前不是 `Dataview vs Bases` 的抽象站队问题，而是：
  - 本机已启用的原生 `Bases` 是否足以承接你现在的项目 / 研究视图
  - 什么时候才值得引入额外社区插件复杂度

## 官方主来源补锚

- [Introduction to Bases - Obsidian Help](https://obsidian.md/help/bases)
  - `Bases` 是官方核心能力，用于按属性创建可编辑、可排序、可筛选的自定义视图
- [Core plugins - Obsidian Help](https://obsidian.md/help/plugins)
  - `Bases` 被列在官方核心插件列表里，不是第三方附加能力
- [Community plugins - Obsidian Help](https://obsidian.md/help/community-plugins)
  - 社区插件会运行第三方代码
  - 社区插件默认不会自动更新，需要手动检查与更新
- [Plugin security - Obsidian Help](https://obsidian.md/help/plugin-security)
  - 官方把插件权限、受限模式和安装边界当作明确安全问题来处理

## 本机状态核对

- `.obsidian/core-plugins.json` 中已确认 `bases: true`
- `.obsidian/community-plugins.json` 当前只有 `claudian`
- `99_系统/数据库` 下至少已存在 3 个 `.base` 文件：
  - `Projects.base`
  - `Knowledge.base`
  - `Projects_Archive.base`

## 插件推荐清单

来自视频 2（附 GitHub 链接）：

| 插件 | 链接 | 用途 |
|------|------|------|
| Calendar | https://github.com/liamcain/obsidian-calendar-plugin | 每日日记日历视图 |
| QuickAdd | https://github.com/chhoumann/quickadd | 快速添加内容 |
| Dataview | https://github.com/blacksmithgu/obsidian-dataview | 数据库查询（代码） |
| Templater | https://github.com/SilentVoid13/Templater | 模板系统 |
| Minimal 主题 | https://github.com/kepano/minimal | 极简主题 |
| Style Settings | https://github.com/mgmeyers/obsidian-style-settings | 主题自定义 |

## Bases 应用场景

来自视频 3、4、5：

- **个人图书馆**：管理读书笔记（视频 4）
- **项目管理**：组织项目和任务（视频 5）
- **通用数据库**：结构化数据管理（视频 3）

## 同频道发现的相关推荐

摘要页发现该作者（频道）还有大量 Obsidian 教程，包括：
- Obsidian 新手系列教程（6集）
- Markdown 关键技巧
- 快捷键配置
- 自定义主题
- 卡片盒笔记法
- Copilot Plus 插件
- 本地 AI（LM Studio）
- Web Clipper + AI
- 每日笔记习惯系统
- 智能收件箱和索引
- 数字花园

> 这些推荐可作为后续深度学习的候选来源池。

## 对视频观点的更准确判断

### Bases vs Dataview

- 视频里“Bases 可替代 Dataview”更像方向性判断，不应直接当成全量替代结论
- 但对你当前 Vault 来说，这个争论现在没有那么紧迫，因为：
  - `Bases` 已经可用
  - 你当前主线更需要低摩擦的项目 / 研究视图，而不是更强代码查询
  - `Dataview` 目前没有被真实痛点倒逼进场

### 插件推荐清单

- `Calendar / QuickAdd / Dataview / Templater / Minimal / Style Settings` 这些推荐可以留作候选池
- 但当前不适合因为视频标题就一起装上
- 更稳的顺序是：
  - 先用官方核心能力解决当前问题
  - 真出现明确阻力，再为单一问题引入单一插件

## 与你的 Vault 的对照

- 你的 Vault 当前使用：OpenClaw 联动 + Obsidian 本地管理
- 当前真实状态不是“缺 Bases”，而是“Bases 已启用，但尚未在当前主线里补 1 条明确样本”
- 当前更缺的不是插件数量，而是：
  - 用现有 `Bases` 把项目 / 研究视图真正跑到顺手
  - 按真实痛点决定社区插件是否值得进入
- Bases 的任务管理和图书馆案例与你的项目结构高度相关，但当前先不急着扩插件栈

## AI 工具 + Obsidian 生态

来自视频 6：
- **NotebookLM + Obsidian**：Google AI 笔记工具与 Obsidian 联动
- 与第一条 OpenClaw + Obsidian 同类型，AI 工具如何与本地笔记库结合是共同主题

## 与当前主线的关系

- 和 [[20_项目/OpenClaw与Obsidian自动化/OpenClaw与Obsidian自动化]] 的关系：
  - 这批研究补的是“Obsidian 的结构化层该怎么落”
  - 当前最稳的答案不是扩插件栈，而是优先用 `Bases + properties + 现有项目/研究文件`
- 和当前主线的直接结论：
  - `Obsidian Web Clipper` 继续负责网页采集
  - `Obsidian CLI` 继续负责低风险追加写回
  - `Bases` 适合作为本地视图层候选，但先小范围试点
  - 社区插件暂不扩容

## 已吸收并降级的子条目

- 以下单条 `链接学习` 已不再保留为主线活跃研究，而是降级为来源索引：
  - [[99_系统/归档/研究/2026/03/链接学习_Obsidian+OpenClaw重构知识管理体系_2026-03-22]]
  - [[99_系统/归档/研究/2026/03/链接学习_Obsidian必备5个插件_2026-03-22]]
  - [[99_系统/归档/研究/2026/03/链接学习_Obsidian_Bases数据库功能_2026-03-22]]
  - [[99_系统/归档/研究/2026/03/链接学习_Obsidian_Bases个人图书馆_2026-03-22]]
  - [[99_系统/归档/研究/2026/03/链接学习_Obsidian_Bases组织项目和任务_2026-03-22]]
  - [[99_系统/归档/研究/2026/03/链接学习_NotebookLM与Obsidian结合_2026-03-22]]
- 当前保留这页作为它们的主来源汇总判断，避免主线里同时挂一串重复 `active` 条目

## 下一步建议

1. 不因为这批视频立即安装 `Dataview / QuickAdd / Calendar / Templater`
2. 先把现有 `Bases` 当成原生视图层，继续观察 `Projects.base / Knowledge.base` 是否已够用
3. 如果要做下一条最小动作，就补 1 个与你当前主线直接相关的 `Bases` 真实视图样本，再决定是否扩大
4. `NotebookLM + Obsidian` 保留在第二批生态扩展里，先不挤进当前主线
5. 该频道其他 Obsidian 教程仍可作为候选来源池，但后续继续按“官方文档 + 本机状态”来筛

## 最终结论

- 是否进入正式研究：进入
- 是否值得后续提炼知识卡：已提炼为 [[40_知识库/01_系统设计/Obsidian应先用Bases承接真实视图，再按痛点引入社区插件]]
- 最推荐的下一步动作：不是“先装 Bases”，而是“承认 Bases 已启用，再补 1 个真实主线视图样本”
- 当前更像：已补官方来源与本机状态的生态判断
