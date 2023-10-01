
## الاستعلام الحالي 
```sql
select page.page_title as ll_page_title,pagelinks.pl_title as ll_page_to_title,pagelinks.pl_namespace as ll_pl_namespace
from page
         inner join pagelinks
                    on pagelinks.pl_from = page.page_id
where pagelinks.pl_from_namespace = 0
  and (pagelinks.pl_namespace = 2 or pagelinks.pl_namespace = 3)
  and page.page_namespace = 0
  and page.page_is_redirect = 0
  and page.page_id not in (select templatelinks.tl_from  from templatelinks
                                                             join linktarget on linktarget.lt_id = templatelinks.tl_target_id
                      where linktarget.lt_title in (select pl_title from pagelinks where  pl_from = 9043549) and templatelinks.tl_from_namespace = 0  )
  and page.page_title not in (select pl_title from pagelinks where  pl_from = 9043549);

```
## صفحات تستخدم الاستعلام الحالي
 * ويكيبيديا:إحصاءات/مقالات يوجد فيها وصلة إلى صفحات المستخدمين 
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرح

