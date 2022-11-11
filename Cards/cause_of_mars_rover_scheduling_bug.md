up:: [[what_was_the_mars_rover_scheduling_bug]]

# Cause of Mars Rover Scheduling Bug

Created: 2022-06-23 08:46

- The issue was a single low-priority process that used the database
- The scheduling algorithm would interrupt the low-priority process in order to work on other higher-priority tasks, but the database was still tied up by the process since it still had to eventually run
- The high priority process (writing data to the database) was unable to be completed because the database was still tied up from the low-priority process
- The low-priority process was never able to finish, because there were too many medium-priority tasks that were being scheduled before it, even though the low priority task was holding up the high priority task
- When the high priority task was pending for too long, the rover would restart in an attempt to fix whatever bug lead up to it being locked, but it kept repeating