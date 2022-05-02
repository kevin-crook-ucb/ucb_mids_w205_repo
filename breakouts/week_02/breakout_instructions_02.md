# Moved to bCourses - all of the content in this page has been moved to bCourses, and as of April 15, 2022, is no longer being updated.  Please use bCourses for the most recent, up to date version. This repo will be deleted once we are sure we have moved everything to bCourses correctly.

# Instructions for Breakouts for Week 02

Several breakouts are provided each week.  Generally there won't be time to get to all of them. Instructors will select which ones and in what order they would like to use for their class each week.  Instructors may choose to do some breakouts at the whole class level instead of using breakout rooms.  For breakouts that we don't get to in class, that you are interested in, you can always come to office hours and discuss with the instructor or TA. 

## Breakout 1 - Widely held beliefs that turned out not to be true

Often, there are widely held, often long standing, beliefs that are not backed up by actual data.  Typically they come from anecdotal evidence, which are factual claims relying only on personal observation, collected in a casual or non-systematic manner. 

Here is one real world example from the airline industry:

Airline tickets are traditionally sold in two main categories:
* Full fare tickets that are fully refundable and have the flexibility to change without penalty.  These are typically purchased for business travel.
* Discount tickets that are not refundable and have high penalties for changes.  These are typically purchased for vacation travel.

For many years the airlines industry assumed that business travelers changed their tickets all the time and that vacation travelers rarely changed their tickets. 

Airlines were one of the first adopters of AI back in the 1980s for revenue management for FM/OB (fare mix / over booking).  Basically, airlines need to determine what mix of fares to allow, that is, how many fares at what price for each flight.  That is the FM part.  The other part is OB, that is how much should we over book a flight, such that it goes out with no empty seats and no passengers are left at the gate when the flight departs. 

The AI models heavily relied on "show rates" for OB.  For each passenger, what is the probability that they will show up for the flight.  These models always assumed a high show rate for vacation travelers and a low show rate for business travelers.

Years later when the business intelligence / data warehousing department came online, it was the first time that anyone actually crunched the data to see if these assumptions based on anecdotal evidence were true.  It turned out, just the opposite was true.  Business travelers rarely changed their flights, even though they could, and vacation travelers often changed their flights, even though they had to pay a penality.

The first consequence of this was to revamp the AI OB model to take into account actual show rates based on actual data and not anecdotal evidence.  

The second consequence was to revamp the rules for vacation travelers.  Such as lowering the change fees and making it easier for them to change.  The revenue gained from change fees made up for the spoiled seats.  Also, allowing vacation travelers to stand by for earlier flights at no cost.  If they don't get on the earlier flight no revenue is lost.  If they get on the earlier flight it frees up their seat on the later flight for last minute travelers.

Can you think of other examples of widely held beliefs based on anecdotal evidence that turned out not to be true when people actually crunched the data?

## Breakout 2 - Proposing a systematic review of a company's widely held beliefs

Note: it is recommended that you do breakout 1 before this one.

We have seen that widely held beliefs based on anecdotal evidence often turn out not to be true after all.

There is a silver lining to this.  The case of someone gives you a lemon, make a lemonade.  This can be a great opportunity for a data scientist.

Suppose you are working as a data scientist at a company.  One project you might propose is to make a comprehensive list of all the widely heald business facts at your company.  Try to sort them from the most impactful first.  Work down the list starting with most impactful. For each one, ask "how do we know this is true?"  Then see if the actual data confirms or denies.  If the data denies the assumed fact, then examine AI models, ML models, DL models, etc. that need to be changed.  Then examine any changes to business processes that you might propose to take advantage of the new found knowledge.

Each team should prepare a "2 minute elevator pitch" to propose the above project to your management.  

When preparing 2 minute elevator pitches, remember BBI and CCC (triple C):
* BBI
  * Bold
  * Brief
  * Impactful
* CCC (triple C)
  * Clear
  * Concise
  * Convincing

## Breakout 3 - Reading and understanding a data model to determine how to join tables

In this breakout your team will walk through the sales database data model (DM) in entity-relationship diagram (ERD) notation for the primary dataset.

GitHub => ucb_mids_w205_repo => labs => week_02 => sales_db_erd_data_dict.md

The primary dataset consists of the following tables:
* stores
* sales
* line_items
* products
* customers
* holidays

For each table in the primary dataset, list the following:
* The column(s) in the primary key
* Is the primary key a composite primary key?
* Is any foreign key part of the primary key?  if so what special shape do we use?

For each relationship, list the following:
* The parent table
* The child table
* Which foreign key(s) in the child table do we join to the primary key in the parent table

Answer the following question:
* Are there any tables without relationships?

The idea is that everyone on your breakout team should feel very comfortable with how to join the tables in our database.  This is needed for project 1 and before we proceed with the remaining breakouts.

## Breakout 4 - Joining tables in a secondary dataset to tables in a primary dataset

Outside of AI, data science, business intellience, data analytics, etc., most database joins are strictly done using a primary dataset following defined relationships in the data model.  

As data scientists, we will make frequent use of secondary datasets to enhance the primary dataset.  

Secondary datasets are often denormalized, that is, they are not properly modeled. They often contain redundant data and don't have relationships between tables.  Our secondary dataset was setup this way on purpose to give you some experience with this.

In this breakout your team will walk through the sales database data model (DM) in entity-relationship diagram (ERD) notation for the secondary dataset and consider possible joins with the primary dataset.

The secondary dataset consists of the following tables:
* zip_codes
* cities
* states

Remember that all joins that don't follow a defined parent / child relationship are considered dangerous joins.  We have to figure out which informal keys to join on.  

For each table, give a list of possible joins to the primary dataset and which informal keys to join on.

We discussed two major problems than can occur when doing dangerous joins.  
* What problem can happen when there are rows in the primary table do not have corresponding rows in the secondary table?  
* What problem can happen when their are rows in the primary table that have more than 1 corresponding row in the secondary table?

## Breakout 5 - Discussing some common secondary datasets and how they can be useful

Think of some other secondary datasets that can be useful in general.   Consider things like weather data, economic data, local demographic data, household data, traffic data, etc. Time permitting, you may want to take a look at https://catalog.data.gov/dataset and do some searches to get some more ideas.

## Breakout 6 - Designing queries and data visualizations 

In this breakout you team will look at designing queries and data visualizations for some of the analytical questions from project 1.

For the queries, you don't have to write SQL, just give a high level design of the query.  Since we already have the joins mapped out, you don't need to include details of joins.  

For the data visualization, you don't have to create the data visualization, just give a high level design, such as what type of data visualization and a brief description of how it will look.

For each of the following, give a high level design of a query and a high level design of a data visualization.  

For store name, use the city name.  

For months, use the natural sort order (January, February, March, etc.)

For product name, use the description in the products table.

* Total sales as a dollar amount
* Total sales as a dollar amount by store, sorted by store name
* Total sales as a dollar amount by month, sorted by month
* Total sales as a dollar amount by store, then by month within store, sorted by store, month
* List the customers who have signed up, but have never bought anything, sorted by last name, first name
* How many of each meal were purchased by day of week, sorted by meal name, day of week
