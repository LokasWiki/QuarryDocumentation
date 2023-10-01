
## الاستعلام الحالي 
```sql

SELECT
  article.page_title as "q_page_title",
  actor.actor_name as "q_user_name",
  article.page_len as "page_size"
FROM revision
# user
join actor on actor_id = rev_actor
# page
JOIN page article ON  article.page_id = rev_page AND article.page_namespace = 2
# externallinks
JOIN externallinks ON(page_id=el_from)
WHERE rev_parent_id = 0
AND revision.rev_timestamp > DATE_SUB(NOW(),INTERVAL 1 DAY)
AND article.page_title LIKE "%/ملعب%"
GROUP BY article.page_id
ORDER BY MIN(revision.rev_id) DESC;

```
## صفحات تستخدم الاستعلام الحالي
 * ويكيبيديا:ملاعب مستخدمين تحتاج لمراجعة 
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرح


