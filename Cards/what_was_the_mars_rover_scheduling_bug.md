up:: [[historical_events_moc]]

# what was the mars rover scheduling bug
Created: 2022-06-23 08:43

- The mars rover was not writing data to the I/O bus
- Scientists couldn't figure out why, because the process for writing data was a high priority process and should've been done first
- The rover kept restarting as well
- The bug was actually known about before launch, but was deemed too low of a priority
	- [[cause_of_mars_rover_scheduling_bug]]
	- [[how_mars_rover_scheduling_bug_was_fixed]]