# 怎么把 GitHub Token 设进环境（长期，非一次性）

不要把 PAT 贴在聊天里当一次性口令。正确做法是写进 **Cursor Cloud Agents → Secrets**，之后每次新 Agent 启动都会自动注入为环境变量。

## 当前状态

这次会话 **还没有关联的持久 Environment**（`environment: null`）。所以要先有环境，再挂密钥；或先用 **个人 Secrets（My Secrets）** 挂到仓库范围。

## 推荐：Dashboard Secrets（持久）

### A. 个人密钥（最快，跨环境）

1. 打开：[https://cursor.com/dashboard/cloud-agents](https://cursor.com/dashboard/cloud-agents)
2. 进入 **Secrets** / **My Secrets**
3. **Add Secrets**，填：
   - 名称：`GITHUB_TOKEN`（必须这个名字，脚本和 `gh` 才会认）
   - 值：你的 GitHub PAT（Fine-grained，Contents: Read and write，仓库勾选 `chair-tf1`）
   - 类型：**Runtime Secret**（敏感；聊天/日志里会显示成 `[REDACTED]`）
   - Apply to：选对应仓库，或 All repositories
4. **Save**
5. **新开一个 Cloud Agent**（已在跑的这次不会自动拿到新密钥）

### B. 环境级密钥（绑某个 Environment）

1. 先在 Cloud Agents 控制台 **创建并 Save 一个 Environment**（连上你的仓）
2. 打开该环境详情（形如 `…/cloud-agents/environments/e/<id>`）
3. 在 **Runtime secrets** 里添加同名 `GITHUB_TOKEN`
4. Save 后同样 **新开 Agent**

## PAT 怎么建（仍要先做一次）

见同目录 [github-pat-setup.md](github-pat-setup.md) 第 1 节，或：

[https://github.com/settings/tokens](https://github.com/settings/tokens) → Fine-grained → 仓库 `dazhongxu08-stack/chair-tf1` → Contents: Read and write。

## 设好之后 Agent 怎么用

新会话里直接说：「用环境里的 `GITHUB_TOKEN` 把最新文档推到 `dazhongxu08-stack/chair-tf1`」。

脚本会读：`$GITHUB_TOKEN`（见仓库 `scripts/push-chair-docs-to-github.sh`）。

自检（在新 Agent 终端）：

```bash
test -n "$GITHUB_TOKEN" && echo "GITHUB_TOKEN 已注入" || echo "未注入：检查 Secrets 名称/作用域，并确认是新开的 Agent"
```

不要 `echo "$GITHUB_TOKEN"`（Runtime Secret 也会被脱敏；且勿把值打进日志）。

## 不要做的事

| 错误做法 | 原因 |
| --- | --- |
| 把 token 写进 `.cursor/environment.json` | 会进仓库，不安全 |
| 写进 README / 脚本明文 | 同上 |
| 只改 Secrets 却继续用旧 Agent | 密钥在**启动时**注入 |
| 类型选 Build Secret | 只给 Docker 构建用，运行中 Agent 拿不到 |

## 和「聊天里贴一次」的差别

| | 聊天贴 PAT | Dashboard Secrets |
| --- | --- | --- |
| 持久 | 否 | 是 |
| 安全 | 差（进对话记录） | Runtime Secret 会脱敏 |
| 生效 | 当次 | 之后每次新 Agent |

官方说明：[Cloud Agent Setup · Secrets](https://cursor.com/docs/cloud-agent/setup)、[Secrets & Network](https://cursor.com/docs/cloud-agent/security-network)
