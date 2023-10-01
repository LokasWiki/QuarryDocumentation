
## الاستعلام الحالي 
```sql
SELECT main.page_title as portal_name, COUNT(*) - 1 as sub_page_count,
    (SELECT COUNT(*) FROM pagelinks WHERE pl_title = main.page_title and pl_from_namespace = 0 and pl_namespace = 100) as links_count
FROM page AS p
INNER JOIN (
    SELECT page_title
    FROM page
    WHERE page_namespace = 100
    AND page_is_redirect = 0
)AS main ON main.page_title = SUBSTRING_INDEX(p.page_title, '/', 1)
WHERE p.page_namespace = 100
GROUP BY portal_name
ORDER BY links_count DESC;

```
## صفحات تستخدم الاستعلام الحالي
 * ويكيبيديا:إحصاءات/قائمة البوابات حسب عدد المقالات 
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرح
