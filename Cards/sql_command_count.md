up:: [[sql_commands]]

# sql_command_count

Created: 20221101 18:01
Modified: 20221101 18:01

count(col) does *not* count null values, only non-null
count(\*) *does* count null values. It counts the number of rows, including ones that are entirely null

```sql
-- SQL cmd block
SELECT count(*), count(user_id), count(email)
FROM users_dirty
```

The above command returns 986, 983, 138
This means there are 3 nulls in user_id and ~800 nulls in email
