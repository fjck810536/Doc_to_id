# Scripts

本目錄預留通用 production scripts。

## 原則

- 核心 scripts 應讀 Project Snapshot / Design Profile，而不是硬編某一本書標題。
- book-specific hack 應放回 Book Project 或 reference implementation，不進 core。
- target InDesign API 由 `PROJECT.json` 決定。
- 每個 build script 必須產生 machine-readable status 與 QA。

## Roadmap

1. 將既有 InDesign 2022 v4 reference script 拆成：
   - generic engine
   - project adapter
   - profile adapter
2. 建立 Book Project → Build Package exporter。
3. 建立 schema validation。
4. 建立 release manifest / checksums。
