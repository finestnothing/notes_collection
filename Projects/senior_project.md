---
name: senior_project
category: school
start_date: 2022-04-13
finish_date:
status: inprogress
---
# Project Title
## `= this.start_date` - `= this.finish_date`
## Status: `= this.status`
## Description

## Notes
- [ ] Make better light-assignment
- [x] Retrain ML model
	- In progress, started [2022-04-14](../Daily_Notes/2022-04-14.md) 6:00PM
	- Changed to only Red/Yellow/Green for this training [2022-04-14](../Daily_Notes/2022-04-14.md)
- [ ] work on README

### Maintenance
- Tested with python 3.9.12
	- If using python 3.10, will run out of memory after first training epoch regardless of batch size
- If using a GPU for training or inference, have to uninstall pytorch and reinstall with cuda enabled (just installing with cuda enabled does not work)
### Tags
#school 