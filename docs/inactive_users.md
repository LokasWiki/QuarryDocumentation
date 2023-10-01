
## الاستعلام الحالي 
```sql
SELECT 
  DISTINCT(actor_name) as ll_actor_name, 
  concat(ug_group) AS user_groups, 
  (
    SELECT 
      MAX(rev_timestamp) 
    FROM 
      revision_userindex 
    WHERE 
      rev_actor = actor_id
  ) AS last_edit_date 
FROM 
  actor_revision 
  JOIN user_groups ON actor_user = ug_user 
  JOIN user ON actor_user = user.user_id 
  LEFT JOIN ipblocks ON actor_user = ipb_user 
WHERE 
  ug_group IN (
    'editor', 'autoreview', 'uploader'
  ) 
  AND ipb_user IS NULL 
  AND actor_id NOT IN (
    SELECT 
      DISTINCT rev_actor 
    FROM 
      revision_userindex 
    WHERE 
      rev_timestamp > DATE_SUB(NOW(), INTERVAL 1 YEAR)
  ) 
GROUP BY 
  actor_name, 
  user_groups;

```
## صفحات تستخدم الاستعلام الحالي
 *ويكيبيديا:إحصاءات/المستخدمين غير النشطين 
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرح
