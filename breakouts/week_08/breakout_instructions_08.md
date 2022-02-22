# Instructions for Breakouts for Week 08

Several breakouts are provided each week. Generally there won't be time to get to all of them. Instructors will select which ones and in what order they would like to use for their class each week. Instructors may choose to do some breakouts at the whole class level instead of using breakout rooms. For breakouts that we don't get to in class, that you are interested in, you can always come to office hours and discuss with the instructor or TA.


## Breakout 1 - Classifying real world problems that are graph oriented

In the asynch and labs, we investigated graphs in terms of graph shapes, graph characteristics, and other considerations, such as minimum spanning trees, density, and x-partite. 

Graph Shapes:
* Random Network
* Small-World Network
* Scale-Free Network

Graph Characteristics:
* Connected or disconnected
* Weighted or unweighted
* Directed or undirected
* Acyclic or cyclic

Other considerations:
* Can finding a minimum spanning tree be useful?
* What would the density be like?  
  * If high density, can we peel off layers?  
  * If low density, can we add relationships?
* What would the x-partite look like: monopartite? bipartite?  k-partite?

Consider the following examples.  For each one, discuss in terms of the above details:
* A big box store chain's supply chain distribution network: ships importing finished goods, port services, transportation from ports using trucks and trains to warehouses, transportation from warehouses to stores using trucks, etc.
* A computer network at a big box store connecting: a headquarters complex of several buildings, regional headquarters, warehouses, stores, vendors, 3r party sales channels, etc.
* A local food delivery service from restaurants to customer's homes
* A startup airline's flight schedule, which is hubless with point to point flights, with connections incidental and low priority
* An established major airline's flight schedule, with several regional hubs enabling connections by design

## Breakout 2 - Breadth-first versus depth-first searches

In the asynch and labs, we discussed the difference between breadth-first and depth-first searches:
* Breadth-first searches visit sibling nodes first before visiting child nodes
* Depth-first searches visit child nodes first before visiting sibling nodes.

Conside the following examples.  For each example, discuss which you think would be the best approach: a breadth-first search or a depth-first search:
* An airline passenger is taking a flight from San Francisco, connecting in Chicago, to New York.  Due to bad weather, their flight arrives an hour late in Chicago.  The passenger misses their connecting flight to New York.  We need an algorithm to reroute them to New York from Chicago.
* An airline's aircraft need regular maintenance.  The FAA sets a maximum number of flight hours and a maximum number of cycles (takeoffs and landings) an aircraft can go through before it needs maintenance.  The airline only has a few maintenance bases with a set number of maintenance slots each night.  The airline does maintenance overnight to maximize daytime flying.  Ideally we want each aircraft to fly as many hours and as many cycles possible within the limits and finish a day at a maintenance base with a reserved maintenance slot.  Hint: should we start with the aircraft's current location and work forward, or start with a maintenance slot and work backwards until we get the aircraft's current location?
* Routing computer network traffic in a computer network at a big box store, connecting a headquarters complex of several buildings, regional headquarters, warehouses, stores, vendors, 3r party sales channels, etc.  Note that computer network traffic is measured in hops between routers, not in distance.
* A computer program that plays chess.  Hint: would opening moves be different from regular game play?
* A Monte Carlo simulation
  * Use repeated random sampling (often millions, billions, etc.), often involving several random variables, to create a list of possible outcomes and the probability of each outcome, typically to predict the future from the past. 
  * For example, in retirement planning, we might run millions of trials of combinations of past stock market history, past bond market history, past inflation, etc. on a simulated future of 30 years and generate a list of growth percentages (or negative growth percentages) and the probability of each.  Typically we would have a starting principle and a yearly spend amount that grows with inflation.  We could give the customer an aggregate probability that they would run out of money in 30 years, a probability that they would keep their principle in 30 years, a probability that they would double their principle in 30 years, etc.
