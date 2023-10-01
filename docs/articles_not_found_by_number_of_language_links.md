
## الاستعلام الحالي 
```sql
SELECT page_title, count(ll_lang) as editcount
FROM langlinks JOIN page on ll_from = page_id
WHERE page_namespace = 0 AND page_is_redirect = 0
AND NOT EXISTS (
    SELECT * FROM langlinks as t
    WHERE t.ll_lang='ar' and t.ll_from = langlinks.ll_from)
GROUP BY ll_from
ORDER BY count(ll_lang) DESC
LIMIT 1000;

```
## صفحات تستخدم الاستعلام الحالي
 * 
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرح
