Create the `order_management_data` keyspace:
```sql
CREATE KEYSPACE order_management_data
WITH replication = {
  'class': 'NetworkTopologyStrategy', 
  'DC-Houston': 1 };
```{{execute}}

Set the current working keyspace:
```sql
USE order_management_data;
```{{execute}}
