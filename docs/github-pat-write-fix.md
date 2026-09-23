# GitHub 推送 403：补 Contents 写权限

## 已确认

- 环境已注入 `GITHUB_TOKEN`（账号 `dazhongxu08-stack`）
- 能读仓库 `chair-tf1`（HTTP 200）
- **不能写**：创建 blob / `git push` → 403
  `Resource not accessible by personal access token`

## 你需要改的（同一 token，不必换 Secrets 值）

1. 打开：https://github.com/settings/personal-access-tokens
2. 编辑当前 Fine-grained token
3. **Repository access**：包含 `dazhongxu08-stack/chair-tf1`
4. **Permissions → Contents：Read and write**（关键）
5. Save

改完后在对话里说「已改权限」，Agent 会立刻重跑推送。

若用的是 Classic token：需勾选 `repo` 权限。
