
## الاستعلام الحالي 
```sql
SELECT user_name, user_editcount
FROM user
WHERE
  ucase(user_name) not like ucase("%BOT") collate utf8mb4_general_ci
  and
  user_name not like "%بوت%" collate utf8mb4_general_ci
  and
  user_name NOT IN (SELECT user_name
                        FROM user_groups
                                 INNER JOIN user ON user_id = ug_user
                        WHERE ug_group = "bot")
                        and user_id not in (137877)
ORDER BY user_editcount DESC
LIMIT 500;

```
## صفحات تستخدم الاستعلام الحالي
 * ويكيبيديا:قائمة الويكيبيديين حسب عدد التعديلات 
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرح

