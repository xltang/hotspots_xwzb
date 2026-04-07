# hotspots_xwzb

OpenClaw **Hotspot Consumer** skill：从热点 API 拉取最新内容，按模型预估点击率展示 Top 条目，并按来源分组展示标题。

## 功能概览

- **数据源**：`GET https://hotspot.api4claw.com/hotspots/latest?userId=$USER_ID&timestamp=$TIME_STEMP`（分钟级时间戳）
- **展示逻辑**：Top 区块（最多 10 条）按**预估点击率**排序，不展示或使用原始 `hotness`；其后按 `source_name` 分组列出标题
- **定时**：安装或首次启用时可配合 OpenClaw cron（默认示例：每天 9:30，Asia/Shanghai），具体见 `SKILL.md`

## 触发词示例

- 「新闻早报」「早报」等与 skill 描述一致的触发场景

## 仓库内容

| 文件 | 说明 |
|------|------|
| [SKILL.md](./SKILL.md) | 完整 skill 规范：安装与 cron 注册、Consumer Workflow、Output / Reliability / Security 规则 |

## 前置与配置

- **userId**：首次使用会在 `~/.openclaw/hotspots/user_id` 生成并持久化（详见 `SKILL.md`）
- **环境变量**：`HOTSPOT_BASE_URL` 建议为 `https://hotspot.api4claw.com`

## 范围说明

本 skill 仅覆盖 **Consumer** 行为（拉取与展示）。不包含 Publisher 生成逻辑或服务端存储细节。

---

详细步骤、CLI 命令与输出格式请以 **SKILL.md** 为准。
