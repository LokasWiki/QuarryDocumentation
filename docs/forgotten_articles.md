
## الاستعلام الحالي 
```sql
SELECT DATE_FORMAT(MAX(rev_timestamp),'%Y-%m-%d %H:%i:%s') AS lastedit, COUNT(rev_id) AS editcount, page_title
FROM revision,
     (SELECT rev_timestamp as lastedit, page_id, page_title
      FROM page,
           revision
      WHERE page_title NOT IN (SELECT page_title FROM page WHERE page_title LIKE '%توضيح%')
        AND page_id IN (SELECT page_id FROM page WHERE page_namespace = 0 AND page_is_redirect = 0)
        AND rev_id = page_latest
      ORDER BY lastedit ASC
      LIMIT 1000) as InnerQuery
WHERE rev_page = page_id
  AND lastedit < DATE_FORMAT(DATE_ADD(NOW(), INTERVAL 2 YEAR), '%Y%m%d%H%i%s')
GROUP BY InnerQuery.page_id, InnerQuery.page_title
ORDER BY lastedit ASC, editcount ASC;
```
## صفحات تستخدم الاستعلام الحالي
 * ويكيبيديا:إحصاءات/مقالات منسية
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرح

