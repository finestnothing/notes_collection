# how_mars_rover_scheduling_bug_was_fixed
Created: 2022-06-23 08:49
#zettel/pending 
- The scientists for the mars rover modified the scheduling algorithm
- After the patch, if a process is holding up a higher-priority process, that instance was promoted to an equally high priority so that it would get done, then demoted once the original high-priority process was completed
	- This is called priority inheritance now

## References
1. [[algorithms_to_live_by_ch5]]