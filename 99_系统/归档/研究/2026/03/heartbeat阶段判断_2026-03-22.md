---
type: research
created: 2026-03-22
status: complete
source_role: moushi
applicable_roles: [moushi, jishu, diaoyan, shenhe]
confidence: A
platform: openclaw
thinking_mode: 闭环思维, 运行态排查
claim_type: 规律
evidence_level: A
validation_status: 已验证
tags: [research, heartbeat, openclaw, operations]
topic: heartbeat阶段判断
---
# heartbeat阶段判断

## 一句话结论

`heartbeat` 现在不是“没开”，而是“调度已经开着，但有效任务几乎为空”，所以当前还不能说它带来了真实收益。

## 这轮要回答什么

- `heartbeat` 现在到底有没有启用
- 它有没有真的减少手动触发、漏触发或整理负担

## 已确认事实

### 1. 调度层已经启用

- 运行态配置里已经存在：
  - `agents.defaults.heartbeat.every = 30m`
- 说明默认心跳调度不是空白状态

### 2. Gateway 历史日志里确实有心跳启动记录

- `gateway.log` 中多次出现：
  - `[heartbeat] started`
- 说明系统层面的心跳轮询确实跑起来过

### 3. 当前 HEARTBEAT 任务内容几乎为空

- Vault 根目录：
  - [[HEARTBEAT]]
  - 当前内容是“保持空文件可跳过 heartbeat API calls”
- 各角色工作区：
  - `调研 / 设计 / 营销 / 文案 / 技术 / 数据 / 审核`
  - 当前 `HEARTBEAT.md` 都几乎只有一句：
    - `无待办时回复 HEARTBEAT_OK`

### 4. 历史会话证明它大多在“检查后无事可做”

- 旧会话里可以看到：
  - 定时触发会读取 `HEARTBEAT.md`
  - 然后常见结果是 `HEARTBEAT_OK`
- 这说明它更像“定时 ping”，还不是“定时产生有效推进”

## 最终判断

- `heartbeat` 是否启用：
  - 是，调度层已经启用
- `heartbeat` 是否已经证明带来收益：
  - 否
- 当前卡点是什么：
  - 不是缺调度
  - 而是缺“明确且轻量的有效心跳任务”

## 当前不该怎么做

- 不要把“日志里有 `[heartbeat] started`”误当成“已经有自动化收益”
- 不要为了证明它有用，给所有角色塞一堆空泛任务
- 不要把心跳做成高频重任务，反而制造噪音和重复整理

## 当前最合理的下一步

1. 只给 `谋士` 设计 1 条最小有效心跳
2. 目标不是“多做事”，而是只检查 1-2 个明确高价值信号
3. 连续观察 1 天，再判断是否真的减少手动检查和漏项

## 推荐的最小有效心跳

先只做这 2 件：

- `00_收件箱` 是否出现未处理条目
- `20_项目` 当前活跃项目是否缺少当日推进记录

如果没有明确待办，就继续返回 `HEARTBEAT_OK`。

## 本轮已执行动作

- 已把最小有效 heartbeat 写入：
  - [[HEARTBEAT]]
  - [[OpenClaw配置/01_主控/HEARTBEAT]]
- 当前设计已经从“空心跳”升级为“有明确检查目标的最小心跳”
- 已完成一次本地模拟触发验证：
  - `moushi` 能按新规则读取 [[HEARTBEAT]]
  - 在当前无明确待办时，正确返回 `HEARTBEAT_OK`
- 下一步只需要做后续收益观察，判断它是否真的减少手动检查和漏项

## 结论收口

- 当前 `heartbeat` 的真实状态应表述为：
  - “调度已启用，但收益未验证”
- 下一步不是“继续开更多 heartbeat”
  - 而是“先把第一个有效 heartbeat 任务做小、做准、做可验证”

## 关联

- [[HEARTBEAT]]
- [[OpenClaw配置/01_主控/HEARTBEAT]]
- [[20_项目/OpenClaw与Obsidian自动化/13_生产级部署计划]]
- [[20_项目/OpenClaw与Obsidian自动化/04_执行清单]]
