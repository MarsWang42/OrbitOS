---
type: research
created: 2026-03-22
status: complete
source_role: moushi
applicable_roles: [moushi, jishu, diaoyan]
confidence: A
platform: Obsidian
thinking_mode: 本机验证, 低风险试点, 取舍判断
claim_type: 验证
evidence_level: A
validation_status: 已验证
tags: [research, obsidian, cli, automation, pilot]
topic: Obsidian CLI最小试接方案
---

# Obsidian CLI最小试接方案

## 一句话结论

`Obsidian CLI` 在这台机器上已经不只是“命令入口存在”，而是完成了本机冒烟验证：`version`、`daily:path`、`read`、`help`、一次真实 `append` 和一次真实 `create` 都已跑通。  
因此它已经适合进入当前项目的“低风险局部试接”阶段，但还不适合立刻替代正式笔记的精细写作和全链路落盘。

## 这轮要回答什么

- 本机 `Obsidian CLI` 到底有没有真正可用
- 它最适合先接到当前主链路的哪一段
- 哪些动作现在可以试，哪些动作仍不该立刻迁移

## 本机已验证事实

### 1. 命令入口和安装链存在

- `obsidian` 当前路径：
  - `/opt/homebrew/bin/obsidian`
- 该路径实际是 wrapper：
  - `/opt/homebrew/Caskroom/obsidian/1.12.4/obsidian.wrapper.sh`
- wrapper 最终转发到：
  - `/Applications/Obsidian.app/Contents/MacOS/Obsidian`

这说明本机不是“只在文档里有 CLI”，而是桌面应用和命令入口都已经装上。

### 2. 版本查询已通过

- 本机执行：
  - `obsidian version`
- 返回：
  - `1.12.4 (installer 1.12.4)`

### 3. 当前 Vault 定位已通过

- 本机执行：
  - `obsidian daily:path`
- 返回：
  - `10_日记/2026-03-22.md`

这说明 CLI 已经能在当前 Vault 上正确解析“今日日记”。

### 4. 读取能力已通过

- 本机执行：
  - `obsidian read path='10_日记/2026-03-22.md'`
- 已成功返回今日日记正文

### 5. 写入能力已通过

- 本机执行：
  - `obsidian append path='10_日记/2026-03-22.md' ...`
- 已成功回写一条：
  - `Obsidian CLI 本机冒烟验证`

所以当前至少可以确认：它不只是能“查帮助”，而是已经完成一条真实写入。

### 6. 草稿创建能力已通过

- 本机执行：
  - `obsidian create path='99_系统/归档/研究/2026/03/Obsidian_CLI研究草稿创建验证_2026-03-22.md' ...`
- 随后执行：
  - `obsidian read path='99_系统/归档/研究/2026/03/Obsidian_CLI研究草稿创建验证_2026-03-22.md'`
- 已确认：
  - 文件创建成功
  - frontmatter 与正文内容可正确读回

这说明 `create` 已经不只是文档能力，而是当前 Vault 中已验证通过的真实能力。

## 官方能力边界

根据官方文档，`Obsidian CLI` 当前已经提供：

- `daily:append`
- `append`
- `create`
- `read`
- `move`

这意味着它天然适合承担：

- 低风险追加写入
- 草稿创建
- 简单读取
- 简单文件级动作

但文档也明确指出：

- CLI 依赖 `Obsidian 1.12` 安装器
- CLI 使用时需要 Obsidian 桌面应用运行

## 当前最适合先接的 3 个场景

### 1. 今日日记追加

最适合，因为：

- 路径稳定
- 格式简单
- 追加型写入风险低
- 即使格式略有偏差，也容易人工修正

### 2. 研究草稿创建

适合用：

- `obsidian create`

来先生成研究草稿或模板化空笔记，再由 `谋士` 做精细补写。  
这一步本机已经完成一次真实验证。

### 3. 低风险日志型回写

适合追加：

- 项目进展记录
- 验证日志
- 巡检结果

这类内容的共同点是：

- 更像“补一条记录”
- 不是“精细重排整篇正式文档”

## 当前不该立刻迁移的部分

### 1. frontmatter 很重的正式研究页

原因：

- 当前正式笔记经常需要精确控制 YAML、章节结构、wikilinks 和结论类型
- 这类内容更适合先由 `apply_patch` 或人工精修

