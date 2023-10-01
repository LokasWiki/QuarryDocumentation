
## الاستعلام الحالي 
```sql
SELECT  cl_to, COUNT(cl_from) as editcount
  FROM categorylinks
  WHERE cl_from IN (
          SELECT DISTINCT ll_from
          FROM langlinks
          WHERE ll_lang = "ar"
          )
      AND cl_to NOT IN (
          SELECT DISTINCT page_title
          FROM langlinks
          LEFT JOIN page ON page_id = ll_from
          WHERE ll_lang = "ar"
              AND page_namespace = 14
          )
       AND cl_to NOT IN
         (SELECT DISTINCT page_title FROM page
         WHERE page_title LIKE "%rticle%"
           OR  page_title LIKE "%ages%"
           OR  page_title LIKE "%All%"
           OR  page_title LIKE "%using%"
           OR  page_title LIKE "%Good"
           OR  page_title LIKE "%Wikipedia%"
           OR  page_title LIKE "%missing%"
           OR  page_title LIKE "%with%"
           OR  page_title LIKE "%anguage%"
           OR  page_title LIKE "%template%"
           OR  page_title LIKE "%box%"
           OR  page_title LIKE "%stub%"
           OR  page_title LIKE "%Use%"
           OR  page_title LIKE "%dmy%"
           OR  page_title LIKE "%ikidata%"
           OR  page_title LIKE "%CS1%"
           OR  page_title LIKE "%list%"
           OR  page_title LIKE "%image%"
           OR  page_title LIKE "%mdy%"
           OR  page_title LIKE "%TOC%"
           OR  page_title LIKE "%mdy%"
           OR  page_title LIKE "%ategory%"
           OR  page_title LIKE "%edirect%"
           OR  page_title LIKE "%Cite%"
           OR  page_title LIKE "%link%"
           OR  page_title LIKE "%need%"
           OR  page_title LIKE "%Engvar%"
           OR  page_title LIKE "%ommon%"
         )

  GROUP BY cl_to
  ORDER BY COUNT(cl_from) DESC
  LIMIT 500;

```
## صفحات تستخدم الاستعلام الحالي
 * ويكيبيديا:إحصاءات/التصانيف غير الموجودة
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرحf
