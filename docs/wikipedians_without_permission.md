
## الاستعلام الحالي 
```sql
SELECT actor_name AS user_name, date(user_registration) AS user_registration,
        user_editcount AS total_edits,
       (SELECT COUNT(*) FROM revision WHERE rev_actor = actor_id AND rev_deleted = 0) AS live_edits,
       (SELECT COUNT(*) FROM revision WHERE rev_actor = actor_id AND rev_timestamp > DATE_SUB(NOW(), INTERVAL 1 MONTH)) AS edits_last_month
FROM actor
         join user on actor_user = user_id
         LEFT JOIN ipblocks ON actor_user = ipb_user
         LEFT JOIN user_groups ON actor_user = ug_user
WHERE ipb_user IS NULL AND ug_user IS NULL
HAVING live_edits >= 400
       AND edits_last_month >= 10;

```
## صفحات تستخدم الاستعلام الحالي
 * ويكيبيديا:قائمة الويكيبيديين بلا صلاحيات 

## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرح


