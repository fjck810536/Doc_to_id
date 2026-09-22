# QA Protocol

## Gate

```
Static QA
  ↓
Regression
  ↓ PASS
Full Build
  ↓
Full QA
  ↓
Visual QA
  ↓
Release
```

## Static QA

- schema validation
- required files
- checksums
- target application/version
- font declarations
- source file existence
- no unresolved fatal state

## Regression

每個 Design Profile 應有最小代表樣本。

Regression 要測：
- title / front matter
- part
- article opening
- body
- footnote
- blank classes
- running heads
- special layout（成熟後另有 special regression）

## Full QA

至少：
- page count / topology
- page classes
- PART recto rule
- article start rule
- intentional vs accidental blank
- overset
- missing / unexpected active fonts
- Basic Paragraph / unmapped styles
- widow/orphan
- footnote split / density
- table overflow
- special glyphs
- special layouts
- running-head state
- folio
- bleed / trim
- PDF export
- INDD save

## 假陽性警告

不要以「本頁是否有 paragraph start」判斷 blank page。
跨頁長段落會讓有文字的頁面看起來沒有 paragraph start。

判定 blank 應檢查實際 page/text-frame content。

## Geometry QA

要依 page class 驗證，不得把 body / article / part / chapter / blank 全拿同一組 frame geometry 比較。

## Visual QA

自動 PASS 不等於送印。

人工仍需看：
- 字面
- 標點擠壓
- 行尾節奏
- 短尾頁
- 註腳密度
- 圖文關係
- 特殊版面
- 章節起頁節奏
