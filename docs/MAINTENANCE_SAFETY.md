# Maintenance Safety / 「驚擾機魂」Protocol

## 目的

這份規則處理一種很常見的出版工程風險：

> 某段舊腳本、舊資料夾、舊字體快取、重複檔案看起來很髒，但目前整條 production path 其實仍在工作。
> 沒有證據就清理，可能把隱性依賴一起刪掉。

本專案把這種情況用兩個口語壓縮詞描述：

- **屎山代碼（LEGACY_DEBT）**：歷史上累積、可疑、重複、耦合不明，但可能仍在承擔功能的程式／資料。
- **驚擾機魂（MACHINE_SPIRIT_RISK）**：在沒有 dependency proof / regression coverage 的情況下，修改或刪除「看起來多餘」的東西，導致已知正常行為退化的風險。

這不是禁止整理，而是要求 **先證明，再整理**。

## Change Risk Levels

### R0 — Documentation only
例：incident note、README、QA explanation、handoff state。
預設可直接做，不應改 runtime 行為。

### R1 — Additive metadata / schema-compatible
例：新增 manifest 欄位但舊 reader 可忽略、新增 QA diagnostics。
要求：不改現有 build path；可回滾。

### R2 — Build behavior change
例：paragraph mapping、page-class 判斷、font normalization、regression slicing、running-head generation。
要求：先寫 incident / hypothesis；最小變更；Regression PASS；再進 Full Build。

### R3 — Environment / destructive cleanup
例：刪 Fonts 目錄、移除舊 installer cache、改 InDesign runtime、改核心字體 family、大規模重構 launcher / JSX。
要求：先確認 active dependency；先備份／可回滾；不和其他 R2/R3 變更綁在同一版；必須有明確驗證步驟。

## Machine Spirit Checklist

在刪除／搬動／重構前，先回答：

1. **它現在真的沒被用嗎？**
2. **我們知道 InDesign / shell / font manager 真正讀哪一份嗎？**
3. **有沒有 last-good build 依賴它？**
4. **如果刪了，Regression 能覆蓋這個依賴嗎？**
5. **能不能只加 diagnostics，不先改行為？**
6. **能不能把 cleanup 拆成獨立版本？**
7. **失敗時能一鍵回滾嗎？**

其中 1–4 任一答案不確定，先標 `MACHINE_SPIRIT_RISK`，不要清。

## 「對抗」repo 的方式

不是隨機重構，而是用已發生事故反推測試：

- 讓新 agent 在完全失憶狀態 restore Project。
- 模擬缺少／重複／巢狀 font 目錄。
- 模擬舊 installer 留下歷史版本資料夾。
- Regression PASS 但 Full QA FAIL。
- synthetic paragraph 在 regression slicing 前後出現。
- status file 帶 BOM / CRLF。
- cache ZIP 存在但毀損。
- InDesign active font 與磁碟檔名／family 名稱不一致。

每個事故都應轉成：**Observed → Hypothesis → Minimal Fix → Regression → Full QA → Lesson**。

## Cleanup 原則

**不要把「整潔」放在「可重現」前面。**

可疑歷史物件先 inventory、hash、ownership 標記、active-use 檢查，最後才 delete。
