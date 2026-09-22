# Known Failures / Lessons Learned

這些是 reference implementation 已踩過的坑。新 agent 不應重新支付一次成本。

## Adobe / Host

- macOS Finder 雙擊 `.jsx` 可能被 After Effects 接走；launcher 應明確 targeting InDesign。
- InDesign 2022 = v17.x；不要假設可用較新 UXP `.idjs` workflow。
- production target 應精確記版本；reference project 曾使用 17.3.0.61。

## Bash 3.2 / macOS

- `set -u` 下，字串裡意外的 `$var` 也可能爆 unbound variable。
- `local a="$1" b="${a}.x"` 在舊 Bash 的賦值／展開順序容易踩坑，拆行。
- Unicode 標點靠近 shell variable 時要明確用 `${var}`。
- cache ZIP 必須做 integrity check，不能只判斷檔案存在。

## Gate

- UTF-8 BOM 會讓肉眼為 `PASS` 的 status 實際變成 `BOM+PASS`，shell exact match 失敗。
- 狀態檔宜用 ASCII 或在 gate 正規化 BOM/CRLF。

## Fonts

- CJK PostScript 名稱可能導致 TC/JP 誤判；核心 family 要明確 Design Lock。
- 不要為了 QA missing font 直接把來源原稿所有歷史字型都安裝回來；先判斷是否是 active direct-format pollution。
- Symbol / Latin mixed glyph 要有明確 fallback policy。

## Prototype calibration

- 來源 TeX 宣告不一定等於最終 PDF 視覺。例如局部 fontsize scope / paragraph boundary 可能讓有效 leading 不同。
- Golden Reference PDF 的實際結果優先於「程式碼看起來應該是多少」。

## Blank-page QA

- 「沒有 paragraph start」不等於 blank。
- 跨頁段落會造成 blank false positive。

## Reflow geometry

- 文章起頁在全文 reflow 後會改變；只校準一次特殊頁 frame，會留下上一輪 article geometry，造成連鎖 drift。
- 可重排的 article opening 應盡量 story-native。

## Word semantics

- `ID_Spacer` 等臨時樣式若仍 active，可能造成意外空間／頁面。
- break normalization 要區分真正結構 break 與 Word 遺留 break。
- 不要把 DOCX 的空格/tab 當可靠的特殊版面幾何。

## Special layout

- 具象詩的 DOCX 可能本身就是轉檔後的殘骸。
- 來源未確認時最安全策略是留 placeholder，而不是「精密還原一個未知的錯誤版本」。

## Regression slicing vs synthetic paragraphs

- Regression slice 必須在 source paragraph semantics 映射後、synthetic layout paragraph（例如 article kicker、special-layout placeholder）注入前完成；或 slicer 必須明確理解這些 synthetic siblings。
- 已知事故：先插入第 4 篇的 `P_ArticleKicker`、再從第 4 個 `P_ArticleTitle` 截斷，會留下帶 `NEXT_PAGE` 的孤立 kicker，讓 18 頁 Golden Regression 變成 19 頁。
- 不應為這類 generator bug 修改 Golden Regression 的預期頁數；應修 pipeline order。
