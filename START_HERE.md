# START HERE

## 0. 這個 repo 解決什麼

Doc_to_id 將「做一本書」拆成兩個長期穩定的角色：

- **GitHub repo：Publishing System**
- **Google Drive：Book Projects**

聊天只是操作介面，不是資料庫。

## 1. 新 session 的第一步

### 使用者已指定 Book Project
直接讀取並驗證該 Project。

### 使用者未指定 Book Project
只先確認一件事：

> **這次要處理哪一個 Google Drive Book Project？請給我資料夾連結或 Project 名稱。**

不要先猜是哪一本，不要拿過去聊天記憶替代 Project。

## 2. Project Restore 最小讀取集合

依序：

1. `00_PROJECT/PROJECT.json`
2. `00_PROJECT/CURRENT_STATE.md`
3. `00_PROJECT/NEXT_ACTION.md`
4. `02_EDITORIAL/BOOK_STRUCTURE.json`
5. `03_DESIGN/DESIGN_PROFILE.json`
6. `05_QA/` 最新 QA
7. `06_BUILDS/releases/` 最新 `BUILD_MANIFEST.json`（若存在）

若上述任何關鍵檔不存在，不要自行補想像；依 `templates/` 建立或回報缺口。

## 3. 先回答三個問題

恢復狀態後，agent 應該能回答：

1. **我們在做哪一本書？**
2. **最後一個可信版本是哪個？**
3. **這次下一步是什麼？**

三個都能明確回答才開始改檔。

## 4. Source of Truth 層級

同一本書中：

1. **Authoritative Project Source**  
   原始稿、Publication Source、Editorial Structure、Design Profile、Assets、Special Layout sources。
2. **Golden Reference**  
   經確認的原型 PDF／校樣 PDF；可作為視覺真相。
3. **Generated Build**  
   一鍵包、INDD、PDF、QA、logs。全部可重建。
4. **聊天內容**  
   只能作補充脈絡，不能覆蓋 Project 中明確鎖定的設定。

## 5. 最重要的反模式

- 從失憶的新聊天重做設計。
- 看到 TeX/CSS 數字就推翻實際 reference PDF。
- Full Build 壞掉後直接在 INDD 手修。
- 用 Word 的空格／tab 幾何去推定具象詩原貌。
- 字型缺失時偷偷換另一套 CJK family。
- 把所有文章強制 recto。
- 把空白頁一律當錯誤。
- 只用「有沒有 paragraph start」判斷頁面是不是空白。
