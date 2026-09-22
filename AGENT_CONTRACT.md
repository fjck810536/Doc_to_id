# Agent Contract

本檔是不可輕易繞過的 production contract。

## A. 狀態與版本

1. 不得依賴「我記得上一個聊天怎麼做」。
2. Project 狀態優先於聊天摘要。
3. 每次 build 必須帶：
   - engine version
   - project version
   - design profile version
   - source hash
   - build timestamp
   - QA status
4. `latest good build` 與 `latest build` 必須分開記錄。
5. 失敗版本不得覆蓋 last-good 指標。

## B. Authoritative / Generated 分離

不得把 generated INDD 當唯一母稿。

可以手工修特殊版面，但必須：
- 進入 `SPECIAL_LAYOUT` source；
- 或把人工修改回寫成 Project 中可追蹤的 source/config。

禁止「只在某一份 INDD 裡修好但 Project 不知道」。

## C. Editorial Contract

Chicago / MLA / APA 等只處理它們真正負責的層次。

做新書時先辨識：
- 書的類型；
- 讀者；
- 閱讀節奏；
- 註腳在書中的角色；
- 文章之間的關係；
- 是否需要 Part / Collection / Article / Chapter；
- 文學／評論／藝術出版的視覺需求。

不得把「符合 Chicago」等同「應該長得像學位論文」。

## D. Design Contract

1. Design Profile 與 content semantics 分離。
2. 已鎖定 profile 不得因 agent 個人偏好任意重設。
3. 若原型書存在，視覺真相優先級：
   - 經確認 Golden Reference PDF
   - 經確認的實際 InDesign measurement
   - 原始設計規格
   - TeX/CSS/Word 宣告
   - agent 推測
4. 字體 fallback 必須可見、可 QA，不得靜默替換。
5. 不分享字體檔；只保存來源、版本、安裝規格與驗證方式。

## E. InDesign Contract

1. Regression FAIL → **禁止 Full Build**。
2. Full QA FAIL → 可以輸出調查用 PDF/INDD，但不得標記 Release PASS。
3. Article Opening 應儘可能是 story-native structure：
   kicker → title → paragraph rule → first body。
4. 不依賴脆弱的絕對定位文字框去維持會隨 reflow 移動的文章標題結構。
5. Running heads 優先使用 semantic styles / text variables，不寫死字串。
6. PART 是否強制 recto、文章是否 recto、blank 是否保留 folio/header，都由 Project page-class rules 決定，不用全域猜測。

## F. Special Layout Contract

當「空間位置本身就是文本」時，不把它當普通 paragraph flow。

例：
- 具象詩
- 雙聲部
- 圖版
- 劇場空間文字
- ASCII / diagrammatic text
- 特殊 symbol composition

如果來源幾何不可信：
- status = `SOURCE_UNVERIFIED`
- strategy = `PLACEHOLDER`
- 保留所需空間
- 不宣稱 DOCX 幾何就是原作。

## G. Session End Contract

只要本 session 改變了 Project 狀態，結束前必須寫回：
- CURRENT_STATE
- NEXT_ACTION
- CHANGELOG
- QA / manifest（若相關）

真正的 handoff 必須能讓完全失憶的新 agent 接班。

## H. Maintenance Safety Contract

1. 「看起來多餘」不等於「可安全刪除」。
2. 已知正常但依賴不明的 legacy path 標記為 `MACHINE_SPIRIT_RISK`。
3. R2/R3 runtime/environment changes 必須與文件整理分開，且不得在同一版同時做多個未驗證核心更動。
4. 清理 Fonts、cache、舊 installer、舊 script 前，先做 inventory / provenance / rollback plan。
5. 優先用新增 diagnostics 驗證假設，再修改 production behavior。