### 2. 复杂的跨文件重构

例如：

- 大批量移动
- 重命名
- 多文件联动改结构

这类动作虽然 CLI 有能力覆盖一部分，但在当前项目阶段还不是最高价值。

### 3. 用 CLI 替代整个主控判断

CLI 是 Obsidian 的自动化入口，不是 `谋士` 的替代品。  
主控判断、意图分流、研究收口和结论提炼，仍然应该由 `OpenClaw + 谋士` 承担。

## 项目日志类回写判断

### 一句话判断

值得局部迁移，但不适合直接迁到当前这张项目总表。

### 为什么

这轮本机验证和当前项目文件结构一起看，能得到一个很明确的边界：

- `obsidian append` 的行为是“追加到文件尾部”
- 当前 [[20_项目/OpenClaw与Obsidian自动化/OpenClaw与Obsidian自动化]] 的 `## 进展` 位于文件中部
- 该文件后面还有 `## 相关`、`## 备注`、`## 项目框架`

这意味着如果直接把项目进展回写迁给 `obsidian append`，新日志会落到整篇文件末尾，而不是落到 `## 进展` 区域里。

### 结论

- 当前项目总表：
  - 不适合直接用 `obsidian append` 写进展
- 独立追加型日志文件：
  - 适合
- 文件尾专门日志段：
  - 也适合

### 最稳的迁移方式

1. 保持项目总表继续由结构化编辑维护
2. 如要迁日志回写，先拆出“追加型项目日志文件”
3. 或者把日志段移到目标文件尾部，再用 CLI 追加

### 当前已落地实现

这一步已经在项目目录中实际落地：

- [[20_项目/OpenClaw与Obsidian自动化/19_项目追加日志]]

并且已用 `obsidian append` 成功追加首条项目日志。  
说明“追加型项目日志文件”不再只是建议，而是已经变成当前项目可直接使用的承接层。

## 最小试接建议

### 当前建议顺序

1. 先把今日日记追加当成默认低风险动作
2. 再试 1 次研究草稿创建
3. 再判断项目日志类回写是否值得切一部分给 CLI

### 当前不建议顺序

1. 不先改正式研究页主模板
2. 不先改复杂项目总表
3. 不先做整套落盘流程重构

## 这轮形成的判断

### 事实

- `Obsidian CLI` 本机已可用
- 当前至少已验证到：
  - 版本查询
  - 日记路径解析
  - 文件读取
  - 帮助命令
  - 一次真实追加写入
  - 一次真实研究草稿创建

### 规律

- 对当前项目最稳的接入方式不是“一次性迁移写入逻辑”，而是“先把低风险追加型动作切过去”
- 对项目目录来说，`Obsidian CLI` 最先落地的正确位置不是项目总表，而是追加型项目日志文件

### 下一步

1. 这份追加型项目日志文件已经通过 `3` 类真实样本观察：
   - 工具验证
   - 官方 release 巡检
   - 外部线索补锚后的研究判断
2. 当前可以确认：
   - `Obsidian CLI` 适合作为低风险追加型日志的默认写回层
   - 适合继续承接项目巡检、验证记录、简短判断这类“文件尾部追加”场景
3. 当前仍不建议扩大到：
   - 项目总表中部结构
   - 重 frontmatter 的正式研究页
   - 复杂多文件联动重构
4. 如要继续扩，只优先扩到其他追加型场景，例如：
   - `daily:append`
   - 独立研究日志文件
   - 独立巡检日志文件
3. 暂不动正式研究页和知识卡主写入流程

## 关联

- [[99_系统/归档/研究/2026/03/OpenClaw与Obsidian整体架构与自动化链路_2026-03-22]]
- [[99_系统/归档/研究/2026/03/Obsidian_CLI研究草稿创建验证_2026-03-22]]
- [[20_项目/OpenClaw与Obsidian自动化/OpenClaw与Obsidian自动化]]
- [[20_项目/OpenClaw与Obsidian自动化/19_项目追加日志]]
- [[20_项目/OpenClaw与Obsidian自动化/10_工具注册表]]
- [[10_日记/2026-03-22]]

## 参考资源

- [Obsidian Changelog](https://obsidian.md/changelog/)
- [Obsidian CLI Help](https://help.obsidian.md/cli)
