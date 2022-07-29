# 編碼差異 MySQL
[引用](https://khiav223577.github.io/blog/2019/06/30/MySQL-%E7%B7%A8%E7%A2%BC%E6%8C%91%E9%81%B8%E8%88%87%E5%B7%AE%E7%95%B0%E6%AF%94%E8%BC%83/)

> `utf8_bin`, `utf8_unicode_ci`, `utf8_general_ci`

先說結論:

- 若只存 英文數字 可以用 `utf8_general_ci` (不推薦使用)
- 若會出現 中文、德文等等非英文的字，emoji 建議使用 `utf8mb4_unicode_ci`


## utf8mb4 vs utf8 vs utf8mb3
MySQL 5.5.3 以後，一般建議用 utf8mb4，因為他才是真正得 utf8 編碼；且完全兼容 utf8

- utf8 只有用 3個字元長度的字
- utf8mb4 使用 4個字元長度的字
- utf8mb3 就是怕 utf8 容易混淆，後續被改成的名稱
mb4 mb3 就是儲存時使用的位元組。

---

## ci vs cs vs bin
- ci case-insensitive 大小寫不敏感
- cs case-sensitive 大小寫敏感
- bin binary value 比較，例如 utf8mb4_bin 會區分大小寫且會區分 `Ä` 和 `A` 的不同

## general vs unicode 


