# Discord部署指南

## 当前状态

- 本机已安装 `openclaw`，当前版本为 `2026.3.13`
- OpenClaw 配置文件位于 `~/.openclaw/openclaw.json`
- 现有配置里已经预留了 `discord / bot-moushi -> moushi` 这条路由
- 当前还缺 3 个关键值：
  - `Bot Token`
  - `Server ID`
  - `User ID`

## 当前补充判断（2026-03-22）

- 这条 Discord 路线已经不只是“能不能接上”，而是官方文档明确支持：
  - `DM`
  - `guild channels`
  - `pairing`
  - allowlist / `requireMention`
  - voice channels
- 当前最稳的起步方式仍然是：
  - 先 `DM pairing`
  - 再进私有服务器
  - 默认保留 `requireMention: true`
- 官方运行模型里：
  - DM 默认进共享主 session
  - guild channel 默认是独立 session
  - 这很适合你后续把 `#coding / #research / #home` 之类频道做分工隔离
- 安全边界要记住：
  - Discord 混合信任多人频道不是官方推荐边界
  - Discord voice transcript 在 `<= 2026.3.1` 有过 owner 标记漏洞，`>= 2026.3.2` 已修复
  - 你本机当前是 `2026.3.13`，所以版本上已覆盖这个修复

## 推荐顺序

先打通 Discord 私聊，再放开私有服务器频道。

这样做有 2 个好处：

- 更容易排错
- 不会一开始就把机器人暴露到整个服务器

## 第1步：在 Discord 创建机器人

到 Discord Developer Portal 新建一个 Application，并创建 Bot。

需要打开这些权限：

- `Message Content Intent`：必开
- `Server Members Intent`：建议开
- `Presence Intent`：可选

生成邀请链接时，至少勾选这些 Scope / Permission：

- Scope：`bot`
- Scope：`applications.commands`
- Permission：`View Channels`
- Permission：`Send Messages`
- Permission：`Read Message History`
- Permission：`Embed Links`
- Permission：`Attach Files`

如果你希望它能加表情，再额外勾选 `Add Reactions`。

## 第2步：拿到 3 个关键值

在 Discord 客户端打开开发者模式后，保存这 3 个值：

- `Bot Token`
- `Server ID`
- `User ID`

另外把服务器的 `Direct Messages` 打开，方便第一次私聊配对。

## 第3步：把 Discord 账号接到 OpenClaw

你当前配置已经有 `bot-moushi` 的 Discord 路由，所以最直接的做法是给这个账号补上 token。

```bash
export DISCORD_BOT_TOKEN='你的 Bot Token'
openclaw channels add --channel discord --account bot-moushi --name "谋士" --token "$DISCORD_BOT_TOKEN"
openclaw gateway restart
openclaw channels list
openclaw channels status --probe
```

说明：

- 这里不要用 `--use-env`
- 因为 `DISCORD_BOT_TOKEN` 的环境变量兜底只对默认账号生效
- 你当前要接的是命名账号 `bot-moushi`

## 第4步：完成第一次 DM 配对

1. 在 Discord 私聊你的机器人
2. 它会回你一个配对码
3. 在本机执行：

```bash
openclaw pairing list discord
openclaw pairing approve discord <配对码>
```

配对码有效期默认是 1 小时。

如果你更习惯从现有通道操作，也可以在已经连好的 OpenClaw 通道里让 `谋士` 帮你批准这个配对码。

## 第5步：把私有服务器加入 allowlist

先用安全模式起步：

```json5
{
  "channels": {
    "discord": {
      "groupPolicy": "allowlist",
      "guilds": {
        "你的ServerID": {
          "requireMention": true,
          "ignoreOtherMentions": true,
          "users": ["你的UserID"]
        }
      }
    }
  }
}
```

这段配置的意思是：

- 只允许指定服务器接入
- 默认必须 `@机器人` 才回应
- 只允许你本人触发
- 如果消息里提到别的用户但没提到机器人，就忽略

等你确认稳定后，再改成更顺手的私有服务器模式：

```json5
{
  "channels": {
    "discord": {
      "guilds": {
        "你的ServerID": {
          "requireMention": false
        }
      }
    }
  }
}
```

## 第6步：验证是否接通

优先做这 3 个检查：

```bash
openclaw channels list
openclaw channels status --probe
openclaw doctor
```

如果需要主动发一条测试消息，目标写法要用前缀：

- 私聊：`user:<UserID>`
- 频道：`channel:<ChannelID>`

例如：

```bash
openclaw message send --channel discord --account bot-moushi --target "user:你的UserID" --message "Discord 已接通"
```

## 最小可用方案

如果你的目标只是“先在 Discord 上用起来”，最小闭环就是：

1. 创建 Bot
2. 开 `Message Content Intent`
3. 拿到 `Bot Token / Server ID / User ID`
4. 执行 `channels add`
5. 私聊配对
6. 只开放你自己的私有服务器

## 下一阶段值得保留的 2 个扩展点

1. **频道隔离当 Mission Control 雏形**
   - 利用 guild channel 独立 session，把 `research / coding / ops` 分到不同频道
2. **语音先当后续扩展**
   - 官方已支持 voice，但不要在多人混合信任频道里先开
   - 更适合等文本 DM / 私有频道稳定后，再单独验证

## 你这台机器的判断结论

基于当前本机状态，OpenClaw 本身不是阻塞点，真正缺的是 Discord 侧凭据和 ID。

等这 3 个值补齐后，可以直接推进到可用状态：

- `Bot Token`
- `Server ID`
- `User ID`
