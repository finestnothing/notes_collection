up:: [[+info_integration_project]]

# odp_more_info

ODP - Outgoing Data Processing

All future integrations, all pull from and use ODP
	Integrations - Mainly used by TechPS. E.G. Wants a file with all beneficiaries nightly etc
Basically any time we send data to the client, ODP handles it all
ODP doesn't have the code, it's just an orchestrator

Orchestrator job
	Every 2 hours
	Add things to a queue table
		Scheduling, etc
	Runs a new job over API if a new job is in the queue (for queue processor)
	Add "queued" entry to job_log, generate uuid for job_id

Schedule goes in integration_schedule, Integration list
Integration schedule
	As many options as possible without being unreasonable
	String for cron - <https://pypi.org/project/cron-converter/>
		Cron tab guru
	Figure something out here
	Only schedule needs to be machine readable
	schedule.next().isoformat() - Get ISO format of next
Once it's queued, no longer cares about specific time of sending. Only in 2 hour windows (for now)

Queue Processor
	Gets everything from queue
	Kicks off a new job for each job in queue
		Only assume we only have a single cluster configuration for now, but may want more later
	Add "running" entry to job_log, make sure to use same job_id
	remove record from queued table
	Start all jobs at once, not sequential

Integration job log table
	Log everything to this table
		job_id from uuid
		queued
		Running
		Success/failure

Create setup of small, medium, large cluster. Defaults to small, but each cluster can set size
	In queue processor, get the json runner cluster size for kicking off the jobs to make that customizeable
	Store the data in a dict

Blue tables - Not human editable at all
Green tables - Tables that get touched for adding new integrations
Orange - Dev tables only

From diagram
	First column is getting all scheduled jobs and should kick off the queue
Python should start the next job with the correct variables
	Look into hitting an existing job from python

Temp Runner
	Runs notebooks, catches any exceptions from step functions dropping
