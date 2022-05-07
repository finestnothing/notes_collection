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
- [x] Make better light-assignment
- [x] Retrain ML model
	- In progress, started [2022-04-14](../Daily_Notes/2022-04-14.md) 6:00PM
	- Changed to only Red/Yellow/Green for this training [2022-04-14](../Daily_Notes/2022-04-14.md)
- [ ] work on README
- [x] Need to run model in openvino
- [ ] Put it in DL workbench, see if that can improve performance
- [x] Presentation Work
- [ ] User Manual
- [ ] Maintenance Manual
- [ ] Testing Document

### Maintenance
- Tested with python 3.9.12
	- If using python 3.10, will run out of memory after first training epoch regardless of batch size
- If using a GPU for training or inference, have to uninstall pytorch and reinstall with cuda enabled (just installing with cuda enabled does not work)

| Jose Ramirez | Michael Ingrum | Alec Resha | Justin Henley | Chloe Hendrix    | Lan Nguyen | Dang Hoang |
| :----------: | :------------: | :--------: | :-----------: | :--------------: | :--------: | :--------: |
| Team Lead    | Backend        | AI/ML      | Databases     | API/Connectivity | Front End  | Front End  |

|      Name      |        Area of Focus        |
|:--------------:|:---------------------------:|
|  Jose Ramirez  |  Team Lead, On-Device Code  |
| Michael Ingrum | Backend Dev, On-Device Code |
|   Alec Resha   |    AI/ML, Data Pipeline     |
| Chloe Hendrix  |      API/Connectivity       |
| Justin Henley  |        Databases Dev        |
|   Lan Nguyen   |        Front End Dev        |
|   Dang Hoang   |        Front End Dev        |

The project has 4 distinct parts loaded in this repo. 
|   Component    |                                Purpose                                |
|:--------------:|:---------------------------------------------------------------------:|
| SignalSenseBox |                   The service that Nodes connect to                   |
|       UI       | This is the demo UI for [signalsense.link](https://signalsense.link/) |
|  AWS Service   |                  This is the centralized AWS service                  |
|    database    |       This is the database that runs on AWS and SignalSenseBox        |

### Tags
#school 