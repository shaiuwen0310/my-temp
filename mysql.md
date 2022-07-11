# 快速閱覽基本常識的記錄

## sql
```sql
# 顯示的 JobTitle 欄位不重複
SELECT DISTINCT (JobTitle) FROM HumanResources.Employee
# 數不重複的click_hit有幾個
SELECT COUNT( DISTINCT click_hit ) as c_h FROM go_blog.blog;

# 跟`grep *123`雷同，效能問題
# 反之 not like
SELECT * FROM go_blog.blog WHERE summary LIKE '第%';

# 條件是 click_hit 在5~50之間，這兩句一樣
SELECT * FROM go_blog.blog WHERE click_hit BETWEEN 5 and 50
SELECT * FROM go_blog.blog WHERE click_hit >= 5 AND click_hit <= 50
# 條件為 click_hit 等於1或6或8，且typeId大於等於1
SELECT * FROM go_blog.blog WHERE click_hit IN (1,6,8) AND typeId >= 1

# table平行合併
# 挑出id相同的行，兩表完全合併在一起
SELECT * FROM go_blog.blog, go_blog.comment WHERE go_blog.blog.id = go_blog.comment.blog_id
# join on 合併，且用 alias 簡化 table 名稱
SELECT go_blog.blog.title, go_blog.blog.summary, go_blog.comment.content FROM go_blog.blog JOIN go_blog.comment ON go_blog.blog.id = go_blog.comment.blog_id
SELECT b.title, b.summary, c.content FROM go_blog.blog as b JOIN go_blog.comment as c ON b.id = c.blog_id

# 表A LEFT JOIN 表B ON 條件
# 以左邊的表作為合併，反之則right join on
SELECT b.id, b.title, b.summary, bt.name FROM go_blog.blog b LEFT JOIN go_blog.blog_type bt ON b.typeId = bt.id;

# 垂直合併
# 兩個一樣欄位的表合併
SELECT * FROM go_blog.blog_type UNION ALL SELECT * FROM go_blog.blog_type_2

# group by
# 依照`blog_type`.name分組
select `blog`.typeId, count(`blog`.typeId) as b_count, `blog_type`.name as b_name from blog left join `blog_type` on `blog`.typeId = `blog_type`.id group by `blog_type`.name







```

# 鍵值 (Key Value)
* 超鍵(Super key): 有多個，可縮減，最小一欄位，最大全部
* 候選鍵(Candidate Key): 有多個選擇，不可縮減
* 主鍵(Primary Key): 從多個候選鍵中選出其一
* 替代鍵(Alternate Key): 各候選鍵中，除了主鍵之外的其他候選鍵
* 外來鍵(Foreign Key): 與其他表一樣的欄位，用虛線連線，可能有多個，不具唯一性
* 





