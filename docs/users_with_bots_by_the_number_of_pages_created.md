
## الاستعلام الحالي 
```sql
SELECT u.user_name as user_name,
       (
           SELECT MIN(rev_timestamp)
           FROM revision
           WHERE rev_actor = a.actor_id
       ) AS first_edit_date,
       (
           SELECT COUNT(*)
           FROM revision
                    INNER JOIN actor ON rev_actor = actor.actor_id
                    INNER JOIN page  on rev_page = page.page_id
           WHERE page_namespace = 0
             AND page_is_redirect = 0
             AND rev_parent_id = 0
             AND rev_actor = a.actor_id
       ) AS pages_created,
       (
            select COUNT(*)
            FROM revision
                     INNER JOIN actor ON rev_actor = actor.actor_id
                     INNER JOIN page p on rev_page = page_id
            WHERE page_namespace = 10
              and page_is_redirect = 0
              and rev_parent_id = 0
              AND rev_actor = a.actor_id
       ) AS template_created,
       (
            select COUNT(*)
            FROM revision
                     INNER JOIN actor ON rev_actor = actor.actor_id
                     INNER JOIN page p on rev_page = page_id
            WHERE page_namespace = 12
              and page_is_redirect = 0
              and rev_parent_id = 0
              AND rev_actor = a.actor_id
       ) AS help_created,
       (
            select COUNT(*)
            FROM revision
                     INNER JOIN actor ON rev_actor = actor.actor_id
                     INNER JOIN page p on rev_page = page_id
            WHERE page_namespace = 14
              and page_is_redirect = 0
              and rev_parent_id = 0
              AND rev_actor = a.actor_id
       ) AS category_created,
       (
            select COUNT(*)
            FROM revision
                     INNER JOIN actor ON rev_actor = actor.actor_id
                     INNER JOIN page p on rev_page = page_id
            WHERE page_namespace = 100
              and page_is_redirect = 0
              and rev_parent_id = 0
              and page_title not like "%/%"
              AND rev_actor = a.actor_id
       ) AS portals_created,
       (
            select COUNT(*)
            FROM revision
                     INNER JOIN actor ON rev_actor = actor.actor_id
                     INNER JOIN page p on rev_page = page_id
            WHERE page_namespace=0
              and page_is_redirect=1
              and rev_parent_id=0
              AND rev_actor = a.actor_id
       ) AS redirect_created,
      (
           select COUNT(*)
           FROM revision
                    INNER JOIN actor ON rev_actor = actor.actor_id
                    INNER JOIN page p on rev_page = page_id
           WHERE page_namespace = 1
             and page_is_redirect = 0
             and rev_parent_id = 0
             AND rev_actor = a.actor_id
       ) AS take_page_created

FROM user u
         JOIN actor a ON a.actor_user = u.user_id
        where actor_user not in (137877)
ORDER BY pages_created DESC
LIMIT 500;

```
## صفحات تستخدم الاستعلام الحالي
 * ويكيبيديا:إحصاءات/المستخدمين حسب عدد إنشاء الصفحات (متضمنة البوتات) 
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرح


