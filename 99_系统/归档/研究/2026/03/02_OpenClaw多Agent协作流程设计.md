---
type: research
created: 2026-03-22
status: archived
source_role: moushi
applicable_roles: [moushi, diaoyan, sheji, yinxiao, yewen, jishu, shuju, shenhe]
confidence: A
platform: system
tags: [research, openclaw, multi-agent]
topic: OpenClaw多Agent协作流程设计
validation_status: 已归档（角色分工与协作判断已被知识层和项目主线吸收）
archive_mode: evidence
---

# OpenClaw多Agent协作流程设计

## 清理结论

- 当前状态：已归档，当前只保留为多 Agent 协作结构的证据页
- 归档理由：`谋士` 入口定位、角色思维模式、OpenClaw 与 Obsidian 分工、标准协作链都已经收成知识卡与项目判断
- 后续如要重启：等真的要补 `Sub-Agent` 真实样本或重做协作链时，再从这页继续

## 研究背景

目标：设计一套适合当前Obsidian体系的多Agent协作流程，实现「谋士」作为前台总控、专家Agent分工执行的架构。

## 当前Obsidian体系结构

```
├── 00_收件箱      # 临时输入
├── 10_日记        # 每日记录
├── 20_项目        # 项目管理
├── 30_研究        # 研究内容
├── 40_知识库      # 知识沉淀
├── 50_资源        # 资源整理
├── 90_计划        # 计划
└── 99_系统        # 系统配置
```

## 多Agent角色定义

| Agent | 角色 | 工作区 | 职责 |
|-------|------|--------|------|
| moushi | 谋士/主控 | Vault根目录 | 总控入口，理解、分发、汇总、交付 |
| diaoyan | 调研 | 02_调研 | 信息搜集、市场调研、竞品分析 |
| sheji | 设计 | 03_设计 | 产品设计、方案规划 |
| yinxiao | 营销 | 04_营销 | 营销策略、内容推广 |
| yewen | 文案 | 05_文案 | 文案撰写、内容创作 |
| jishu | 技术 | 06_技术 | 技术实现、代码开发 |
| shuju | 数据 | 07_数据 | 数据分析、报告生成 |
| shenhe | 审核 | 08_审核 | 质量审核、内容把关 |

## 角色思维模式

为了避免“角色有分工，但判断方式混乱”，每个角色都应有相对稳定的思维模式：

- `moushi`：路由思维、闭环思维、第二序思维
- `diaoyan`：来源比较、假设驱动、样本边界意识
- `sheji`：用户场景、约束转译、表达一致性
- `yinxiao`：漏斗思维、测试思维、反馈回路
- `yewen`：受众感知、利益点表达、版本对照
- `jishu`：系统拆解、最小闭环、验证优先
- `shuju`：指标定义、概率思维、因果谨慎、可重复性
- `shenhe`：逆向审查、风险控制、反例检查

这样可以保证：

- 过程分工清楚
- 同类问题有统一判断框架
- 最终沉淀的知识不会因为角色不同而彼此冲突

## 协作流程设计

### 流程一：标准任务流（用户 → 谋士 → 专家 → 审核 → 用户）

```
用户消息
    ↓
moushi（谋士/主控）
    ├── 理解意图
    ├── 判断类型（项目/研究/知识/日常）
    └── 分发到对应Agent
    ↓
专家Agent（diaoyan/sheji/yinxiao/yewen/jishu/shuju）
    ├── 执行任务
    └── 产出结果
    ↓
shenhe（审核）
    ├── 质量审核
    └── 给出建议
    ↓
moushi（汇总）
    └── 返回用户
```

补一句更清晰的角色定位：

- `moushi` 更像前台秘书与路由器，负责接收、判断、分配、汇总
- 真正的深处理、学习、转化应优先交给对应专家角色完成
- 正式知识不按 agent 分裂存放，而是在统一知识层通过 `source_role / applicable_roles` 保留来源与适用范围

