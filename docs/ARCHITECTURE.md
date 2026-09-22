# Architecture — Drive-centered Book Projects

## 概念

```
GitHub: Doc_to_id
  Publishing System
        |
        | read / validate / build
        v
Google Drive Book Project
  一本書的 authoritative database
        |
        v
Export Build Package
        |
        v
InDesign
        |
        v
INDD + PDF + QA
        |
        v
QA / state 回寫 Book Project
```

## 為什麼 Book Project 在 Drive

書籍專案包含大量不適合放普通 Git 的檔案：

- DOCX
- PDF
- INDD
- 圖片／掃描
- 大型校樣
- 可能有授權限制的素材

Drive 適合作為可被作者／編輯直觀管理的專案資料夾。

GitHub 只保存：
- protocol
- schema
- scripts
- design profiles
- reusable tooling
- 事故知識
- reference implementation（不含不應公開的素材）

## Book Project 標準目錄

```
BOOK_PROJECT/
├── 00_PROJECT/
│   ├── PROJECT.json
│   ├── CURRENT_STATE.md
│   ├── NEXT_ACTION.md
│   ├── CHANGELOG.md
│   └── LAST_GOOD_BUILD.json
├── 01_MANUSCRIPT/
│   ├── SOURCE/
│   └── PUBLICATION_SOURCE/
├── 02_EDITORIAL/
│   ├── EDITORIAL_DIAGNOSIS.md
│   ├── BOOK_PROPOSAL.md
│   ├── BOOK_STRUCTURE.json
│   ├── CHICAGO_POLICY.md
│   └── HOUSE_STYLE.md
├── 03_DESIGN/
│   ├── DESIGN_PROFILE.json
│   ├── reference/
│   └── special_layouts/
├── 04_ASSETS/
│   ├── images/
│   ├── captions/
│   └── ASSET_MANIFEST.json
├── 05_QA/
│   ├── regression/
│   ├── full/
│   └── visual/
├── 06_BUILDS/
│   ├── working/
│   └── releases/
└── 99_ARCHIVE/
```

## Authority

`01_MANUSCRIPT` + `02_EDITORIAL` + `03_DESIGN` + `04_ASSETS`
是重建書籍所需要的 source。

`06_BUILDS` 是生成物。理論上可刪除後重建。

## 多本書

同一個 repo 對很多 Drive Book Projects 工作：

```
BOOK_PROJECTS/
├── 共犯者的無終奇語/
├── 小說_A/
├── 評論集_B/
└── 藝術家書_C/
```

不要為每一本書複製一套 agent。
