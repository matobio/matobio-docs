---
sidebar_position: 1
---

# Database size

## SQL Server

```
SELECT
        t.database_id
        ,d.name
        ,recovery_model_desc  
    , log_size = CAST(SUM(CASE WHEN [type] = 1 THEN size END) * 8. / 1024 AS DECIMAL(18,2))
    , data_size = CAST(SUM(CASE WHEN [type] = 0 THEN size END) * 8. / 1024 AS DECIMAL(18,2))
    , total_size = CAST(SUM(size) * 8. / 1024 AS DECIMAL(18,2))
FROM sys.master_files as t
JOIN sys.databases d ON d.database_id = t.database_id
GROUP BY t.database_id,d.name,recovery_model_desc  
order by CAST(SUM(size) * 8. / 1024 AS DECIMAL(18,2)) desc
```