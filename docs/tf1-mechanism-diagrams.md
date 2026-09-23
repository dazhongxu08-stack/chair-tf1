# 合脊 TF-1 带尺寸机构简图（中文）

> 配套：`docs/tf1-mechanical-structure-analysis.md`  
> 单位：**mm**。示意非 CAD。头枕前后行程 **TBD**。  
> **修改后口径：** 扶手 4D 纯机械；上背左右分块各 3DOF。

## 先打开这个（修改后结构图）

| 文件 | 说明 |
| --- | --- |
| [`media/tf1-structure-updated.html`](../media/tf1-structure-updated.html) | **推荐**：修改后结构总图 + 侧视 + 背系分块（Safari） |
| [`media/tf1-structure-overview.png`](../media/tf1-structure-overview.png) | 机构层级总图 PNG |
| [`media/tf1-side-structure-updated.png`](../media/tf1-side-structure-updated.png) | 侧视（修改后） |
| [`media/tf1-back-layers.png`](../media/tf1-back-layers.png) | 背系正视（左右分块） |

macOS：

```bash
open -a Safari "$HOME/Library/Application Support/Cursor/AgentStores/cursor_agent_stores/bc-42a51c64-43dd-46eb-b684-f91ee822ddd8/files/media/tf1-structure-updated.html"
```

或下载 GitHub zip 后：

```bash
open -a Safari ~/Downloads/chair-tf1-main/media/tf1-structure-updated.html
```

## 全套简图（含早期尺寸图）

| 文件 | 说明 |
| --- | --- |
| [`media/tf1-mechanism-preview.html`](../media/tf1-mechanism-preview.html) | 图1–4 合集预览 |
| [`media/tf1-side-overall.png`](../media/tf1-side-overall.png) | 图1 侧视总成（早期） |
| [`media/tf1-lumbar-sled.png`](../media/tf1-lumbar-sled.png) | 图2 腰靠滑架 |
| [`media/tf1-recline-envelope.png`](../media/tf1-recline-envelope.png) | 图3 倾仰档位 |
| [`media/tf1-back-layers.png`](../media/tf1-back-layers.png) | 图4 背系正视（已更新分块） |

## 尺寸总表（修改后）

| 部件 | 外包络 / 关键尺寸 | 运动行程 |
| --- | --- | --- |
| 头枕 | 360 × 200 | 升降 80；外翻 45°；内翻 90°；前后 **TBD** |
| 靠背框 | 500 × 570 | 升降 50 |
| 上背 | 500 × 340 外包络；**左/右分块** | **每块** ↑50；AP 50；节距 ±15° |
| 腰靠 | 480 × 240 | ↑50；AP 50；节距 ±15° |
| 扶手 | — | **4D 纯机械**（↑70 / 前后40 / 侧摆 / 旋转；无电机） |
| 座高 | 座面离地 | 450–550 |
| 倾仰 | 座–背夹角 | 90° / 100° / 130° / 160° |

*更新：2026-09-23 · 增加修改后结构总图专页*
