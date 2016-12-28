# find column schema
```sql
SELECT column_name
FROM information_schema.columns
WHERE table_name = 'user_table'
order by ordinal_position
```
