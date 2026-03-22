---
type: knowledge
created: 2026-03-22
status: stable
source: feishu
source_role: moushi
applicable_roles: [moushi, diaoyan, jishu, sheji, yinxiao, yewen, shuju, shenhe]
confidence: A
platform: system
tags: [knowledge, openclaw, obsidian, system-design]
topic: OpenClaw与Obsidian分工原则
---

# OpenClaw与Obsidian分工原则

## 核心原则

| 工具 | 职责 | 特点 |
|------|------|------|
| OpenClaw | **执行与推进** | 动态、实时、对话式 |
| Obsidian | **沉淀与组织** | 静态、结构化、可视化 |

## 具体分工

### OpenClaw 负责
- **执行**：运行命令、操作文件、调用API
- **推进**：跟踪进度、生成下一步行动、提醒待办
- **对话**：理解意图、分发任务、汇总结果
- **自动化**：定时任务、事件触发、子Agent调用
- **验证与复盘组织**：推动自审、他审、项目验证与闭环优化

### Obsidian 负责
- **沉淀**：捕获信息、整理知识、归档成果
- **组织**：分类存储、关联链接、结构化呈现
- **呈现**：可视化、搜索、阅读
- **持久化**：长期存储、版本管理
- **留痕**：保存自审细节、复盘结论与验证记录

## 工作流

```
用户输入
    ↓
OpenClaw（理解意图）
    ↓
┌─────────────────────────────────────┐
│  OpenClaw 执行层                     │
│  ├── 收件箱捕获                      │
│  ├── 任务分析与分发                   │
│  └── 结果汇总                        │
└─────────────────────────────────────┘
    ↓
Obsidian 沉淀层
    ├── 分类存储（项目/研究/知识库）
    ├── 关联链接
    └── 知识网络构建
```

## 设计理由

1. **能力互补**：OpenClaw 擅长动态处理，Obsidian 擅长静态组织
2. **职责清晰**：避免Agent记忆膨胀，减少上下文污染
3. **可追溯**：所有成果都沉淀到Obsidian，可随时查阅
4. **可持续**：Obsidian作为长期知识库，OpenClaw作为短期执行层

## 关联

- [[99_系统/归档/研究/2026/03/02_OpenClaw多Agent协作流程设计]]
- [[20_项目/OpenClaw与Obsidian自动化/13_生产级部署计划]]
- [[40_知识库/01_系统设计/知识沉淀要经过验证复盘闭环]]
- [[AGENTS]]
- [[TOOLS]]
