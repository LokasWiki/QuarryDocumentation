
## الاستعلام الحالي 
```sql
SELECT
  actor_name AS name,
  count(logging.log_id) as score
FROM logging
INNER JOIN actor ON log_actor = actor.actor_id
and log_type = "review" and  log_action in ('approve','approve-ia','approve-a','approve2-i','approve-i','approve2','unapprove','unapprove2')
#and log_namespace = 0
and ucase(actor_name) not like ucase("%BOT") COLLATE utf8mb4_general_ci
  and actor_name not like "%بوت%" collate utf8mb4_general_ci
  and actor_name Not IN (SELECT user_name
                         FROM user_groups
                                  INNER JOIN user ON user_id = ug_user
                         WHERE ug_group = "bot")
  and actor_id NOT IN ("2579643")
  and actor_user not in (137877)

GROUP BY actor_name
ORDER BY score desc,actor_name
limit 100
```
## صفحات تستخدم الاستعلام الحالي
 * ويكيبيديا:قائمة الويكيبيديين حسب عدد مراجعة التعديلات 
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرح

