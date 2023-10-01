
## الاستعلام الحالي 
```sql

select page_title, count(ll_lang) as editcount  from langlinks
inner join page on page.page_id = langlinks.ll_from
where page.page_namespace = 10
AND NOT EXISTS (
    SELECT * FROM langlinks as t
    WHERE t.ll_lang='ar' and t.ll_from = langlinks.ll_from
)    
GROUP BY ll_from
ORDER BY count(ll_lang) DESC
LIMIT 1000;

```
## صفحات تستخدم الاستعلام الحالي
 * 
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرح