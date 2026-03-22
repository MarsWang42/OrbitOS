---
title: memory-lancedb-pro 记忆插件大升级
source: B站视频
date: 2026-03-21
type: research
status: archived
source_role: jishu
applicable_roles: [moushi, jishu]
confidence: B
platform: B站
validation_status: 已归档（旧插件观察样本，当前未进主线）
archive_mode: evidence
tags: [OpenClaw, Memory, 插件, AI]
---

# memory-lancedb-pro 记忆插件大升级

来源：B站 - AI超元域
标题：让OpenClaw实现真正自我进化！让龙虾越用越聪明！

---

## 核心功能：智能提取

**智能提取 = 记忆秘书**

- 听完和 AI 的对话后，自动挑出值得记住的内容
- 还会检测之前是否已存在类似内容，避免重复存入

### 工作流程

1. 对话 → 大模型提取内容
2. 向量检索（相似内容检测）
3. 大模型判定：创建新记忆 / 合并到旧记忆 / 跳过

### 智能过滤

- **会存入**：技术偏好、使用习惯、重要信息
- **不会存入**：无关紧要的内容（如"今天天气不错"）

---

## 安装方式

### 两种方案

1. **脚本安装** - 直接运行安装脚本
2. **Skill 自动化安装**（推荐）

### Skill 自动安装

- 专为小白设计，无需执行复杂命令
- 可安装到：OpenClaw、Claude Code、Codex、Windsurf、Cursor 等
- 安装后 AI 会自动知道如何配置和使用

### 安装步骤

1. 安装 Skill
2. 让 AI 告诉你如何安装 memory-lancedb-pro
3. 选择配置方案（在线API / 本地Ollama）
4. 让 AI 自动配置

---

## 配置方案

| 方案 | 特点 |
|------|------|
| 最简单 | 在线 API |
| 最省钱 | 本地 Ollama |
| 功能最全 | 混合方案 |

### 在线 API

- 嵌入模型：Jina 等
- 重排模型：Cohere 等
- 大模型：OpenAI / Claude 等

### 本地方案（Ollama）

- 嵌入模型：BGE-M3、Qwen3-Embedding 等
- 大模型：Qwen3 等

---

## 功能开启

- 写入记忆
- 读取记忆
- 智能提取（核心）
- 去重检测

---

## 项目信息

- GitHub：托管于组织下
- Star：2.4K+
- 贡献者：20+ 位
