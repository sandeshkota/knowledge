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

Creating non-clustered index with a subset
```sql
CREATE NONCLUSTERED INDEX IX_test
        ON dbo.tbl (col1)
        where col2 = 10
        
-- index is used in below query
SELECT * FROM dbo.tbl WHERE col2 = 10 AND <any_other_condition>

-- problem when we are using a parameter, index will not be used as at optimization time value of col2 is not known
-- Plus, its plan is cahced and reused (so it wont be used when col2 = 10 as the plan may be cached when col2 = 5)
DECLARE @col2_value = 10
SELECT * FROM dbo.tbl WHERE col2 = @col2_value AND <any_other_condition>
```

Creating a Covering Index (including columns to read)
```sql
CREATE NONCLUSTERED INDEX IX_Material
        ON dbo.tbl(col1,coll2)
        INCLUDE (col3,col4,col5);
```

Forcing a query to use a certain index
```sql
SELECT * FROM table1 USE INDEX (col1_index,col2_index)
  WHERE col1=1 AND col2=2 AND col3=3;
  
SELECT * FROM t1
   USE INDEX (i1,i2) IGNORE INDEX (i2);

SELECT * FROM t
  USE INDEX (index1)
  IGNORE INDEX (index1) FOR ORDER BY
  IGNORE INDEX (index1) FOR GROUP BY
```

Create materializd view
```sql
CREATE MATERIALIZED VIEW mv_table1_table2 AS
  SELECT col1, col2
    FROM table1, table2
    WHERE table1.id = table2.ref_id
```
