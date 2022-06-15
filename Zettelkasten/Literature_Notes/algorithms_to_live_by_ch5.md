# algorithms_to_live_by_ch5
Created: 2022-06-15 15:34

- 2-Machine sorting problem
	- Used for optimizing downtime/overall time
	- Proposed by Selmer Johnson at RAND Corporation, 1954
		- Initially applied to book binding machines, but works equally well for laundry
		- If the first of two steps takes longer, put it at the end of the schedule
		- If the second of two steps takes longer, put it at the beginning of the schedule
		- If first and second are equal, put wherever they fit/in the middle
- Sum of Completion Time Minimization
	- Assuming all tasks are weighted the same, it is best to do shorter tasks first
		- E.G. a 4 day project and 1 day project. If you do 4 day project first, total wait time is 4 days, and wait time for 1 day project is 5 days, so 9 total days of waiting. If 1 day done first, 1 day of waiting plus 5 days of waiting for 4 day project.
	- Doesn't change the total time, but reduces the sum of completion times
	- Also minimizes the number of tasks faster
- Mars Rover Scheduling Bug
	- 1997, mars rover landed on Mars
	- There was a significant bug in the scheduling algorithm. A low priority task had reserved the database. When it was interrupted after a set amount of time, a high priority task is put on hold since it also needs the database. The low priority task was not getting done because there were a lot of medium priority tasks that were scheduled before it, therefore locking both the low priority task and high priority task behind the medium ones.
	- They modified the algorithm to include priority inheritance, so when the low priority task blocked the high priority one, it was temporarily promoted to high priority
		- This meant that the low priority task actually got completed so the high priority task could run
	- The issue was known about before it was launched, but ironically it was deemed a low priority issue
- Task grouping
	- If you have similar tasks, do them all at once
		- If you have 5 bills to pay that all have 30 day period, pick one day in 30 day period to do all of the bills at once rather than doing them as they come in
	- It will make you switch tasks less and make it easier to focus on this task as well as others

## References
1. [[202206150654]]
2. [[202206141754]]