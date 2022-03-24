### Get the sizes of all databases on a Maria server, sorting by size

```sql
SELECT table_schema, ROUND(SUM(data_length + index_length) / 1024 / 1024, 1) "Db-size-in-MiB"  FROM information_schema.tables
GROUP BY table_schema
ORDER BY 'Db-size-in-MiB' asc;
```

### Get the size of a single Maria database

```sql
SELECT table_schema, ROUND(SUM(data_length + index_length) / 1024 / 1024, 1) "Db-size-in-MiB"  FROM information_schema.tables
WHERE table_schema LIKE 'database-name-here' 
GROUP BY table_schema;
```