### 流程二：简单任务流（直接执行）

适用于简单查询、闲聊、快速记录：
```
用户消息 → moushi → 直接响应
```

### 流程三：复杂项目流（多Agent协作）

适用于复杂项目，需要多个Agent协作：
```
moushi（规划）
    ↓
diaoyan（调研）→ sheji（设计）→ jishu（实现）→ shuju（分析）
    ↓
shenhe（审核）
    ↓
yewen（文案）→ yinxiao（营销）
    ↓
moushi（汇总交付）
```

## 触发机制设计

### 飞书意图触发词
| 前缀 | 触发Agent | 目标目录 |
|------|-----------|----------|
| 收件箱： | moushi | 00_收件箱 |
| 项目： | moushi + sheji | 20_项目 |
| 研究： | moushi + diaoyan | 30_研究 |
| 知识： | moushi | 40_知识库 |
| 文案： | moushi + yewen | 按主题 |
| 技术： | moushi + jishu | 按主题 |
| 数据： | moushi + shuju | 按主题 |
| 审核： | moushi + shenhe | 按主题 |

### 指令型触发词
| 前缀 | 动作 |
|------|------|
| 整理收件箱： | moushi批量整理00_收件箱 |
| 推进项目： | moushi生成下一步行动 |
| 审核： | shenhe执行质量审核 |

## 会话路由设计

### 当前配置（已有bindings）
```json
{
  "type": "route",
  "agentId": "moushi",
  "match": { "channel": "feishu", "accountId": "bot-moushi" }
},
{
  "type": "route",
  "agentId": "diaoyan",
  "match": { "channel": "feishu", "accountId": "bot-diaoyan" }
},
// ... 其他Agent
```

### 路由策略
1. **主控路由**：bot-moushi 作为统一入口，所有消息先到moushi
2. **专家路由**：用户可直接@特定专家Agent获取服务
3. **子Agent调用**：moushi通过subagents功能调用其他Agent

## 记忆隔离策略

### 当前问题
- 所有Agent共享memory-lancedb
- 可能造成记忆污染

### 解决方案
1. **Agent专属记忆**：每个Agent的记忆文件独立存储
2. **记忆蒸馏规则**：
   - moushi：蒸馏用户偏好、系统配置
   - 专家Agent：蒸馏各自领域的知识
3. **跨Agent知识共享**：通过Obsidian笔记而非memory共享

## 知识流转链条

推荐把多 Agent 协作理解成下面这条链：

`用户输入 -> moushi 判断与分配 -> 对应专家角色学习/转化 -> 落到 项目/研究/知识 -> 今日日记记录 -> 用户可追溯`

这样做的目的不是把知识库拆散，而是把“过程责任”交给角色，把“正式沉淀”收回统一知识体系。

## 验证与优化闭环

如果希望系统真正“学有所用”，还要补上这一段：

`对应专家执行 -> 自审 -> 他审 / 审核 -> 项目验证 -> 复盘 -> 再沉淀为稳定知识`

其中：

- 专家角色先做自审，说明边界、风险和未验证部分
- `shenhe` 或其他角色做他审，防止单角色过拟合
- 最后通过项目结果来判断这条经验是否真的提高成功率
- 成功与否不只看单次结果，还要看质量、效率、稳定性和可复用性
- 自审细节与复盘结论应保留，作为后续优化材料

## 待验证问题

- [ ] 多Agent路由是否正常工作？
- [ ] moushi调用子Agent是否正常？
- [ ] 记忆隔离是否有效？
- [ ] Agent间协作流程是否顺畅？

## 参考资料

- [[20_项目/OpenClaw与Obsidian自动化/13_生产级部署计划]]
- [[99_系统/归档/研究/2026/03/对标样本_OpenClaw三大Agent深度解析_2026-03-22]]
- [[99_系统/归档/研究/2026/03/对标样本_飞书前台正式落位链路统一验收_2026-03-22]]
- B站视频：https://b23.tv/LXakkcv
