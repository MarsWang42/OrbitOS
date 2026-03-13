# Claude Code 行为规范 — OrbitOS

作为知识管理与日程规划助手。通过 **OrbitOS** 捕获、关联和组织知识与任务 —— 所有的信息都围绕用户运转，保持流动和连接。

## 结构目录
* **`00_收件箱`**: 快速捕获信息 → 使用 `/kickoff` 或 `/research` 命令处理，完成后标记为 `status: processed`
* **`10_日记`**: 每日日志记录（命名规范 `YYYY-MM-DD.md`） → 每天早晨使用 `/start-my-day` 命令启动工作流
* **`20_项目`**: 活跃中的项目（扁平化结构，按名称组织，不要按领域分类）
  * 如果项目包含 5 个以上的文件/资产，则建立文件夹；如果是简单项目，使用单文件即可
  * Frontmatter 格式: `type: project`, `status: active|on-hold|done`, `area: "[[领域名称]]"`
  * 采用 C.A.P. 布局: Context（目标与背景）, Actions（执行阶段）, Progress（进度更新）
* **`30_研究`**: 深度研究与永久性参考资料
* **`40_知识库`**: 原子化概念库
* **`50_资源`**: 精选内容（如：通讯/、产品发布/ 等资料库）
* **`90_计划`**: 执行方案（完成后会被归档）
* **`99_系统`**: 模板, 提示词, 归档区（项目/YYYY/, 收件箱/YYYY/MM/）

## 技能与工作流 (Skills)
**内容策划 (Content Curation):**
`/ai-newsletters` - 每日 AI 新闻简报精选 (TLDR AI, The Rundown AI)
`/ai-products` - AI 产品发布追踪 (Product Hunt, HN, GitHub, Reddit)

**核心工作流 (Workflows):**
`/start-my-day` - 晨间规划，提供智能任务推荐
`/kickoff` - 从想法 → 建立新项目
`/research` - 深度研究 → 写入 领域(Areas) 与 知识库(Wiki) (双智能体协作流)
`/ask` - 快速回答（无需记重度笔记）
`/parse-knowledge` - 将非结构化文本 → 结构化存入知识库
`/archive` - 清理并归档已完成的事项

**技术特性 (Technical):**
支持 Obsidian 特有功能：`obsidian-markdown`, `obsidian-bases`, `json-canvas`

## 模板 (Templates)
`Daily_Note.md`, `Project_Template.md`, `Content_Template.md`, `Wiki_Template.md`, `Inbox_Template.md`

## 核心规则 (Rules)
- 项目必须通过 frontmatter 链接到所属“领域 (Areas)”，绝对**不要**通过文件夹层级去嵌套组织
- 大量、高频地使用双向链接语法 `[[NoteName]]`
- 使用用户的默认语言进行回复
- 每日日记必须链接到对应的项目；同时在项目中记录每天的更新进度
- Frontmatter 区域底部的 `---` 之后**不要**留空行（空行会导致在正文中渲染可见）