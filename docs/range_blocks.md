
## الاستعلام الحالي 
```sql
SELECT
  ipb_address,
  ipb_range_start,
  ipb_range_end,
  actor_name,
  ipb_timestamp,
  ipb_expiry,
  comment_text
FROM ipblocks
inner join actor on actor.actor_id = ipblocks.ipb_by_actor
inner join comment on comment.comment_id = ipblocks.ipb_reason_id
WHERE ipb_address LIKE '%/%';

```
## صفحات تستخدم الاستعلام الحالي
 * ويكيبيديا:إحصاءات/نطاقات الأيبيهات الممنوعة
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرح

