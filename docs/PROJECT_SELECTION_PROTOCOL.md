# Project Selection / Restore Protocol

## 觸發

新對話、新 agent、模型切換、長對話壓縮後恢復、跨裝置繼續工作。

## 規則

### 沒有指定 Project
第一個問題：

> **這次要處理哪一個 Google Drive Book Project？請給我資料夾連結或 Project 名稱。**

這個問題優先於排版細節。

### 已指定 Project
不要再問一次。直接 restore。

## Restore

讀 `PROJECT.json` 後確認：

- project_id
- book title
- schema version
- publication source
- design profile
- current stage
- production target
- last good build
- next action

再讀 CURRENT_STATE / NEXT_ACTION / structure / design / latest QA。

## Restore Report

開始實際修改前，agent 內部必須形成這個最小狀態：

```
PROJECT:
LAST GOOD:
CURRENT:
UNRESOLVED:
NEXT:
DO NOT:
```

必要時可以向使用者簡短回報，但不需要每次展示全部內部結構。
