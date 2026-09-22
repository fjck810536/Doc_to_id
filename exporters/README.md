# Exporters

目標：把 Google Drive Book Project 的 authoritative state 匯出成 **自包含的一鍵 InDesign Build Package**。

Exporter 不應把聊天內容當 input。

## 必要 input

- PROJECT.json
- Publication Source
- BOOK_STRUCTURE.json
- DESIGN_PROFILE.json
- required assets
- special-layout manifests
- target runtime

## Output

- launcher
- scripts
- config snapshot
- exact source snapshot
- required assets subset
- regression expectation
- checksums
- build manifest
- README

## 可重現性

同一 Project version + same Design Profile + same engine version 應產生等價 build configuration。
