# Editorial Protocol

## 原則

出版編輯不是「把原稿排漂亮」。

在進入版型前，先確定書的閱讀結構與出版語境。

## Intake 要回答

1. 這是什麼書？
   - 學術專書
   - 評論集
   - 散文集
   - 小說
   - 藝術家書
   - 檔案／劇場書寫
   - 混合形式
2. 預期讀者是誰？
3. 文章之間靠什麼形成一本書？
4. 註腳是純引用、作者的第二聲部、編者說明，還是混合？
5. 原稿有哪些歷史層／修訂層？
6. 哪些差異應被編輯統一？哪些差異應被保留？
7. 哪些內容是 linear text，哪些其實是 spatial object？
8. 前言、後記、致謝、目錄、圖版等 paratext 應放在哪個結構層？

## Chicago baseline

Chicago 可以規範：
- 註腳／尾註
- 引文
- 書目
- 大小寫、標點等 editorial conventions

Chicago **不自動決定**：
- 書頁比例
- 字體
- 文章 opening
- Part / Collection 的視覺階序
- 頁眉
- 具象詩
- 文學書的節奏

因此每個 Project 應另外保存：
- `CHICAGO_POLICY.md`
- `HOUSE_STYLE.md`
- `DESIGN_PROFILE.json`

## 結構層級

通用語意模型：

```
BOOK
  PART
    COLLECTION
      PREFACE (optional)
      ARTICLE
        CHAPTER (optional)
        SECTION
```

不是每本書都要用全部層級。

Collection 適合：
- 同人物的一組文章
- 同議題但不要求理論一致的短輯
- 形式不同但應並置的作品群

不要為了視覺整齊而消滅有意義的不一致。
