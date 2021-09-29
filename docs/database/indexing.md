### Indexes
An index is an on-disk structure associated with a table/view that speeds retrieval of rows  
Indexes are special lookup tables that the database search engine can use to speed up data retrieval  

### Creating Indexes
- Ror New Systems
  - create indexes to support unique requirements
  - create indexes for forieg key columns
  - create indexes to supported common queries
  - be prepared to change indexes later
- For existing systems
  - identify most resource intensive queries
  - identify most important queries
  -  index to support them
  -  re-investigatee regularly

### SQL Server
- Data is stored in 8kb chunks, called pages
- Organized into a key structure (B-tree/Balanced tree)
- Data logically ordered by the index key

### Types of Indexes
- Clustered index
- Non-clustered index
- Covering index
- Indexed views
- Columnstore indexes

