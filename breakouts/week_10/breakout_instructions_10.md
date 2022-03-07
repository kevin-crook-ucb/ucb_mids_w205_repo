# Instructions for Breakouts for Week 10

Several breakouts are provided each week. Generally there won't be time to get to all of them. Instructors will select which ones and in what order they would like to use for their class each week. Instructors may choose to do some breakouts at the whole class level instead of using breakout rooms. For breakouts that we don't get to in class, that you are interested in, you can always come to office hours and discuss with the instructor or TA.

## Breakout 1 - Deciding which type of database to use

In the asynch and the labs this semester, we have learned about several types of databases.

For traditional relational database:
* PostgreSQL, a traditional relational databases which use SQL as the query language

For NoSQL:
* Neo4j, a NoSQL graph database that uses Cypher as the query language
* MongoDB, a NoSQL document database
* Redis, a NoSQL in-memory, key-value database
* Wide-column, which uses SQL on top of NoSQL, such as Amazon RedShift or Google BigQuery

For each of the following real world business / use cases, from a purely data science perspective, discuss which type of database would be the best fit:

* A trucking company needs to plan long haul shipments all over the continential USA in the most efficient manner

* A multiplayer game has a leader board.  There can be millions of users world wide that are constantly earning points and everyone wants to know the current value of the leader board at any given time. 

* An major airline has its analytical database tables in Amazon Redshift.  It has data science analytical processes that analyze flights, customers, aircraft, pilots, flight attendants, etc.  Sometimes they need to analyze data using graphs, while other times, they use machine learning, deep learning, etc. where the graph structure is not relevant.

* A computer gaming company is developing a new game and wants to figure out common scenarios of sequential moves to help design a game playing engine

* A startup company has grown a lot over the last few years and is just starting to build a data science team.  They have sales data that needs to be analyzed from several points of view: store, customer, product, etc.

* A telecom company wants to lay new fibre cabling to businesses and homes around a city to allow communications in the most efficient manner possible

* A startup company has a website that uses a traditional relational database to store customer data in several tables and also server side session variables (sometimes called server side cookies)  When it gets busy, customers trying to login get timeouts when it is pulling data from several relational tables, and customers who are already logged in start to get timeouts when pulling server side session variables.

* An online auction company wants to detect fake accounts which bid to get prices higher

* A wall street firm receives streaming data of stock quotes that it needs to store in a database.  Stock quotes come in extremely high volume and constantly change.  Lots of users are constantly pulling quotes from the database and want the most recent data as fast as possible.

* A government domestic security agency is studing a terrorist group to try to figure out who the major players are so they can attempt to wiretap their communications, compromise them, etc.

* A growing company has a sales reporting database in PostgreSQL with numerous analytical reports, data visualizations, etc. that run against it.  As the data grows, the reports are running longer and longer.  Consider short term and longer term.

* An weather company has weather stations in hundreds of cities around the USA with sensors that are constantly updating with current temperature, wind speed and direction, barometric pressure, rainfall, etc.  They have lots of users who are contantly pulling the data in real time to display on websites, etc.

## Breakout 2 - A GPS (vehicle device) company supports route finding with live traffic data

A company makes and supplies GPS units (vehicle devices) that support route finding with live traffic data.  

Obviously, they would need a graph of all roads with attributes, weights, directions, etc.

As we discussed in previous weeks, they would probably use a variation of A* and pre-compute spanning trees between well known points to use as a heuristic.  They would need multiple spanning trees between points to allow a choice of route, or re-routing based on current live traffic.

For city to city travel, such as from a place in Berkeley to a place is Los Angeles, they would probably pre-compute routes that are updated for traffic conditions that would be used by numerous users.

For live traffic, some of it is known in advance, such as typical congestion periods based on day of week and time of day, construction zones, special events, holidays, etc.  Other things are not known in advance, such as collisions, bad weather, trees or powerlines or other debris down on roads, ice or snow, etc.

Most GPS units are designed to function independently of the server for calculating and re-calculating routes.  They typically use on board SSD to store data.  Like most IoT devices, the code is probably very tight to allow it to run on a low end processor without minimal memory, and it probably uses SQLite, which is a small footprint, single file SQL database designed for IoT devices.

GPSs typically download data for the roads in advance so they can function without communications with a server.  Ever so often, the GPS will need to update the roads data from the server. The GPS will also need to update the pre-computed minimum spanning trees and the pre-computed city to city high level routes.

For live traffic data, the GPS will need to communicate with the server in real time.  To avoid downloading a lot of live traffice data, most GPSs use this technique:  They create an imaginary grid structure.  When getting live traffic data, the GPS unit can send its current location in latitude and longitude to the server, and the server can figure out which imaginary grid the vehicle is located in.  It can then send data only for that grid, plus maybe some neighboring grids.

The server side is very different from the client GPS device side.  We will assume we can build servers as large as we need them.  

Focusing just on the server side, for each of the following, discuss which SQL or NoSQL database (or databases) would be a good fit, or maybe a homebrew solution:

