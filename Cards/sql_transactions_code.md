up:: [[sql_transactions]]
tags:: #sql #code

# SQL Transactions Code

Created: 20221027 08:37

```sql
BEGIN TRANSACTION
```

Starts a transaction, any future commands are sent in it until it ends

```sql
SELECT @@TRANCOUNT
```

States the number of transactions you are in (0 for none, 1+ for being in one or more)

```sql
-- ROLLBACK
```

Discards any changes that have been made in any transactions so far that have not been committed
Ends the transactions
It is best to keep this commented out so it doesn't end the transaction on it's own
To run it, select just the `ROLLBACK` part and execute that instead of the entire script

```sql
-- COMMIT
```

Finalizes any changes that have been made in any transaction
Ends the transactions
It is best to keep this commented out so it doesn't end the transaction on it's own
To run it, select just the `COMMIT` part and execute that instead of the entire script
This makes it so you don't accidentally commit your changes if you run the entire sql script, and lets you do testing before finalizing them

## Example

[[sql_transaction_code_example]]
