
## الاستعلام الحالي 
```sql
SELECT
  article.page_title,
  article.page_namespace,
  count(distinct actor.actor_name) as "bot_users",
  GROUP_CONCAT(DISTINCT actor.actor_name)  as "bot_users_named",
  TIMESTAMP(max(rev_timestamp))  as "last_edit_on_page",
  COUNT(*) AS edits
FROM revision
INNER JOIN page article ON  article.page_id = rev_page  #AND article.page_namespace = 0
INNER JOIN  actor ON actor_id = rev_actor
WHERE 
	rev_timestamp > DATE_SUB(NOW(), INTERVAL 2 day)
            AND actor_name IN (SELECT user_name FROM user_groups INNER JOIN user ON user_id = ug_user WHERE ug_group = 'bot')
GROUP BY article.page_id
having count(*) > 10
ORDER BY edits DESC;
  
```
## صفحات تستخدم الاستعلام الحالي
 * مستخدم:LokasBot/حروب البوت 
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرح

