# Prototype Analysis Protocol

## 目標

把「我喜歡這本原型書」轉成可重現、可 QA 的 Design Profile。

不是目測仿製。

## 證據優先級

1. Golden Reference PDF 實際視覺／測量
2. 已確認的 INDD 實際屬性
3. 設計規格文件
4. 生成來源（TeX/CSS/Word）
5. agent 推測

如果來源程式宣告與 PDF 實際效果不同，以經確認 PDF 為準。

## 分析項

- trim / bleed / facing pages
- margins / text area
- baseline / leading
- CJK / Latin / mono fonts
- optical sizes
- first-line indent
- title hierarchy
- article opening
- part opening
- footnotes
- rules / ornaments
- running head / folio
- intentional blank pages
- recto rules
- editorial colors
- tables
- figures / captions
- special layouts
- fallback glyph policy

## Design Lock

鎖定後：
- 指定版本號；
- 保存 Golden Reference hash；
- 修改任何核心值要升 design profile version；
- 不把「新 agent 覺得更好看」當修改理由。

## 內容與設計分離

DOCX 樣式回答「這是什麼」：
`ID_ArticleTitle`, `ID_Body`, `ID_PartTitle`...

Design Profile 回答「它長什麼樣」。

同一份語意稿可以套不同 profile。
