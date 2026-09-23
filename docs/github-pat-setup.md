# 怎么设置：把最新文档推到 GitHub

目标仓库：[https://github.com/dazhongxu08-stack/chair-tf1](https://github.com/dazhongxu08-stack/chair-tf1)

> **想长期进环境、不要每次聊天粘贴？**  
> 请看 → [github-secrets-env-setup.md](github-secrets-env-setup.md)（Cursor Dashboard → Secrets → Runtime Secret `GITHUB_TOKEN`）。

## 1. 在 GitHub 新建 Token（PAT）

1. 打开：[https://github.com/settings/tokens](https://github.com/settings/tokens)  
   （或：GitHub → 右上角头像 → **Settings** → 左侧最下 **Developer settings** → **Personal access tokens**）
2. 建议用 **Fine-grained token**（细粒度）：
   - **Generate new token**
   - Token name：例如 `chair-tf1-upload`
   - Expiration：选短一点（7–30 天）
   - Resource owner：选 **dazhongxu08-stack**
   - Repository access：**Only select repositories** → 勾选 **chair-tf1**
   - Permissions → Repository permissions：
     - **Contents**：Read and write
     - **Metadata**：Read-only（一般会自动带上）
   - 生成后 **立刻复制**（只显示一次）
3. 若用 **Classic token**：勾选 `repo` 权限即可（权限更大，用完建议尽快作废）。

> 若旧 token 曾发在聊天里：请到同一页面 **Revoke** 作废，再用新 token。

## 2. 交给 Cursor 云端 Agent 使用（推荐）

在 Agent 对话里发一条（把 `ghp_xxx` 换成你的新 token）：

```text
请用这个新 PAT 把最新文档推到 dazhongxu08-stack/chair-tf1：
GITHUB_TOKEN=ghp_xxx
推完后确认仓库里有 tf1-decisions-open.html 和 tf1-design-review.md，然后提醒我作废 token。
```

Agent 会跑仓库里的脚本：`scripts/push-chair-docs-to-github.sh`。

## 3. 你自己在电脑终端推（可选）

若本机已装 git，且已 clone 该仓库：

```bash
export GITHUB_TOKEN=ghp_xxx
# 若脚本在 Cursor 项目里：
./scripts/push-chair-docs-to-github.sh
```

或用 GitHub 网页：**Add file → Upload files**，把 Project 里 `docs/`、`media/` 最新文件拖上去（适合只补几个文件）。

## 4. 推完怎么确认

打开：  
[https://github.com/dazhongxu08-stack/chair-tf1/tree/main/docs](https://github.com/dazhongxu08-stack/chair-tf1/tree/main/docs)

应能看到：

- `tf1-decisions-open.html`
- `tf1-decisions-latest.md`
- `tf1-design-review.md`

## 5. 安全

用完后到 [Tokens 设置页](https://github.com/settings/tokens) **Revoke** 该 token。不要把 token 写进仓库文件或 README。
