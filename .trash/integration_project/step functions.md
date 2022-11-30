up:: [[jira_proof_of_concept]]

# Step Functions

Each one will execute a specific task and have appropriate logging
Works for different integrations and destinations

Importable
	One notebook with all step functions defined there
	Run notebook so all functions can be imported from other notebooks
	Other notebooks just run them

Will have one notebook for running each function, basically just imports function

step_parameters table
	pass in integration id and required data to run the functions
step function list
	step_id and step name for getting step_parameters based on

Efficient way to go between integration step and step_parameters, specific with step_parameters
Option to reuse step_parameters somehow

Each function should have logging
	Start, end for each function

Also will want a step function to encrypt files if S3 doesn't
- Uses PGP encryption with a public key
- Happens after TEAMS file move

## Functions:

The functions below are subject to change.'
[[get_df]]
[[write_df]]
[[upload_to_s3]]
[[send_to_teams]]
[[encrypt_file]]
[[decrypt_file]]
[[generate_encryption_key_pair]]

Import libraries on demand, not import all
Views for integrationid to integration name
Namespaces for functions
Programmatically - when adding new integrations, only ask them to fill out fields pertaining to their specific steps