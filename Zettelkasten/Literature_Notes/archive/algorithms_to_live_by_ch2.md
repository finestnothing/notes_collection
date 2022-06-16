# algorithms_to_live_by_ch2
Created: 2022-06-13 09:35

- Explore/Exploit problems
	- Exploring means to try something new or gather new information
	- Exploit means to stick to something already known, or use information that you have already tried
- How do you balance exploring and exploiting? There are a lot of options
- Interval is very important. The closer to the beginning of your interval (lifetime, time in city, etc), the more you should explore. The closer to the end (old, about to move etc), it's usually better to exploit current bests. 
	- The longer that you have left in the interval, the more time you have to exploit any new options that you explore. Near the end, you may find something great but you won't have long to actually enjoy/exploit it.
- Herbert Robbins algorithm for explore/exploit
	- Exploit one place until it is a loss/disappointment. Then, explore and exploit the next win that you get until it is also a loss/disappointment, repeat.
	- Not perfect, and generally shouldn't be used.
- Gittins Index
	- Was created for drug trials, to balance exploring new compounds or more thoroughly testing/examining existing ones.
	- Geometrically weigh future opportunities less
		- If there's a 1% chance of being hit by a bus, value tomorrow dinner at 99% of tonights, 98% the following night, etc
	- Large table of values on page 40 of algorithms_to_live_by
		- Now moved to [[gittins_index_table]]
	- The value of an entirely untested option (0 wins, 0 losses) is 0.7029. If the value of a place drops below this, explore somewhere new!
		- 9 wins 1 loss: 0.8695
		- 9 wins 2 losses: 0.8103
		- 9 wins 3 losses 0.7573
		- 9 wins 4 losses: 0.7101
		- 9 wins 5 losses: 0.6677
	- Once you hit the value of 0.6677 in the example above, you should abandon the current option and explore a new one.
	- Page 41 of algorithms_to_live_by has a modified Gitins Index where the next payoff is valued at 99% of the current payoff, all the values of the Gittins Index table are higher

## References
1. [[202206111251]]