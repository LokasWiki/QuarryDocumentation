
## الاستعلام الحالي 
```sql
SELECT
    DISTINCT page_title,el_index
FROM
    externallinks
        JOIN page ON el_from = page_id
WHERE
        el_index_60 LIKE 'mailto:%'
  AND page_namespace = 0
LIMIT
    1000;

```
## صفحات تستخدم الاستعلام الحالي
 * ويكيبيديا:إحصاءات/مقالات بها وصلات بريد إلكتروني 
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرح
