# Moved to bCourses - all of the content in this page has been moved to bCourses, and as of April 15, 2022, is no longer being updated.  Please use bCourses for the most recent, up to date version. This repo will be deleted once we are sure we have moved everything to bCourses correctly.

# Instructions for Breakouts for Week 13

Several breakouts are provided each week. Generally there won't be time to get to all of them. Instructors will select which ones and in what order they would like to use for their class each week. Instructors may choose to do some breakouts at the whole class level instead of using breakout rooms. For breakouts that we don't get to in class, that you are interested in, you can always come to office hours and discuss with the instructor or TA.

## Breakout 1 - Adding AI to a queuing system

As we studied in the aynch and labs, queueing systems have been around longer than computers.  

Before computers, most queueing systems worked with boxes and folders.  Runners, typically teenagers or young adults, would run folders between departments: taking folders out of one department's out box and putting them in the next departments in box.  Boxes and folders were often color coded by priority, such as red, yellow, green, with red highest.  Folders were tabbed by the date they entered a department's box.  Folders that had been too long in the green box would be moved to the yellow box, and folders that had been in the yellow box too long would be moved to the red box.  Metrics were kept on how many folders a department worked per day, how many folders each person worked each day, etc.  A lot of what we think of as modern computer logic really isn't quite so modern.

We covered several business cases:

* Refunds review for a big box store

* Home loan processing

* Airline frequent flyers

We learned that enterprise message queues configured to work in the producer / consumer model are the modern equivalant of boxes and folders.   We learned that we can create very sophistocated queuing systems that include:

* Computer systems that are totally different (such as mainframes, Windows servers, Linux servers, TPF, etc.)

* Software systems from multiple vendors

* Humans to perform manual tasks that require human logic and reasoning that is considered too complex to be coded

The last bullet point is actually of the greatest opportunities for AI at most companies!  Please keep this in mind in your data science career.

Discuss a high level design to replace the manual tasks performed by humans for a business case.  You can think of a business case you know from your work or prior work, or you can use one of the business cases from the asynch / labs, which are listed above.  

You may want to consider the following:

* It's often helpful for an AI system to come up with categories, such as strongly approve, approve, lean towards approve, neutral (manual review required), lean towards disapprove, disapprove, strongly disapprove.

* Will we always have cases that will need manual review?

* Do we need to audit a random sample to make sure the AI system is giving the right answer?  How should we setup the audit?

* When we are busy, can we modify the categories that need manual review? Modify the auditing?  Likewise, when we are not busy?  Should we develop a risk model (another opportunity for another AI system!)

* Can we ever totally replace the humans? 

* When we deploy a new AI system, should we used a phased strategy?  How can we convince executives that it's working?

* The people with the most knowledge to help us build the AI system will be the people the AI system may be replacing.

Since queuing systems are such a fruitful area for adding AI with excellent return on investment (ROI), discuss how you as a data scientist would make a proposal to your data science management to review all queuing systems enterprise wide, make a list of all manual processes, and cherry pick the manual processes that are the best candidates.  What would be the criterial for best candidates?

## Breakout 2 - AI using the Lambda Architecture

We learned in the asynch and labs about the lambda architecture, which consists of the following layers:

* Speed layer 
  * Immediate analytics
  * No time for deeper analytics
  * Industry slang: "knee jerk analtyics"
  * We used the streaming model in our labs

* Batch layer
  * Later analytics
  * More time for deeper analytics
  * Allows us to evaluate how accurate the speed layer is
  * Allows analytics unrelated to the speed layer
  * Industry slang: "Monday morning quarterback analytics"
  * We used the publisher / subscriber model in our labs

* Serving layer
  * Present stored data and/or analytics results
  * Can use: traditional database, big data scale out database, NoSQL database, data lake, serverless SQL, or any combination

We covered several business cases that would lend themselves to the Lambda architecture:

* Social media

* Railroad track sensors

* Factory automation

* Air traffic control

* Point of sale (POS) for a big box store

* Refunds review for a big box store

* Home loan processing

* Airline boarding pass scanner

* Airline frequent flyers

* Image / video processing

We also learned about the Kappa architecture which has a speed layer only

Discuss what we lose if we use the Kappa architecture instead of the Lambda architecture.  

Discuss any cases you can think of where the Kappa architecture would be justified.
 
Discuss a high level design of a Lambda architecture for a business case.  You can think of a business case you know from your work or prior work, or you can use one of the business cases from the asynch / labs, which are listed above.  

You may want to consider the following:

* What should go into the speed layer?

* How can the batch layer be used to evaluate how accurate the speed layer is?

* How can the batch layer can be used for analytics unrelated to the speed layer?

* What should go into the serving layer?

Since lambda architecture is such a fruitful area for adding AI with excellent return on investment (ROI), discuss how you as a data scientist would make a proposal to your data science management to review all queuing systems enterprise wide, make a list of decisions for each process that could benefit the company if made in real time, cherry pick those processes that are the best candidates.  What would be the criterial for best candidates?


## Breakout 3 - Master data management and enterprise data catalogues

Master data management is the process of identifying master data for a company.  

Most companies have a lot of common data that most sofware systems in the company need.  It would be best for them to pull that data from one single source that is updated regularly and serves as the "system of record".  

For example a big box chain might have a list of stores.  There will be lots of different sofware systems in the company that will use the list of stores.  A lot of software systems will have their own table for the list of stores, and will have to manually update it when new stores open or when existing stores close or move.  If the updates are not made, often systems will not pull data for stores that are not in the store list.  Before master data managment became common, it would not be uncommon for a big box store chain to have tens or even hundreds of systems that needed to be manually updated whenever stores opened or closed.

With master data managment, the list of stores would be stored in master data, in a central database that is frequently updated that all software systems would need to check and pull data from on a regular basis.  In the past this was typically stored in a single SQL database.  Now more and more companies are placing it in data lakes, especially those using serverless SQL.

Another addition would be common data from public domain datasets, purchased commercial datasets, government datsets (data.gov), etc.  that numerous systems in the company can benefit from, especially analytical systems, AI systems, etc.  

Examples of these from the asynch and labs include:

* Demographics (Census data)

* Weather

* Economic Data (Federal Reserve datasets)

* Housing data by address (such as home values)

* IRS data

Select an industry of your choosing and discuss some examples of master data for that industry, both internal company data, and useful external data from public domain datasets, purchased commercial datasets, government datsets (data.gov), etc. 

Enterprise data catalogues typically will have a list of all of the companies master data, together with a description, layout information, schemas for serverless SQL, etc.  Discuss best practices for an enterprise data catalogue.

## Breakout 4 - Dumping enterpise message queue data into a data lake

For the first 30 years or so of enterprise message queues, data lakes had not been invented.  

In our labs, we studied the typical lifetime of messages on enterprise message queues using the different models (these are the typical lifetimes - people used to do some inventive stuff to make them longer):

* Publisher / subscriber has a defined lifetime such as 30 days, 60 days, 90 days, etc. and all message are removed when the lifetime has expired.

* Producer / consumer messages are deleted when they are removed from the queue.

* Streaming messages are use it or lose it.  If we don't capture them soon after they are received, they are lost.  

These lifetimes and typical useage pattern can result in the following issues:

* Popular publisher / subscriber queues that have a lot of subscribers which places a heavy load on the enterprise message queuing system

* Producer / consumer messages that would be beneficial for analytics are lost forever once they are read.

* Streaming messages are very intensive for reading.  If we have multiple systems reading the streaming messages, we put a strain on the enterprise message queuing system.  We also waste a lot of resources.

One solution is to simply write processes that dump data to a data lake, especially serverless SQL:

* For publisher / subscriber queues, write a process to subscribe to the queue and dump the messages to a data lake at X interval

* For producer / consumer queues, have 2 queues instead of 1.  Most queuing software allows for "mirrored" queues.  Write a process to consume  every message from the second queue and dump them to a data lake

* For streaming messages, write 1 process to read the streaming data and dump it to a data lake

Discuss some best practices for doing this, considering the following:

* How often should the publisher / subscriber dump to the data lake?

* Should every publisher / subscriber queue be dumped to the data lake?

* What should be the criteria for subscribing to a topic instead of reading from the data lake?

* Should every producer / consumer queue be mirrored and dumped to the data lake?

* How often should streaming data be batched and dumped to the data lake?

* Should every streaming data be dumped to the data lake?

* What should be the criteria for subscribing to streaming data directly versus reading from the data lake?


