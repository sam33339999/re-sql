
## member
| seq   | name  | uid   | displayname   | gender    | phone |
|:----- |:----- |:----- |:------------- |:---------:|:----- |
| 1     | SamZ  | U1235 | SamCheng      | male      | 09111 |
| 2     | JeffS | U1236 | JeffSam       | male      | 09112 |
| 3     | IvyC  | U1237 | IvyCheng      | female    | 09113 |


## tags
| seq   | tag_name  | created_at    | updated_at    |
|:----- |:--------- |:-------------:|:-------------:|
|     1 | VIP | 2022-06-26 00:00:00 | 2022-06-26 00:00:00 |
|     2 | 有購買衝動行為 | 2022-06-26 00:00:00 | 2022-06-26 00:00:00 |
|     3 | 時常購買3C產品 | 2022-06-26 00:00:00 | 2022-06-26 00:00:00 |
|     4 | 時常買飲料的人 | 2022-06-26 00:00:00 | 2022-06-26 00:00:00 |

## member_tag
| seq | uid | tag_seq | created_at | updated_at |
|-----|-----|---------|------------|------------|
|1|U1235|1|2022-06-26 00:00:00|2022-06-26 00:00:00|
|2|U1235|2|2022-06-26 00:00:00|2022-06-26 00:00:00|
|3|U1236|2|2022-06-26 00:00:00|2022-06-26 00:00:00|
|4|U1235|3|2022-06-26 00:00:00|2022-06-26 00:00:00|
|5|U1237|2|2022-06-26 00:00:00|2022-06-26 00:00:00|

### question1
請找出 uid 是 'U1235' 的名字？

### question2
請找出 displayname 含有 'Cheng' 的人員找出來？

### question3
請找出 displayname 含有 'Cheng' 的人員且性別為男性'male'？

### question4
請排列出 誰有哪些標籤 的表請列出來


```sql
CREATE TABLE `member`(
	`seq` INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY COMMENT '自增值',
	`name` VARCHAR(50) COMMENT '姓名',
	`uid` VARCHAR(50) COMMENT 'uid',
	`displayname` VARCHAR(50) COMMENT '顯示姓名',
	`gender` ENUM('male', 'female') COMMENT '性別',
	`phone` VARCHAR(20) COMMENT '手機號碼'
);

INSERT INTO `member`(`name`, `uid`, `displayname`, `gender`, `phone`) VALUES ('SamZ', 'U1235', 'SamCheng', 'male', '09111');
INSERT INTO `member`(`name`, `uid`, `displayname`, `gender`, `phone`) VALUES ('JeffS', 'U1236', 'JeffSam', 'male', '09112');
INSERT INTO `member`(`name`, `uid`, `displayname`, `gender`, `phone`) VALUES ('IvyC', 'U1237', 'IvyCheng', 'female', '09113');


CREATE TABLE `tags`(
    `seq` INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY COMMENT '自增值',
    `tag_name` VARCHAR(50) COMMENT '姓名',
    `created_at` DATETIME DEFAULT CURRENT_TIMESTAMP COMMENT '建立時間',
    `updated_at` DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '更新時間'
);

INSERT INTO `tags`(`tag_name`) VALUES ('VIP'), ('有購買衝動行為'), ('時常購買3C產品'), ('時常買飲料的人');


CREATE TABLE `member_tag`(
    `seq` INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY COMMENT '自增值',
    `uid` VARCHAR(50) NOT NULL COMMENT 'member 的 uid',
    `tag_seq` INT UNSIGNED NOT NULL COMMENT 'tag 的 seq',
    `created_at` DATETIME DEFAULT CURRENT_TIMESTAMP COMMENT '建立時間',
    `updated_at` DATETIME DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP COMMENT '更新時間'
)

INSERT INTO `member_tag`(`uid`, `tag_seq`) VALUES ('U1235', '1'), ('U1235', '2'), ('U1236', '2'), ('U1235', '3'), ('U1237', '2');
```