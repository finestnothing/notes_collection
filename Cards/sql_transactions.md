up:: [[data_engineering_moc]]
tags:: #sql #bestpractice

# sql_transactions

Created: 20221027 08:43

Using transactions is best practice when modifying a [[sql_table]] or [[sql_database]] that is actively being used in [[prod]].

Transactions are essentially a way to create a [[git_branch|branch]] of database edits.
You can either keep all the changes you make or discard them together.

You can read or write to a table in a transaction
Once you begin accessing or altering a table it locks everyone else out until the transaction ends, but you can continue to access them
Make sure to keep any changes quickly, or set aside a time when no one else will be using the table(s)

The [[sql_transactions_code]]s are best run in the same file that you are making changes to, here is a quick reference [[sql_transaction_code_example|example]] of using the code as well
