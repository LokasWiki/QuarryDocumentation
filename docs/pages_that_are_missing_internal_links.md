
## الاستعلام الحالي 
```sql
SELECT p.page_title as ll_page_title, p.page_len as ll_page_len, a.actor_name as ll_user_name
FROM page p
         LEFT JOIN pagelinks pl ON p.page_id = pl.pl_from
         INNER JOIN revision r ON p.page_id = r.rev_page
         INNER JOIN actor a ON r.rev_actor = a.actor_id
WHERE pl.pl_from IS NULL AND p.page_is_redirect = 0 AND p.page_namespace = 0
  AND r.rev_id = (SELECT MIN(rev_id) FROM revision WHERE rev_page = p.page_id)
```
## صفحات تستخدم الاستعلام الحالي
 * ويكيبيديا:إحصاءات/مقالات بدون وصلات داخلية 
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرح

