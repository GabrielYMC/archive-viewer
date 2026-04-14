# Archive Viewer

**對話封存檔的三欄式閱讀器——單一 HTML 檔，零依賴，拖曳即用**

```
archive-viewer/
├── archive-viewer.html   ← 瀏覽器直接開，不需要安裝任何東西
├── README.md
├── LICENSE
└── examples/             ← 範例封存檔
    └── example-archive.md
```

## 這是什麼？

一個專門閱讀 [conversation-archive protocol](https://github.com/YOUR_USERNAME/agent-commons)
格式封存檔的瀏覽器工具。

三欄佈局：
- **左欄**：檔案列表 + Tag 過濾（光棒導航）
- **中欄**：結構化摘要（脈絡、軌跡、概念、決議、產出物）
- **右欄**：對話全文渲染（User/Agent 氣泡式呈現）

## 使用方式

1. 下載 `archive-viewer.html`
2. 用瀏覽器打開
3. 把 `.md` 封存檔拖進去

就這樣。不需要 Node.js、不需要 Python、不需要任何 server。

## 功能

- **多檔拖曳**：一次拖入所有封存檔
- **光棒導航**：`↑`/`↓` 或 `j`/`k` 切換檔案
- **Tag 過濾**：自動收集所有 frontmatter tags + 關鍵字區塊，點擊過濾
- **全域搜尋**：`/` 跳到搜尋框，搜尋標題、tags、摘要內容
- **對話搜尋**：右欄獨立搜尋框，搜尋對話全文內容並高亮
- **相關對話跳轉**：`related_conversations` 欄位是可點擊的連結
- **Evergreen 萃取**：中欄「✦ 萃取 Evergreen」按鈕，一鍵開啟 seedling 模板編輯器，匯出為 .md 直接放入 Obsidian vault

## 鍵盤快捷鍵

| 按鍵 | 功能 |
|------|------|
| `↑` `↓` 或 `j` `k` | 切換檔案 |
| `/` | 跳到搜尋框 |
| `Esc` | 清除所有篩選 |

## 封存檔格式

本工具讀取遵循 conversation-archive protocol 的 .md 檔。最小格式：

```markdown
---
type: conversation-archive
status: archived
domain: your-domain
created: 2026-04-13
archived: 2026-04-14
tags: [tag1, tag2]
source: claude-ai
---

# 對話標題

## 脈絡
一兩句話描述。

## 發展軌跡
A → B → C

## 關鍵概念
- **概念名**：定義

## 決議
- 決定了 X

## 產出物
- 檔案名 — 說明

## 關鍵字
tag1, tag2, tag3

## 對話全文

<details>
<summary>展開原始對話</summary>

H: 使用者訊息
A: Agent 回應

</details>
```

## 與其他 repo 的關係

```
agent-commons           ← 定義 protocol（規範）
conversation-archiver   ← 生產封存檔（寫入端）
archive-viewer          ← 閱讀封存檔（讀取端）  ← 你在這裡
kanban-agent-pm         ← 使用以上所有的垂直應用
```

## 授權

MIT
