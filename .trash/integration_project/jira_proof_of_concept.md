up:: [[+info_integration_project]]

# Jira Task - Proof of Concept

## Intro

As a: member of Data Services
I need to: be able to send data to clients and see what happens along the process
So that: it can be reported on and we can tell when something broke

## Requirements:

- Proof of concept with a few jobs that run one [[step functions]] each
- Integration Database
	- Must be source of truth for integrations and step functions
- Job orchestrator job to fill queue table with queued jobs
	- Should log when jobs are queued
- Queue processor to execute the job runners
	- Marks scheduled jobs as running
	- Create temporary jobs for each queued job
- Job runner that runs the integrations notebook and logs if something fails along the way
- Higher level function that takes functions as parameters
- [[step functions]]
	- Importable function that takes integration_id, {args}
	- Logs data to the integration_step_log table
	- Supports a 'dev' option that can be enabled to skip logging to the table
- Upload write file to s3 bucket step function
