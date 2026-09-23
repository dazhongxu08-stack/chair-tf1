# 新开 Agent 后请直接发这一句

当前这次会话**拿不到** My Secrets（密钥只在 Agent **启动时**注入）。你已在 My Secrets 建好 token 后，请：

1. **确认密钥名称正好是** `GITHUB_TOKEN`（不是 `GitHub Token`、`github_token`、`GH_PAT` 等）
2. **新开一个 Cloud Agent**（不要在本会话继续）
3. 复制发送：

```text
用环境里的 GITHUB_TOKEN，运行 scripts/push-chair-docs-to-github.sh，把 chair-tf1-docs 最新内容推到 dazhongxu08-stack/chair-tf1。推完确认 docs 里有 tf1-decisions-open.html 和 tf1-design-review.md，并提醒我核对仓库页面。
```

推成功后打开：https://github.com/dazhongxu08-stack/chair-tf1/tree/main/docs

## 若新 Agent 仍报 Missing GITHUB_TOKEN

- Secrets 名称必须精确为 `GITHUB_TOKEN`
- 类型用 **Runtime Secret**
- Apply to 要包含本仓库（或 All repositories）
- 必须是 **新开的** Agent，旧会话不会补注
