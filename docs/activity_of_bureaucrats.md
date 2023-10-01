
## الاستعلام الحالي 
```sql
select user_name,
				  (select count(*) from logging
                    inner join actor on actor_id = log_actor
                    where actor_user = user_id and log_type = "rights" and
                    log_params like '%5::newgroups%"bot"%'
                    and log_params not like '%::oldgroups"%"sysop"%5::newgroups%'
                    and log_params not like '%::oldgroups"%"bot"%5::newgroups%') as "+بوت",

                  (select count(*) from logging
                   inner join actor on actor_id = log_actor
                   where actor_user = user_id and log_type = "rights" and
                  log_params like '%5::newgroups%"sysop"%'
                  and log_params not like '%::oldgroups"%"sysop"%5::newgroups%') as "+إداري",

                  (select count(*) from logging
                   inner join actor on actor_id = log_actor
                   where actor_user = user_id and log_type = "rights"  and
                  log_params like '%5::newgroups%"bureaucrat"%'
                  and log_params not like '%::oldgroups"%"bureaucrat"%5::newgroups%') as "+بيروقراط",

                  (select count(*) from logging
                   inner join actor on actor_id = log_actor
                   where actor_user = user_id and log_type = "rights"  and
                  log_params like '%5::newgroups%"accountcreator"%'
                  and log_params not like '%::oldgroups"%"accountcreator"%5::newgroups%') as "+منشئ حسابات",

                  (select count(*) from logging
                   inner join actor on actor_id = log_actor
                   where actor_user = user_id and log_type = "rights"  and
                  log_params like '%5::newgroups%"import"%'
                  and log_params not like '%::oldgroups"%"import"%5::newgroups%') as "+مستورد",

                  (select count(*) from logging
                   inner join actor on actor_id = log_actor
                   where actor_user = user_id and log_type = "rights"  and
                  log_params like '%::oldgroups"%"import"%5::newgroups%'
                  and log_params not like '%5::newgroups%"import"%' ) as "-مستورد",

                  (select count(*) from logging
                   inner join actor on actor_id = log_actor
                   where actor_user = user_id and log_type = "rights"  and
                  log_params like '%::oldgroups"%"accountcreator"%5::newgroups%'
                  and log_params not like '%5::newgroups%"accountcreator"%') as "-منشئ حسابات",

                  (select count(*) from logging
                   inner join actor on actor_id = log_actor
                   where actor_user = user_id and log_type = "rights"  and
                  log_params like '%::oldgroups"%"bot"%5::newgroups%'
                  and log_params not like '%::oldgroups"%"sysop"%5::newgroups%'
                  and log_params not like '%5::newgroups%"bot"%') as "-بوت",

                  (select count(*) from revision
                   inner join actor on actor_id = rev_actor
                   where actor_user = user_id and rev_page = 213729 and
                  rev_minor_edit = 0) as "وب:طصب"
from user
inner join user_groups
on ug_user = user_id
where ug_group = "bureaucrat";

```
## صفحات تستخدم الاستعلام الحالي
 * ويكيبيديا:إحصاءات/نشاط البيروقراطيين 
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرح
 


