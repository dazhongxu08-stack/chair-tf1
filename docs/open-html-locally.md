# 本地打开 HTML（macOS）

不要用 `http://127.0.0.1:…`（那是云端地址，会报 -102）。

## 方法一：从 GitHub 下载整包（推荐）

1. 浏览器打开：
   https://github.com/dazhongxu08-stack/chair-tf1/archive/refs/heads/main.zip
2. 解压到「下载」文件夹（得到 `chair-tf1-main`）
3. 终端执行：

```bash
open -a Safari ~/Downloads/chair-tf1-main/docs/tf1-decisions-open.html
```

机构预览：

```bash
open -a Safari ~/Downloads/chair-tf1-main/media/tf1-mechanism-preview.html
```

也可在 Finder 里双击 HTML → 打开方式 → Safari。

## 方法二：只下单个决策页

1. 打开：
   https://raw.githubusercontent.com/dazhongxu08-stack/chair-tf1/main/docs/tf1-decisions-open.html
2. 菜单「文件 → 存储…」存到桌面
3. 双击用 Safari 打开

## 方法三：离线 zip

仓库内：`media/tf1-local-html.zip`  
或 Project：`media/tf1-local-html.zip`  
解压后打开 `tf1-decisions-open.html`。

## 建议优先打开

| 文件 | 内容 |
| --- | --- |
| `docs/tf1-decisions-open.html` | 最新产品决策（轻量） |
| `media/tf1-mechanism-preview.html` | 机构简图预览 |
| `docs/tf1-decisions-latest.html` | 含内嵌图的完整决策页 |
