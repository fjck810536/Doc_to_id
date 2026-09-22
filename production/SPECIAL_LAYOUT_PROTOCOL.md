# Special Layout Protocol

## 判斷標準

如果文字的 x/y 關係本身承載意義，就不要假裝它只是一般段落。

典型：
- 具象詩
- 左右雙聲部
- 分裂／鏡像文字
- 文字圖
- 舞台位置
- 特殊符號構圖
- 大量依賴 tab / space 的 Word 版面

## 狀態

每個特殊物件至少有：

```
id
source_status
strategy
source_files
known
unknown
frame_policy
notes
```

`source_status`：
- VERIFIED
- PARTIALLY_VERIFIED
- SOURCE_UNVERIFIED

`strategy`：
- NATIVE_IND
- LINKED_INDD
- VECTOR_ASSET
- IMAGE_ASSET
- PLACEHOLDER

## SOURCE_UNVERIFIED

若 DOCX 很可能已破壞原始幾何：
- 不重建假的「精確版」；
- 保留 placeholder；
- 記錄所需版面空間；
- 等可靠原始貼文、PDF、掃描、作者確認後再填。

這不是排版失敗，而是資料來源誠實性。
