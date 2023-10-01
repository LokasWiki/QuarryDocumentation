
## الاستعلام الحالي 
```sql
SELECT
    afl_filter_id,
    SUM(CASE WHEN DATE(afl_timestamp) = CURDATE() - INTERVAL 6 DAY THEN 1 ELSE 0 END) AS hit_in_day_1,
    SUM(CASE WHEN DATE(afl_timestamp) = CURDATE() - INTERVAL 5 DAY THEN 1 ELSE 0 END) AS hit_in_day_2,
    SUM(CASE WHEN DATE(afl_timestamp) = CURDATE() - INTERVAL 4 DAY THEN 1 ELSE 0 END) AS hit_in_day_3,
    SUM(CASE WHEN DATE(afl_timestamp) = CURDATE() - INTERVAL 3 DAY THEN 1 ELSE 0 END) AS hit_in_day_4,
    SUM(CASE WHEN DATE(afl_timestamp) = CURDATE() - INTERVAL 2 DAY THEN 1 ELSE 0 END) AS hit_in_day_5,
    SUM(CASE WHEN DATE(afl_timestamp) = CURDATE() - INTERVAL 1 DAY THEN 1 ELSE 0 END) AS hit_in_day_6,
    SUM(CASE WHEN DATE(afl_timestamp) = CURDATE() THEN 1 ELSE 0 END) AS hit_in_day_7,
    abuse_filter.af_public_comments,
    abuse_filter.af_hidden
FROM
    abuse_filter_log 
INNER JOIN
    abuse_filter ON abuse_filter.af_id = abuse_filter_log.afl_filter_id
WHERE
    afl_timestamp >= NOW() - INTERVAL 1 WEEK
    AND abuse_filter.af_enabled = 1
    AND abuse_filter.af_deleted = 0
GROUP BY
    afl_filter_id, abuse_filter.af_public_comments
ORDER BY
    afl_filter_id;
```
## صفحات تستخدم الاستعلام الحالي
 * مستخدم:LokasBot/ضربات المرشحات في آخر أسبوع
 
## شرح الاستعلام الحالي
## ملاحظات علي التسشغيل
## امثله اخر متقدمه مع الشرحf
