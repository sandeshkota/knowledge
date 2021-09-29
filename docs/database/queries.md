Query to find pages allocated to a table
```sql
SELECT  OBJECT_NAME(Object_Id) as TableName,
        used_page_count,
        reserved_page_count,
        row_count
FROM sys.dm_db_partition_stats
WHERE OBJECT_NAME(Object_Id) in ('TABLE_1', 'TABLE_2')
      
```

ON & WHERE in SQL Queries
- same for inner joins but different for left joins

```sql
SELECT *
FROM Orders
LEFT JOIN OrderLines ON OrderLines.OrderID=Orders.ID
WHERE Orders.ID = 12345
-- returns only rows whose Orders.Id = 12345


SELECT *
FROM Orders
LEFT JOIN OrderLines ON OrderLines.OrderID=Orders.ID 
    AND Orders.ID = 12345
-- returns all rows of Orders by filling the data for OrderLines where Orders.Id = 12345
```
