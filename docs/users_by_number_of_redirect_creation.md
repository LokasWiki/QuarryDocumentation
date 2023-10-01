
## الاستعلام الحالي 
```sql
SELECT actor_name, COUNT(*) as q_user_editcount
FROM revision r
         INNER JOIN actor ON r.rev_actor = actor.actor_id
         INNER JOIN page p on r.rev_page = p.page_id
WHERE p.page_namespace=0
and p.page_is_redirect=1
and r.rev_parent_id=0
  and ucase(actor_name) not like ucase("%BOT") COLLATE utf8mb4_general_ci
  and actor_name not like "%بوت%" collate utf8mb4_general_ci
  and actor_name Not IN (SELECT user_name
                         FROM user_groups
                                  INNER JOIN user ON user_id = ug_user
                         WHERE ug_group = "bot")
  and actor_id NOT IN ("2579643")
  and actor_user not in (137877)
GROUP BY actor_name
having COUNT(*) > 1
ORDER BY COUNT(*) DESC
LIMIT 500;

```
## صفحات تستخدم الاستعلام الحالي
 * ويكيبيديا:إحصاءات/المستخدمين حسب عدد إنشاء التحويلات 
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرح

