# InDesign Build Protocol

## Pipeline

```
Book Project
  ↓ validate
Publication Source
  ↓ semantic normalization
Build Config
  ↓
Environment / font check
  ↓
Regression
  ↓ PASS only
Full Build
  ↓
Full QA
  ↓
Release candidate
```

## Build Artifact

一鍵包必須包含：

```
BOOK_ID_BUILD/
├── 00_一鍵建書.command
├── README.md
├── VERSION.txt
├── Manuscript/
├── Config/
│   ├── PROJECT_SNAPSHOT.json
│   ├── BOOK_STRUCTURE.json
│   ├── DESIGN_PROFILE.json
│   ├── BUILD_MANIFEST.json
│   └── CHECKSUMS.sha256
├── Scripts/
├── Regression/
└── Assets/ (needed subset only)
```

## InDesign version

Target 必須由 Project 指定，不能由 agent 自動升級 API。

舊版 InDesign / ExtendScript 專案：
- 用對應宿主版本支援的 API；
- 不把 UXP / `.idjs` 假設套到不支援的版本。

## Article Opening

優先使用單一 story 中的結構：

```
Kicker
Title
Paragraph Rule Below
First body paragraph
```

並搭配 keep options。

不要把 kicker/title/rule 拆成三個會隨 reflow 漂移的絕對定位物件，除非 Design Profile 明確要求且有穩定 anchor。

## Running heads

使用語意樣式、Text Variables 或可重建的 section state。

章名更動後重新 build 應能自動更新頁眉。

## Generated INDD

Full INDD 是重要工作產物，但不是 source-of-truth。

需要人工特殊排版時，回寫為：
- Special Layout source
- object manifest
- 或可追蹤的 override package