* Imaginary grids 
  * Pre-compute
  * Store and query
* Spanning trees between well known points to use as a heuristic
  * Pre-compute
  * Store and query
* City to city routes between well known points
  * Pre-compute
  * Store and query
* Live traffic
  * Known in advance, such as construction zones, special events, holidays, etc.  
    * Pre-compute
    * Store and query
  * Not known in advance, such as collisions, bad weather, trees or powerlines or other debris down on roads, ice or snow, etc.
    * Pre-compute
    * Store and query
  
## Breakout 3 - Deciding between MongoDB or Redis for analytics

In the asynch and labs, we learned that when Redis's value is a JSON object, from a logical standpoint, it's very similar to MongoDB.  The main differences from a non-logical standpoint would be:
* Redis favors memory and backs to disk, the entire database has to fit into memory
* MongoDB favors disk and caches to memory, the database can be much larger as it doesn't have to fit in memory
* Redis can only query by key, to query on anything else, we have to read the entire database
* MongoDB supports queries by other than the key, and secondary indices can be created to speed up the queries
* Redis is much faster than MongoDB for queries by key
* For the same size database, Redis will be much more expensive than MongoDB due to using memory instead of disk

Let's limit our discussion to a purely data science perspective of using these databases for analytics.

Suppose a company has some analytical databases in MongoDB that are heavily used.  They are getting complaints that some analytical jobs are running slow.  The company decides to create an identical Redis database for each MongoDB database.  For each of the following scenarios, discuss whether it would be justified to use the higher cost Redis database instead of the MongoDB database:

* A big box store has a large customer database of hundreds of millions of customers
  * The big box store wants to send out ad hoc coupons in real time based on real time events.  An AI system will determine what coupons to send out to what customers.
  * An AI system reads each customer to determine who the best customers are and ranks them diamond, platinum, gold, silver, bronze, etc.
    * What if the frequency is once a month?
    * What if the frequency is once a week?
    * What if the frequency is daily?
* A credit bureau has a large customer database of hundreds of millions of customers
  * An AI system reads each customer to determine their credit score to sell this data to consumers and companies
    * What if the frequency is once a month?
    * What if the frequency is once a week?
    * What if the frequency is daily?
  * A customer is seeking pre-approval for a credit card in real time and the AI system needs to recalculate their credit score 
* An airline has 1,500 aircraft and a database of maintenance records
  * An AI system constantly runs through maintenace records to see what is coming due, what is completed, estimated times for repairs in progress, what needs re-routing to maintenance slots, what needs to be scheduled for maintenance, etc.
  * A daily morning report to executives needs to aggregate and summarize the above data
* A service station chain has a database of real time gas prices and a feed of real time oil futures prices
  * An AI system constantly analyzes the real time gas prices and oil futures prices to see if we need to raise or lower our prices at each station
  * An AI system makes predictions of future prices of gas, future volumes sold (people buy less when prices go up), and future profit margins at each station
    * What if the frequency is once a month?
    * What if the frequency is once a week?
    * What if the frequency is daily?

## Breakout 4 - Using MongoDB and Redis for a huge scale out website

In the asynch and the labs, we learned how most websites use both MongoDB and Redis.  

We will be covering Web API servers in the next couple of weeks with more details related to the web API server.  For the purposes of this breakout, we will limit our discussion to just the database pieces.

Whenever a customer logs into a website, the sequence typically goes like this:
* A traditional SQL relational database stores the username, password hash, customer ID, multi-factor authentication details, etc.  This data is pulled to validate the login.
* If the login is successful, the web server creates a unique session ID (SID) and uses that as the key for Redis with the value being session variables (aka server side cookies)  Session variables are used and updated with every transaction.
* The web server then queries the customer's data from MongoDB using the customer ID.  If they used a traditional relational database, they would have to pull from several relational tables which would be very intensive to join.  With MongoDB they can pull all customer data with one key based query.

Discuss the following issues:

The system of record (SOR) is a relational database.  A job has to refresh the MongoDB database with changes from the relational database every X minutes (or hours or once a day).  When a customer logs in, they may be seeing stale data.  
* Do you have websites that you log into regularly which will warn you of stale data, that recent transactions may not show up until X hours (or the next day)?  
* Do you think they might be using MongoDB?

Assume we have a refresh rate of X hours (or the next day) and customers are complaining about stale data.   Assume it's not feasible to constantly update MongoDB in real time (or we would not have this problem in the first place). 
* Could we use a second MongoDB to store updates on a temporary basis, query both on login, and give customers up to date data?
* Could we use Redis to store updates on a temporary basis, query both on login, and give customers up to date data?
* Could we hit synchronization issues with using two separate databases?  What if the primary MondoDB database gets updated, and we get a customer login before we can remove the update data from the secondary database?  Suggest a way to prevent this.
* What criteria could we use to determine which database to use for the secondary, MongoDB or Redis?
