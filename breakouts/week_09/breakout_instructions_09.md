# Moved to bCourses - all of the content in this page has been moved to bCourses, and as of April 15, 2022, is no longer being updated.  Please use bCourses for the most recent, up to date version. This repo will be deleted once we are sure we have moved everything to bCourses correctly.

# Instructions for Breakouts for Week 09

Several breakouts are provided each week. Generally there won't be time to get to all of them. Instructors will select which ones and in what order they would like to use for their class each week. Instructors may choose to do some breakouts at the whole class level instead of using breakout rooms. For breakouts that we don't get to in class, that you are interested in, you can always come to office hours and discuss with the instructor or TA.

## Breakout 1 - Finding single points of failure

A major airline had a complete outage, involving several major systems that brought the operation of the airline to a complete hault.   No aircraft could take off anywhere in the system.  The outage lasted for almost an entire day before the problem was found and resolved.  After the problem was resolved, it took the airline a couple of days to clear the backlog of passengers stranded at airports.

It turns out that the issue was one single router in the computer network that failed.  

How could it be that a major airline would have a computer network with a single point of failure that several major operational systems were dependent on?

Most company start with a computer network of routers that is well designed.  As time passes, the network keeps getting larger and larger, as servers, workstations, subnets, etc. are added.  Even the best designed network will get keep getting more and more convoluted as years of network additions add up.

Once a complex, convoluted network is in place, it's really hard to reconfigure it.  Essentially the entire company would have to take a series of major outages, probably over months, to reconfigure the network from scratch.  However, it is possible to incrementally move a small number of routers.

After the outage, the executives want to know if the data science department can help incrementally moving a small number of routers.  Here are their main questions:
* Regarding routers that are single points of failure
  * Do we have any other routers that are a single point of failure?
    * Are there any single points of failure that are easy to avoid?
    * Are there any single points of failure that may be hard to avoid?
* Regarding routers that are not single points of failure
  * Can we detect routers that are not in efficient positions?

Assume each router has a routing tables, logs, etc. that we can write a program to collect into a single place.

Discuss how we can use a graph database and some of the graph algorithms we have learned to help answer those questions.

## Breakout 2 - Determining influence of employees in a major company

A lot of big companies have employees organized hierarchically into divisions, departments, groups, etc.  Typically, there is a formal hierarchy in which individual employees report to a manager, who reports to a director, who reports to an VP, etc. up to the CEO.

In addition to this official, formal hierarchy, there is often an unofficial, parallel, stealth network of relationships between employees.  

Assume we have the following data:
* Email logs
* Video conference logs
* Phone conference bridge logs
* Corporate land line call logs
* Corporate issued cell phone call and text logs
* Corporate messaging system logs (such as Slack)
* Meetings logs

Assume the logs will only give us such things as senders, receivers, participants, dates, times, durations, etc.  They will not include the actual content of the communications.

Discuss how we can use a graph database and some of the graph algorithms we have learned to see if we can uncover the network of unofficial, parallel, stealth relationships between employees.

Discuss some examples of relationships that would be valuable to uncover.

## Breakout 3 - Using graphy features and/or graph algorithm features as part of a heuristic to speed up an A* search

In last week's asynch and labs, we learned about the A* algorithm:
* Shortest path algorithm is quite intensive as it involves finding all paths
* To guarantee we have the shortest path, we have to find all paths
* A* uses a heuristic at each step to reduce the search space
* A heuristic is sometimes called a rule of thumb, an educated guess, a mental shortcut, etc.
* A* gives us a faster solution, but it does not guarantee the shortest path

In one of last week's breakouts, we looked at several real world business cases and discussed some heuristics that could be used in the A* algorithm.   These heuristics were very specific to the business cases.

It's also possible to precompute and add some generic speedups to A* based on graphy features and/or graph algorithm features which can be used as heuristics or as part of a heuristic.

See if you can come up with some examples.

## Breakout 4 - Model evaluation using graphs

In the aynch, we discussed how AI, ML, DL, etc. models can be evaluated using graphs.  

The process works like this:
* Load the output solution from the model into a graph
* Gather graph statistics
* Run graph algorithms
* Analyze the graph statistics and outputs from the graph algorithms to see how well the model performed

In the business cases, we looked at the example of a hurricane wiping out an entire metroplex's electric power, wired communications lines, and cell towers.  Emergency services was bringing in portable cell towers to quickly restore communications.  An AI model was giving advice and multiple solutions on where to place the portable cell towers.  We looked at how using a graph database and graph algorithms can help us to evaluate the AI model's advice and which solutions have the highest probability of working best.

In the business case, we were assuming US domestic coastal city.  In the last few years, some US territories which are islands have had their communications infrastructure completely destroyed by natural disasters such as hurricanes, volcano eruptions, tsunamis, etc.

Most island territories tend to have:
* 1 major city where half (or more) of the population lives
* 2 or 3 smaller cities
* Small coastal communities
* Interior farmland with low populations but critical to food supply
* In the modern era, most external communications links to islands tend to be using submarine (underwater) fiber optic cables.  
* External submarine fibre optic cables tend to be connected to the largest city
* Due to most cities being coastal, the island fibre optic cables need to run from the largest city over stretches of often uninhabited territory

Consider different types of communications:
* External to the island
* Within the major city
* Within the smaller cities
* City to city
* Small community to city
* Small community to small community
* Farmers in rural areas need to coordinate food supply, get food to people before it spoils
* Workers in rural areas need to coordinate installation of portable cell towers, portable generators, fuel to generators, repairs to electric power cables and fibre optic communications lines, etc.

Discuss how the solutions we discussed in the asynch would need to be modified for the island scenario.
