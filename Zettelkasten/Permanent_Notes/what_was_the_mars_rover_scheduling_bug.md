# what_was_the_mars_rover_scheduling_bug
Created: 2022-06-23 08:43

- The mars rover was in a perpetual loop of not writing data to the I/O bus
- Scientists couldn't figure out why, because the process for writing data was a high priority process and should've been done first
- The rover kept restarting as well
- The bug was actually known about before launch, but was deemed too low of a priority

## References
1. [[algorithms_to_live_by_ch5]]
2. [[cause_of_mars_rover_scheduling_bug]]