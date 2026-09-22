# Handoff Protocol

## 目的

讓「完全不知道前一個聊天內容」的新 agent 仍能安全接班。

## 每次重要 session 結束

更新：

### CURRENT_STATE.md
只寫現在為真的狀態：
- 已完成
- current engine/profile/project versions
- last good build
- known unresolved
- do-not-regress facts

### NEXT_ACTION.md
下一步必須具體、可執行。

### CHANGELOG.md
追加本次改動與原因。

### LAST_GOOD_BUILD.json
只在新的 build 真正通過所需 Gate 後更新。

## 不應放在 handoff 的內容

- 冗長聊天摘要
- 已被推翻的舊推測（除非在事故紀錄）
- 與下一步無關的討論

Handoff 是 runtime state，不是聊天備份。
