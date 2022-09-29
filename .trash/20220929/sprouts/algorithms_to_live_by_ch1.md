# algorithms_to_live_by_ch1
Created: 2022-06-11 13:52

## Early Stopping 
Mathematical/early stopping is a kind of mathematics problems where you try to tackle the question of when to stop. They are often applied when you cannot revisit a choice, like when you have to make a decision on the spot. You can't wait until the very last option or you are stuck with them, but if you stop too early then you almost certainly miss out on a better option. 

### 37% Method
One efficient method for solving this problem is by using the 37% rule. Under this system, you should spend 37% of your time or options just exploring, with no intention to pick them. You will likely see really good options, really bad ones, and everything in between. 
The original problem is called the Secretary problem. You are interviewing secretaries, but you have to give an immediate decision, either hire them or let them go on the spot. Once you hire one, you are done and stop searching. To apply the 37% rule, say that you have 100 interviews set up. For the first 37, do not hire any of them just get a bearing for their skills. After these, continue interviewing and immediately pick the next best option. In a fun mathematical coincidence, 37% of the time you will get the best option in your pool of options with this method.

The 37% model is also very flexible. You can apply it over the amount of options (see above), or over time. An example is setting a 1 month time to pick an apartment, but if you don't offer after seeing it, someone else immediately gets it. After browsing apartments for 11 days to observe options, keep looking until the next option that is the best you have encountered so far and immediately pick it.

Algorithms like this are called look-then-leap. You look for a set amount of time, then leap on the next best option.

37% was derived by using the formula of 1/e.

With 2 options, you have a 50/50 shot of getting the best option. With 3, you have a 33% risk of dismissing the best applicant, and a 16% risk of never seeing them. If you have 3 options, look at the first one then pass. This pass is purely random, and you have a 1/3 chance of having dismissed the best option. Now that you're past the observation phase, look at the second option. If it is better than the first, immediately take it and be done. If it is worse, then pass and take the third option. If the first option was the best, you either got the second best or the worst, but if it wasn't the best option then you are far more likely to have gotten the best option.

E.G.: Numbers represent how good each option actually is (3 is best)
(1, 2, 3) - You get the second best
(1, 3, 2) - You get the best
(2, 3, 1) - You get the best
(2, 1, 3) - You get the best
(3, 1, 2) - You get the second best
(3, 2, 1) - You get the worst

In this, you actually get the best 3 of 6 times, and second best 2 of 6 times and only get worst 1 of 6 times.

The threshold rule is also important to apply to the 37% rule, but it is not always feasible. If you are able to rank choices, you can pick a set threshold to immediately hire someone if they meet or exceed it. Returning to the secretary problem, we can use typing speed percentiles. The below percentile table is a helpful guide for using these, as the chance of getting a high percentile candidate falls off quickly near the end of your group. The remaining amount can be scaled up as well (50, 20, 10, 8, 6, 4, etc)
- Remaining: 25, pick from 98th percentile
- Remaining 10: Pick from 90th percentile
- Remaining 5: pick from 85th percentile
- Remaining 4: pick from 78th percentile
- Remaining 3: pick from 69th percentile
- Remaining 2: Pick from 50th percentile

### Optimal Stopping

Using optimal stopping seeks to solve a similar problem. As the chances of a success decrease, you take the first option further away.

The example used in the text is parking, comparing spaces from your destination with how full the parking is.
- Occ%: 0 spaces from dest: 0
- Occ%: 50 spaces from dest: 1
- Occ%: 75 spaces from dest: 3
- Occ%: 80 spaces from dest: 4
- Occ%: 85 spaces from dest: 5
- Occ%: 90 spaces from dest: 7
- Occ%: 95spaces from dest: 14
- Occ%: 96 spaces from dest: 17
- Occ%: 97 spaces from dest: 23
- Occ%: 98 spaces from dest: 35
- Occ%: 99 spaces from dest: 69
- Occ%: 99.9 spaces from dest: 693
I.E. if parking is approximately 90% full, take the first free spot you see starting 7 parking spots away from your destination. If 95% full, take the first free spot 14 spaces from dest. This applies well assuming that all parking is evenly distributed (all costs the same, infinite straight road, etc)

### Quitting while you're ahead

There is also a very helpful algorithm for telling when to stop ahead. This applies to situations where you have a chance for success/gains, but also a chance to lose everything.
If you have a 90% chance of succeeding (with 10% chance of losing all that you have made), you should attempt it 90/10=9 times then stop and keep your rewards. After that, the amount that you stand to lose (and the chance of it) outweighs the benefits. If you have a 50% chance of success or failure, only try it 50/50=1 time. You have nothing to lose the first attempt, but if you succeed, the chance of losing outweighs the potential benefits.

## References
1. [[202206100707]]
2. [[202206100727]]
3. [[202206111224]]