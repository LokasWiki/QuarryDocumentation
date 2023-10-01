
## الاستعلام الحالي 
```sql
SELECT user_name,

           (select count(*) from logging
                    inner join actor on actor_id = log_actor
                    where actor_user = user_id and log_type = "delete"  and log_action not in ("delete_redir","restore") ) as "delete_count",
           (select count(*) from logging
                    inner join actor on actor_id = log_actor
                    where actor_user = user_id and log_type = "delete" and log_action = "restore" ) as "restore_count",

           (select count(*) from logging
                    inner join actor on actor_id = log_actor
                    where actor_user = user_id and log_type = "delete" and log_action = "revision" ) as "revision_count",
           (select count(*) from logging
                    inner join actor on actor_id = log_actor
                    where actor_user = user_id and log_type = "delete" and log_action = "event"  ) as "event_count",
           (select count(*) from logging
                    inner join actor on actor_id = log_actor
                    where actor_user = user_id and log_type = "protect" and log_action in("modify","protect")) as "protect_count",
       (select count(*) from logging
                                 inner join actor on actor_id = log_actor
        where actor_user = user_id and log_type = "protect" and log_action = "unprotect") as "unprotect_count",
       (select count(*) from logging
                                 inner join actor on actor_id = log_actor
        where actor_user = user_id and log_type = "protect" and log_action = "modify") as "modify_count",
       (select count(*) from logging
                                 inner join actor on actor_id = log_actor
        where actor_user = user_id and log_type = "block" ) as "block_count",
       (select count(*) from logging
                                 inner join actor on actor_id = log_actor
        where actor_user = user_id and log_type = "block" and log_action = "unblock") as "unblock_count",
       (select count(*) from logging
                                 inner join actor on actor_id = log_actor
        where actor_user = user_id and log_type = "block" and log_action = "reblock") as "reblock_count",
       (select count(*) from logging
                                 inner join actor on actor_id = log_actor
        where actor_user = user_id and log_type = "rights" ) as "rights_count"
FROM user
         JOIN user_groups ON user_id = ug_user
WHERE ug_group = "sysop" and user_name not in ("مرشح الإساءة")
ORDER BY user_name ASC , delete_count DESC, restore_count DESC, revision_count DESC, event_count DESC, protect_count DESC, unprotect_count DESC, modify_count DESC, block_count DESC, unblock_count DESC, reblock_count DESC, rights_count DESC;

```
## صفحات تستخدم الاستعلام الحالي
 * ويكيبيديا:إحصاءات/نشاط الإداريين 
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرح
