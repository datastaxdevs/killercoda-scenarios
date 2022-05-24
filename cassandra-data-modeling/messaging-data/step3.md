Execute the CQL script to insert sample data:
```sql
SOURCE '~/messaging_data.cql'
```{{execute}}

Retrieve all rows from table `folders_by_user`:
```sql
SELECT * FROM folders_by_user;        
```{{execute}}

Retrieve all rows from table `unread_email_stats`:
```sql
SELECT * FROM unread_email_stats;
```{{execute}}

Retrieve all rows from table `emails_by_user_folder`:
```sql
SELECT * FROM emails_by_user_folder;                    
```{{execute}}

Retrieve all rows from table `emails`:
```sql
SELECT id, "to", "from" FROM emails; 
SELECT id, subject, body FROM emails; 
SELECT id, attachments FROM emails;
```{{execute}}

Retrieve all rows from table `attachments`:
```sql
SELECT * FROM attachments;       
```{{execute}}