* A Las Vegas simulation
  * We input a desired outcome.  The algorithms runs trials (similar to the Monte Carlo simulation) until the desired outcome is reached or until all outcomes have been exhausted and the desired outcome cannot be found.  This tells us how many trials it takes to get a specific outcome.
  * In the retirement planning scenario detailed above, we would start with the outcome of running out of money in 30 years.  How many trials to get to that?  We run the outcome of keeping our principle in 30 years.  How many trials to get to that?  We double principle, how many trials to get to that? etc.

A couple of additional questions:

Which do you think is easier to create a parallel algorithm for:  a breadth-first or a depth-first search?

Which do you think is more useful: Monte Carlo simulations or Las Vegas simulations?

## Breakout 3 - Eulerian circuits versus Hamiltonian circuits

In the asynch and labs we discussed the difference between Eulerian circuits and Hamiltonian circuits:
* Eulerian circuit
  * Visit every relationship only one time
  * Visit nodes one or more times
* Hamiltonian circuits
  * Visit every node one one time
  * Visit relationships one or more times

Conside the following examples.  For each example, discuss which you think would be the best overall approach, Eulerian or Hamiltonian.  Or is neither one a good approach, that is, do we need to visit both nodes and relationships multiple times?  Can we break it down into more specific problems or more specific subproblems that are clearly Eulerian or Hamiltonian?
* A broadway show, or circus, or entertainer, has a huge production of sets and equipment and wants to play multiple shows in the same cities.
* Checking parking meters along streets of a city
* Delivering mail
* Grocery shopping
* A policman on patrol
* A startup airline's flight schedule, which is hubless with point to point flights, with connections incidental and low priority
* An established major airline's flight schedule, with several regional hubs enabling connections by design
* A HVAC vendor's parts delivery that get ad hoc calls all day at random times that could be in totally different areas of the city miles apart

## Breakout 4 - Traveling salesman problem

The traveling salesman problem is typically stated as:
* A salesman starts and ends in his home city
* The salesman has a list of cities the salesman needs to visit
* The salesman only wants to visit each city exactly once
* Each city pair has a distance between them
* The saleman wants to travel the shortest path possible

It's easy to see that we need to find a Hamiltonian cycle to solve the problem.  We want to visit each node (city) just one time.  Since there could be "dead ends", we may visit relationships (roads) more than once, such as backtracking on a road to a remote city.

This is one of the most widely studied problems in graph theory.  

The brute force solution is a combinatorial algorithm:
* Generate every possible order of the cities
* Calculate the cost of each possible order
* The answer is the order of cities with the lowest cost

If you Google it, you will find numerous algorithms trying to shave computation time off of the traveling salesman problem.   However, the down side to these algorithms is that we will never be sure we have the shortest path.  

Consider the following problem.  How would you design the algorithm to schedule deliveries:
* We want to deliver a product from one location near the city center to customer locations up to 30 miles from the city center
* We have several delivery vehicles
* We will only deliver Monday through Friday
* From 6am to 9am
  * Traffic within a 5 mile radius of the city center is clogged
  * Inbound traffic from 30 miles out is clogged
* From 4pm to 7pm
  * Traffic within a 5 mile radius of the city center is clogged
  * Outbound traffic up to 30 miles out is clogged
* For security reasons, we don't want to deliver before 6am or after 10pm.  We will leave it on the porch on odd hours.

Assume the deliver truck has an onboard mounted laptop computer.  What could we do after each delivery is made as the driver is starting to drive to the next delivery?

## Breakout 5 - Heuristics for the A* shortest path algorithm

In the asynch and labs, we investigated the A* shortest path algorithm:
* Shortest path algorithm is quite intensive as it involves finding all paths
* To guarantee we have the shortest path, we have to find all paths
* A* uses a heuristic at each step to reduce the search space
* A heuristic is sometimes called a rule of thumb, an educated guess, a mental shortcut, etc.
* A* gives us a faster solution, but it does not guarantee the shortest path

In the neo4j implementation of A* from the labs, it used the great circle distance as the heuristic.  This required each node to have a latitude and longitude pair. 

