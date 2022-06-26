# monte-carlo-football
A Monte Carlo simulation to guesstimate the Premier League champions.

This project uses mongoDB for its database operations. To run the program, you need to download the mongoDB first.
https://www.mongodb.com/try/download/community

This is not a complete project, but I will work on it in the following week/days.

Monte Carlo, which is a county in Monaco and a famous city for gambling, is a discrete simulation approach used in the existence of very few data. 
Also this method is usually used in static simulations.

The main idea here is to use few past data to simulate the system, in this context it is the Premier League.

synthetically genereated the data required to simulate by using past season's information, provided in a .csv file.
the amount of synthetic data generated is equal to the wanted simulation size.

The goals are calculated with two main factors:
- w: the average goals that team scored
- l: the average goals that team conceded

so the wl = the goal scored to team b by team a. (w is the average of the scorer team and l is the average goals conceded for the opposing team)
i.e.: 
- Manchester City scores a goal on average of ~2.6 per game.(values are generated by normal distribution using past data)
- Chelsea concedes ~0.63 goals per game.
- Manchester scores 2.6 * 0.63 = 1.638, ~2 goals. (always round the result)

then, the fixture is created where every team matches with all, both as home and away teams

the number of match weeks in season are determined by: (# of teams - 1) *2
and there will be (weeks *2) = 12 matches

the simulation of the fixture matches are done by weekly or all league.

the part where estimating the win probability for each team after 4th week not implemented, however it can actually be done easily by some basic calculations:

the win probability of each team for week(n) after week(4) can be estimated by the number of times where team is #1 in all league simulations until the week(n)
divided by simulation_size.
i.e.
Manchester City is #1 at week(4) in 643 simulations
the simulation size is 1000
Manchester City prediction is 653/1000 = 64.3%



