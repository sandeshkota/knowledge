Query to find pages allocated to a table
```sql
SELECT  OBJECT_NAME(Object_Id) as TableName,
        used_page_count,
        reserved_page_count,
        row_count
FROM sys.dm_db_partition_stats
WHERE OBJECT_NAME(Object_Id) in ('TABLE_1', 'TABLE_2')
      
```
