up:: [[+info_work]]

tags:: #work 

# Standard Integration Project
Project home for integration project.
The goal is to send data to clients through a series of step functions with logging along the way.

- [x] Create Tables
	- [x] integration_queue
		- integration_id
		- job_id
		- queue_timestamp
	- [x] integration_list
		- integration_id
		- integration_name
		- client_id
		- cluster_size
	- [x] integration_schedule
		- integration_id
		- schedule
	- [x] job_log
		- integration_id
		- job_id
		- timestamp
		- status (queued, running, failed, success)
	- [x] step_log
		- job_id
		- step_id
		- timestamp
		- status (queued, running, failed, success)
	- [x] integration_log
		- High level log?
	- [x] step_param_map
		- Used for mapping integration_id + step_id = parameter_id
		- integration_id
		- step_id
		- parameter_id
	- [x] step_parameters
		- parameter_id
		- parameter_name
		- parameter_value
		- parameter_type
- [ ] Create Step Functions

[[odp_more_info]]
[[jira_proof_of_concept]]
[[step functions]]