up:: [[sql_transactions_code]]
tags:: #sql #code/example

# sql_transaction_code_example

Created: 20221027 08:48

A quick demo of using [[sql_transactions_code]] to alter a table in a database safely

```sql
BEGIN TRANSACTION

SELECT @@TRANCOUNT

ALTER TABLE {db}.{table}
ADD {field} {data type} {NULL | Default Value}

-- ROLLBACK
-- COMMIT
```
