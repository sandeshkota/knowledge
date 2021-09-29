## Indexes
An index is an on-disk structure associated with a table/view that speeds retrieval of rows  
Indexes are special lookup tables that the database search engine can use to speed up data retrieval  

## Creating Indexes

### For New Systems
  - create indexes to support unique requirements
  - create indexes for forieg key columns
  - create indexes to supported common queries
  - be prepared to change indexes later

### For existing systems
  - identify most resource intensive queries
  - identify most important queries
  -  index to support them
  -  re-investigatee regularly

## SQL Server
- Data is stored in 8kb chunks, called pages
- Organized into a key structure (B-tree/Balanced tree)
  
  <img src="../assets/database/index_tree_structure.png" width="500" height="300">
  
- Data logically ordered by the index key

### Index operations in execution plans
- Index seek: Navigation down the tree from the root to find a value (single/ range of rows)
  
  <img src="../assets/database/index_seek.png" width="500" height="300">
  
- Index scan: Read all are some of the leaf pages (rows read = all rows, actula number of rows = which are greater than 250)

  <img src="../assets/database/index_scan.png" width="500" height="300">
  
- Key lookup: Single row seek to the clustered index


## Types of Indexes

### Clustered index
- index which defines the physical storage of the table
- one per table (or none - called as heap table)
- should be unique
- clustered index keys are used as a row address in all the other indexes
- reduce updating the clustered index values (as in that case it has to be deleted from one page and should be created in another page)

### Non-clustered index

### Covering index

### Indexed views

### Columnstore indexes


### Reading Execution Plan
- Number of Rows Read: number of rows the query read (need to read most to check if it is within the quer filters or not)
- Actual number of Rows: number of rows needed (based on the query filters)
- Logical Reads: number of pages read (leaf nodes read)

### Other concepts to explore
- Page Splits: inserting a row which actually should go into a page in b/w and which is full (a new page will be added and the new content along with its continuation row data is added in the new page, and address nodes (intermediate/root) are updated




