
## الاستعلام الحالي 
```sql
select 
  page.page_id, 
  page.page_title, 
  page.page_namespace, 
  page.page_len, 
  IF(page.page_len < 1000, 'YES', 'NO') as "needed_to_check" 
from 
  categorylinks 
  inner join page on page.page_id = categorylinks.cl_from 
where 
  cl_to like 'إحصاءات_يحدثها_LokasBot' 
  and cl_type like 'page'
  order by page.page_len asc,needed_to_check desc;
  
```
## صفحات تستخدم الاستعلام الحالي
 * مستخدم:LokasBot/صفحات إحصاءات قد تكون معطلة تحتاج للفحص
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرح

