
## الاستعلام الحالي 
```sql
 SELECT
page_title AS file,
actor_name AS username
FROM page
INNER JOIN revision ON rev_page = page_id
INNER JOIN actor ON actor_id = rev_actor
WHERE
((page_title like "%أ%"
or page_title like "%ض%"
or page_title like "%ص%"
or page_title like "%ث%"
or page_title like "%ق%"
or page_title like "%ف%"
or page_title like "%غ%"
or page_title like "%ع%"
or page_title like "%ه%"
or page_title like "%خ%"
or page_title like "%ح%"
or page_title like "%ج%"
or page_title like "%د%"
or page_title like "%ذ%"
or page_title like "%ش%"
or page_title like "%س%"
or page_title like "%ي%"
or page_title like "%ب%"
or page_title like "%ل%"
or page_title like "%ا%"
or page_title like "%إ%"
or page_title like "%ت%"
or page_title like "%ن%"
or page_title like "%م%"
or page_title like "%ك%"
or page_title like "%ط%"
or page_title like "%ئ%"
or page_title like "%ء%"
or page_title like "%ؤ%"
or page_title like "%ر%"
or page_title like "%ى"
or page_title like "%آ%"
or page_title like "%ة%"
or page_title like "%و%"
or page_title like "%ز%"
or page_title like "%ظ%")
AND (page_title NOT LIKE "%پ%" AND page_title NOT LIKE "%چ%" AND page_title NOT LIKE "%ژ%"
AND page_title NOT LIKE "%ک%" AND page_title NOT LIKE "%گ%" AND page_title NOT LIKE "%ی%" AND page_title NOT LIKE "%ۀ%"))
AND rev_timestamp > NOW() - INTERVAL 1 DAY
AND rev_parent_id = 0
AND page_namespace = 6
LIMIT 500;

```
## صفحات تستخدم الاستعلام الحالي
 * ويكيبيديا:أحدث الملفات العربية على كومنز 
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرح
