# Instructions for Breakouts for Week 07

Several breakouts are provided each week. Generally there won't be time to get to all of them. Instructors will select which ones and in what order they would like to use for their class each week. Instructors may choose to do some breakouts at the whole class level instead of using breakout rooms. For breakouts that we don't get to in class, that you are interested in, you can always come to office hours and discuss with the instructor or TA.

## Breakout 1 - Company still uses old school waterfall with ETL

Assume you have just taken a position as a full stack data scientist at a company.  

The company's IT department is very old school.  They are still using the waterfall processs with traditional data warehousing and traditional business intelligence.  They are still doing ETL instead of ELT.  (Remember from the asynch that when people say ETL they sometimes mean ELT.  It's just that the term ETL is long engrained. THIS ACTUALLY IS ETL.)

One of the projects you have just been assigned to has a dataset that will be loaded by the ETL group, and your boss wants you to perform some analytics on it.  Your boss asks you to review the project plan and give feedback.  According to the timeline, it will be 11 months before you are able to do any analytics on the dataset. The kickoff won't happen until the project plan is signed off on, which may take several more weeks.  So, it could be a year or more before you can even start on analytics.

You request to take a look at a sample of the actual dataset.  You find out that no one has a sample of the dataset, just the specifications and layout of the dataset.   Somehow they managed to come up with a detailed 11 month project plan without ever even looking at the data.   You find this very strange.  

However, this is not strange for a waterfall shop. It's typical, expected, and business as usual.  The way they have done things for the last 20+ years.   The 11 month project plan is probably a generic plan created 15 or 20 years ago with minor modifications along the way.  They just dust it off and do some word replacements every time they need it.

This is also very typical for outsourcing companies as well.  The long timelines are very profitable, so there is no incentive for them to change.  

Discuss how you would explain and convince your boss to give you a shot at a more modern approach, and how you can produce some analytics in a few weeks.

Assume you boss is convinced by your explanation.  Now you are under pressure to perform.  

What should be your number one goal to achieve in the shortest time possible? 

What things would you sacrifice to achive this goal in the short term, that can be enhanced longer term?

## Breakout 2 - Fuzzy logic

In the asynch and labs, we discussed and used some modules to handle misspelled words, typos, alternate spellings, garbled data, etc.

* Soundex
* Levenshtein Distances
* Fuzzy Logic

We discussed that fuzzy logic combines things like traditional Soundex and Levenshtein Distances with things like:
* Context
* Grammer
* Statistical words and phrases by language, region, industry, person, etc.

Assume you are a full stack data scientist at a company.  Your boss tells you that they have a startup incubator that funds startup companies, with your company serving as a test bed and also receiving first use of the new technologies being developed.  

They just invested in a new startup that is focused on fuzzy logic.   Your boss asked you if you have worked on fuzzy logic before.  You reply that you have.  She asks you to schedule a meeting with the fuzzy logic startup and explain to them some of the shortfalls you have seen so far with existing modules and some ideas for how to make their module better.

Discuss a game plan of shortfalls and ideas that you would discuss with the fuzzy logic startup.

## Breakout 3 - To dedupe or not to dedupe

In the asynch and labs, we learned that we sometimes have duplicates in a dataset and we need to "dedupe" or de-duplicate, that is, remove duplicates.  We also learned that sometimes duplicates are legitimate, and we should not remove them.  

Consider the following scenarios and discuss if we should dedupe or not:

* A POS shows a sale of a customer buying a product.  Later it shows another sale of the exact same customer buying the exact same product with the exact same form of payment.  Consider each of the following timelines:
    * A few seconds later
    * A few minutes later
    * A couple of hours later

* A POS shows a sale of a customer buying a several products with specific quantities of each.  Later it shows another sale of the same customer buying the exact same products in the exact same quantities with the exact same form of payment.  Consider each of the following timelines:
    * A few seconds later
    * A few minutes later
    * A couple of hours later

* Our product table has two items with the exact same name and description:
  *  With different vendor part number
  *  With the same vendor part number

* Our customer table has two customers with the exact same first name and exact same last name at the exact same address
  * With similar buying patterns
  * Without similar buying patterns
  * With the same form of payment that they always use
  * With a different form of payment that they always use

* Our holiday table has two holidays on the same date with different names

## Breakout 4 - To impute or not to impute

In the asynch and labs, we learned what is probably a new term to most students: impute or imputing.  We learned that it means to fill in missing values.

We learned about some techniques we can use to impute:
* Average
* Fill down: previous values, good for time series, etc.
* Design a model to predict the value

We also learned that we can skip imputing by setting it to a null value and/or leaving it empty.

We also learned of the dangers of imputing: we risk that we will distort the dataset

Consider the following scenarios and discuss 1) if we should impute or not, and 2) if so, how to impute and the risk we are taking:

* A dataset that's going into a machine learning algorithm has one feature (data item) that is crucial to the algorithm.  Assume we get a million records in each dataset each day.  Consider the following missing percentages for the feature:
    * 1 % is missing
    * 10 % is missing
    * 25 % is missing
    * 50 % is missing

* A POS system has a sale transaction with a missing time stamp:
    * The POS system has a server at the store.  Without network delays transactions always come in order.
    * The POS system has a central server for all stores.  With network delays some transactions come out of order by as much as 30 seconds.
    * The POS system has a central server that is old school mainframe that batches in 4 hour batches.  Transactions in the batch are sorted by customer id.

* A remote weather station takes temperature readings once every 15 minutes and communicates via the cell phone network. The cell phone network sometimes loses connectivity.  Readings are use it or lose it, so when cell phone network connectivity is down, readings during that time period are lost.  There are numerous weather stations about 100 miles apart.  Consider the following cases:
    * One reading is lost.  We have before and after.
    * 4 hours of readings are lost.  We have before and after.
    * 24 hours of readings are lost.  We have before and after.
    * 3 days of readings are lost.  We have before and after.

* We have a robotic factory where industrial robots do all of the assembly line work.  The only work done by humans is maintenance on the robots.  One robot puts out widely variant readings in streaming fashion.  The data is use it or lose it.  So sometimes our process to read the streaming data cannot keep up and we lose that data.

* A railroad has millions of sensors on tracks all over the country to detect issues with the tracks, and especially to guard them against terrorists attacks.  The data feeds into an AI system.  The AI system can immediately recommend actions such as sending an emergency message to a train to immediately stop.   Freight trains can take miles to stop.  Emergency stops are extremely dangerous, so we don't want to stop unless we absolutely have to.  The sensors transmit data via the cell phone network, so as mentioned previously, we can lose data.

* An airline has its aircraft report data such as direction, speed, altitude, rate of climb, rate of descent.  The aircraft transmit data via cell phone network, satellite, or short wave radio depending on where they are flying in the world.  Especially over remote spans of uninhabited ocean, we want to warn aircraft of dangers such as weather, turbulence, other aircraft, etc.  In remote areas of the oceans, it's sometimes hard to get connected even using both satellite and short wave.   When we are not connected we lose data.  

## Breakout 5 - Outliers: keep, toss, or replace

In the asynch and labs, we learned that outliers are often very hard to decide what to do with.  We can keep them, toss them, or replace them, depending on the circumstances.

Consider the following scenarios and decide if we should keep, toss, or replace the outliers.  If we decide to replace them, what should we replace them with?  What is the risk for each case?

* Weather stations:
   * A weather station in Berkeley reads 120 F in January
   * A weather station in Berkeley reads -15 F in January
   * A weather station in Dallas reads 120 F in August
   * A weather station in Dallas reads 90 F in January
   * A weather station in Seattle reads 110 F in August

* Big box store: We have sensors that detect how many people have entered the store and how many have left the store.  On one day the data shows that the store was off the charts busy, not typical of the day of week and time of day.  Consider the cases of:
   * The sales data does not seem to confirm the number of people in the store
   * The sales data is higher, but not quite enough to account for the number of people in the store, maybe half of them

* Railroad track sensors: A track sensor gives a warning of disconnected track (possible terrorist attack) but the secondary sensor is showing connected. An AI system has to make a split second decision, what should it do?
      
* Nuclear reactor: A cooling tower gives an off the charts high reading, however, it has given false readings in the past.  An AI system has to make a split second decision, what should it do?
   * Secondary sensors are mixed, but lean against confirmation.
   * Secondary sensors are mixed, but lean towards confirmation.
   

