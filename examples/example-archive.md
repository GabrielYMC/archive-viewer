---
type: conversation-archive
status: archived
domain: ai-agent
created: 2026-04-13
archived: 2026-04-14
part: 1/2
tags: [kanban, multi-role, supervisor, markdown, skills]
source: claude-ai
related_domains: [pkm-productivity]
related_conversations:
  - 2026-04-13_example-archive-2
---

# 範例：用 Markdown 做多角色專案管理

## 脈絡

探索如何用最輕量的基礎設施（Markdown 檔案 + 角色切換 + 外部督導）為 AI agent 加入專案管理能力。

## 發展軌跡

比較多個開源 agent 框架 → 發現「重量級編排」和「輕量級協作」是兩個不同方向
→ 選擇輕量路線：一個 kanban.md 當看板、roles/*.md 當行為約束
→ 加入 supervisor hook（外接強模型，~900 token/次做品質判斷）
→ 通用化為 6 種專案原型（軟體、活動、志工、研究、行銷、內容）

## 關鍵概念

- **Markdown kanban**：一個 .md 檔案就是整個看板，欄位和角色完全自訂
- **角色即約束**：不是多個 agent，而是同一個 agent 載入不同角色檔來切換視角
- **Supervisor hook**：外接強 LLM，只看 500 字摘要，三元判斷 APPROVE/REVISE/ESCALATE

## 決議

- 決定採用 Markdown kanban 作為唯一狀態源
- 決定 Supervisor 用 Opus 級模型，限 500 字摘要輸入

## 產出物

- kanban-agent-pm.skill — 完整 skill 套件（6 references + 4 scripts + 3 presets）

## 關鍵字

kanban, 多角色協作, supervisor, markdown, 以簡馭繁, agent skills, 專案管理

## 對話全文

<details>
<summary>展開原始對話（Part 1 範圍）</summary>

H: 我想讓 AI agent 有簡單的專案管理能力，可以分幾個角色合作，用 kanban 當溝通基礎。

A: 核心思路是：不引入框架，用 Markdown 檔案當 Kanban，用 system prompt 角色切換當多角色，用一個便宜的 supervisor call 當品質關卡。一個 kanban.md 放在專案根目錄就夠了。

H: 可以做成 skill 嗎？

A: 好，讓我用 skill-creator 的規範來打包。每個角色一個 .md 檔，supervisor 用固定 prompt 模板，整個系統的基礎設施就是幾個 Markdown 檔案加一個 Python 腳本。

H: 但你預設了軟體開發的立場，我有很多不同類型的專案。

A: 你說得對。讓我通用化——佔位符驅動的模板、6 種專案原型、init_project.py 支援 --preset 參數。

</details>