Note that in the modern era, as discussed in week 2, we typically use geodesic distances which consider the Earth as an ellipsoid rather than a sphere.  Geodesic gives a more accurate result.

Discuss the following cases where the great circle distance (or geodesic distance) is not a good measure.  What would be a good measure to use for the heuristic for routing the following?:
* A GPS device in your car that you requested to avoid toll roads
* A metroplex of lots of small cities and a ride share (or taxi) service has only purchased tax stickers for certain cities and cannot pass through other cities without risking a ticket
* Most airlines have a lot of left over cargo space after passenger bags have been loaded and contract with freight companies to carry freight in left over empty space
* You have an electic car and take a cross country trip and don't want to run out of juice in between charging stations

Another use of A* is design an algorithm to precompute paths based on general principles or probability density functions and use the precomputed paths as a heuristic for the actual path searching.  Discuss how this might be applied to the previous examples we discussed.  Hint: consider using a depth-first search to precompute paths to serve as a heuristic for a breadth-first search:
* An airline passenger is taking a flight from San Francisco, connecting in Chicago, to New York.  Due to bad weather, their flight arrives an hour late in Chicago.  The passenger misses their connecting flight to New York.  We need an algorithm to reroute them to New York from Chicago.
* An airline's aircraft need regular maintenance.  The FAA sets a maximum number of flight hours and a maximum number of cycles (takeoffs and landings) an aircraft can go through before it needs maintenance.  The airline only has a few maintenance bases with a set number of maintenance slots each night.  The airline does maintenance overnight to maximize daytime flying.  Ideally we want each aircraft to fly as many hours and as many cycles possible within the limits and finish a day at a maintenance base with a reserved maintenance slot.  Hint: should we start with the aircraft's current location and work forward, or start with a maintenance slot and work backwards until we get the aircraft's current location?
* Routing computer network traffic in a computer network at a big box store, connecting a headquarters complex of several buildings, regional headquarters, warehouses, stores, vendors, 3r party sales channels, etc.  Note that computer network traffic is measured in hops between routers, not in distance.
* A computer program that plays chess.  Hint: would opening moves be different from regular game play?
* A Monte Carlo simulation
  * Use repeated random sampling (often millions, billions, etc.), often involving several random variables, to create a list of possible outcomes and the probability of each outcome, typically to predict the future from the past. 
  * For example, in retirement planning, we might run millions of trials of combinations of past stock market history, past bond market history, past inflation, etc. on a simulated future of 30 years and generate a list of growth percentages (or negative growth percentages) and the probability of each.  Typically we would have a starting principle and a yearly spend amount that grows with inflation.  We could give the customer an aggregate probability that they would run out of money in 30 years, a probability that they would keep their principle in 30 years, a probability that they would double their principle in 30 years, etc.
* A Las Vegas simulation
  * We input a desired outcome.  The algorithms runs trials (similar to the Monte Carlo simulation) until the desired outcome is reached or until all outcomes have been exhausted and the desired outcome cannot be found.  This tells us how many trials it takes to get a specific outcome.
  * In the retirement planning scenario detailed above, we would start with the outcome of running out of money in 30 years.  How many trials to get to that?  We run the outcome of keeping our principle in 30 years.  How many trials to get to that?  We double principle, how many trials to get to that? etc.


## Breakout 6 - Building a probability density function for Cybersecurity risk for computer network traffic

A big company with a huge computer network wants to experiment with using graphs to detect suspicious network traffic.  Often hackers traffic patterns are unusual, such as "phone home" logic where they are copying massive amounts of data to external locations.  

Assume we can get the router logs of traffic patterns and load them into a graph database and try to check for unusual patterns.

However, the problem with this is that there will be tons of data, creating a high density graph, so much so that traditional pattern matching will be computationally intractible.

Another approach is a build a probability density function that will give us the current risk and allow us to possibly detect unusual traffic patterns.

Discuss how you would approach this. Hint: recall in the asynch we discuss how to handle graphs with a high level of density.

