Create the `music_data` keyspace:
```sql
cqlsh -e "

CREATE KEYSPACE music_data
WITH replication = {
  'class': 'NetworkTopologyStrategy', 
  'DC-Houston': 1 };"
```{{execute}}
