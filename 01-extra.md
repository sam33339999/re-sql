# MYSQL - extra

## WHERE `{field}` IN (...) 查找多筆結果時
```sql
SELECT * FROM tags WHERE seq IN (1,2,3,4,5);
```

## LIKE 查詢某...的字串
> (1)比如說我要查我自己 `亞欣(Sam)` 但是實際查找時，我懶得打這麼多；
或是說(2)我要查姓 `鄭` 的會員有幾個 ?

```sql
- question1
SELECT * FROM `member` WHERE `displayname` LIKE '%Sam%';
SELECT * FROM `member` WHERE `displayname` LIKE '亞欣%';
- question2
SELECT COUNT(*) FROM member WHERE `name` LIKE '鄭%';
```

---

## 基本簡介 介紹
- SELECT
- FROM
- WHERE 
- JOIN

### `SELECT` 是查找表中的哪些欄位去做顯示， `*` 代表全部撈出來，有什麼欄位就撈什麼欄位
> 比如說 `member` 裡面有 `seq`, `name`, `displayname`, `uid`, `gender`, `phone`

```sql
- 把所有欄位全部撈出來
SELECT * FROM `member` WHERE `name` LIKE '亞欣%';

- 所以你也可以只要查找這個人的 uid 的話
SELECT uid FROM `member` WHERE `name` LIKE '亞欣%';
```
---

### `FROM` 資料從哪裡來 ?
> 像是剛剛有說明，member 表中的資料，所以資料從 member 這邊來

```sql
SELECT * FROM member;
```
---

### `WHERE` 是去把撈出來的資料去做過濾，有 `AND`, `OR`, `>`, `=`, `<` 等等的

```sql
SELECT * FROM `member` WHERE `seq` = 1;

SELECT * FROM `member` WHERE `gender` = 'male' AND `name` LIKE '鄭%';
```
---

### JOIN 將兩表 或是 多表把資料關聯起來
> JOIN {表} ON {條件}

```sql
- JOIN 一張表
SELECT m.*, mt.* FROM `member` m
LEFT JOIN `member_tag` mt ON m.uid = mt.uid
WHERE m.name LIKE '亞欣%';

- JOIN 多張表 ...
SELECT m.*, mt.*, t.* FROM `member` m
LEFT JOIN `member_tag` mt ON m.uid = mt.uid
LEFT JOIN `tags` t ON mt.tag_seq = t.seq
WHERE m.name LIKE '亞欣%';
```








