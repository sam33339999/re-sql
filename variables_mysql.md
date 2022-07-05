# veriable MYSQL
> 變數，操作 `MySQL`

- [mysql-store-strings-in-variables-and-concatenate-them-to-return-them-to-the-term](https://stackoverflow.com/questions/20721261/mysql-store-strings-in-variables-and-concatenate-them-to-return-them-to-the-term)

```sql
SET @fname = "sam.zheng";

SELECT * FROM member WHERE displayname = @fname;
```

> 但是或許你的需求是 ... , 0912345678 + sam.zheng ... 
就是說是有 電話號碼加上姓名的需求的話 ...


```sql
SET @namefill = CONCAT("0912345678", "sam.zheng");

-- 在這裡的時候 @namefill 會等於 0912345678sam.zheng

SELECT * FROM member WHERE somefield = @namefill;
```

> 在或許，你會需要這種需求 會員id + phone + gender 然後用特定符號做分隔(例如 `;`)的話 ...

```sql
SET @id = "1";
SET @phone = "0912345678";
SET @gender = "male";

-- CONCAT_WS(“分隔符號”, args...);
SET @field_content = CONCAT_WS(";", @id, $phone, @gender);

SELECT * FROM member WHERE multi_content = @field_content;
```