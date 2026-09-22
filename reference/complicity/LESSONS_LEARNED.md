# 《共犯者的無終奇語》Reference Implementation Lessons

此處只保存可泛化的工程經驗；本書實際 authoritative source 應存在自己的 Google Drive Book Project。

## 已證明可行的部分

- DOCX 使用 `ID_*` 語意 style 作為 transport layer。
- InDesign 2022 / 17.3.0.61 可用 ExtendScript JSX 建置。
- 18-page Regression 能有效阻止明顯 regression 直接進 Full Build。
- Full Build 能生成 200+ 頁 INDD/PDF；長書才會暴露 reflow／特殊頁校準問題。
- QA 必須區分 truly blocking 與 false positive。

## Prototype01 重要設計鎖

- CJK：Noto Serif CJK TC / Noto Sans CJK TC
- Latin：EB Garamond 12 / EB Garamond 08
- body：9.7 pt / effective ~12.2 pt
- PART recto
- ordinary article next-page, not universally recto
- editorial red ~ #7D3033
- footnote 7.5 / 10.4
- footnote marker gap = thin space
- page-class-specific blank behavior

## 書籍結構經驗

一條文章清單不夠。

實際上需要：
`Part → Collection → Article / Chapter`

例如：
- 「詭譎斷章」適合 Collection
- 「虛構展覽」適合 Collection
- 某人物文章組可形成 Collection
- 某一組專有的「前言」應是 Collection Preface，而不是假裝普通 Article

## 〈鬱足〉

這篇證明 spatial text 必須獨立成 Special Layout。

尤其具象詩的 DOCX 本身是否保留原始幾何並不確定，因此：
- 不把 DOCX 的空格/tab 當原作；
- 先留固定區塊；
- status = SOURCE_UNVERIFIED；
- 找到可靠來源後再製版。

## 這個 reference 的用途

未來 engine 改版時，可以拿這些已知事故作 regression checklist。

不要把這本書的特殊內容硬編進通用 engine。
