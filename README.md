# Doc_to_id

**Drive-centered publishing system：把一本書當成可持續維護的 Book Project，再由同一套出版引擎輸出 InDesign 一鍵建書包。**

這個 repo **不是某一本書的資料庫**。它是共用的「出版社／排版引擎」。

每一本書的權威資料放在 Google Drive 的獨立 **Book Project** 中；本 repo 負責讀取 Book Project、執行出版編輯流程、分析／鎖定原型書設計、產生 DOCX→InDesign 建置設定、跑 Regression / Full QA，最後匯出可重現的一鍵導入包。

## 新對話怎麼開始

任何新 agent / 新對話都先讀：

1. `SKILL.md`
2. `START_HERE.md`
3. `AGENT_CONTRACT.md`

如果使用者尚未指定 Book Project，第一個問題固定是：

> **這次要處理哪一個 Google Drive Book Project？請給我資料夾連結或 Project 名稱。**

如果使用者已經在開場提供 Project 連結／名稱，不要重問，直接進行 Project Restore。

## 核心原則

- **Repo = 出版引擎與方法。**
- **Google Drive Book Project = 一本書的權威資料庫。**
- **一鍵 InDesign 包 / INDD / PDF / QA = 可重建的 Build Artifact，不是唯一真相來源。**
- Chicago、MLA 等是引用／學術規範，不等於整本書的視覺設計。
- 先判斷「這是什麼書」，再決定「它怎麼長」。
- DOCX 先語意化；Design Profile 再決定版面。
- 特殊構圖若來源不可靠，標記 `SPECIAL_LAYOUT` 並保留洞，不得擅自把錯誤 DOCX 幾何當原作。
- Regression FAIL 時禁止 Full Build。
- Full QA FAIL 時禁止直接手修 INDD 冒充來源修復。

## Repo 導覽

- `editorial/`：出版編輯、Chicago baseline、結構與 house style
- `design/`：原型書分析與 Design Profile
- `production/`：DOCX 語意層、InDesign 建置、特殊版面與輸出
- `qa/`：Regression、Full Book、視覺校樣
- `schemas/`：Book Project / Design / Structure / Build 的機器可讀 schema
- `templates/`：建立新 Book Project 的模板
- `profiles/`：可重用設計 Profile；Prototype01 是第一個 reference profile
- `reference/`：事故與實作經驗，不是通用規則本身

目前狀態：**v0.1 架構建立完成。** 通用 exporter / Drive Project 自動建置器將在後續版本接上現有 InDesign 2022 reference implementation。
