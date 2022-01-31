# Instructions for Breakouts for Week 05

Several breakouts are provided each week. Generally there won't be time to get to all of them. Instructors will select which ones and in what order they would like to use for their class each week. Instructors may choose to do some breakouts at the whole class level instead of using breakout rooms. For breakouts that we don't get to in class, that you are interested in, you can always come to office hours and discuss with the instructor or TA.

## Breakout 1 - Factory assembly line

In the asynch, we used the analogy of a factory assembly line and compared it to a data pipeline.

Select a product of your choosing. Make a list of the major pieces of the product (don't go into too many pieces).  

Discuss aspects of a simple, high level pipeline to assemble and finish the product.  

Try to give an example of each of the following:
* A process that would be dependant on previous processes
* A couple of processes (or more) that can be done in parallel
* Inputs to a process
* Outputs from a process
* A process that is very serial and creates a bottleneck
* What is the best optimization we can make to speed up a factory assembly line?

## Breakout 2 - Generalizing the factory assembly line to a data pipeline

Taking what we learned from the first breakout, discuss how we can generalize this to a data pipeline.  

Try to give an example of each of the following:
* A process that would be dependant on previous processes
* A couple of processes (or more) that can be done in parallel
* Inputs to a process
* Outputs from a process
* A process that is very serial and creates a bottleneck
* What is the best optimization we can make to speed up a data pipeline?

## Breakout 3 - Pipeline for a 3rd party sales channel dataset

Assume we have a third party sales channel for Acme Gourmet Meals which provides a batch file at the end of every day with sales data, such as:
* Store data
  * 3rd party sales channel has a different store id than our database (very common for 3rd party)
  * Address for the store that the 3rd party sales channel sold for
* Customer data 
  * Only for customers that made a sale that day
  * 3rd party sales channel has a different customer id than our database (very common for 3rd party)
  * First name, last name, address
* Sales
  * Each sale has the 3rd party's store id and the 3rd party's customer id (not ours!)
  * 3rd party sales channel has a different sales id than our database (very common for 3rd party)
  * Sales date, subtotal amount, sales tax, total amount
* Line items
  * Each sale has line items
  * 3rd party sales channel has a different product id than our database (very common for 3rd party)
  * Product id, quantity, price, taxable flag

Discuss at a high level:
* What types of bad data can we get?
* How to reconcile the 3rd party ids with our ids
  * Which type of data should we give to the 3rd party?
    * Should we give the 3rd party our product list? Why or why not?
    * Should we give the 3rd party our customer list? Why or why not?
* How to combine the 3rd party sales data with our data

## Breakout 4 - Advantages and disadvantages of clusters of containers

Last week, in a breakout, we discussed and came up with a list of advantages of containers.

Discuss any new advantages that clusters of containers give us.

Last week, in a couple of breakouts, we discussed cybersecurity issues:
* Directory and file ownership and permissions issues with mounted volumes
* Being able to get a root shell, the Holy Grail of hacking, if Docker is run as root

Do clusters of containers add any cybersecurity risks on top of these known risks?

## Breakout 5 - Scale up, Scale down, load balancing

In this week's asynch we discussed how container orchestration systems allow us to scale up and down and load balance such as the following:
* Start with a minimum number of containers
* Add more containers during peak times when demand increases
* Remove containers as demand decreases
* Load balancing: distributing the workload evenly among containers

We covered the business case of an electric company using smart meters with more frequent readings during peak times to keep the electric grid stable, and less frequent readings during off-peak times.

Try to come up with and discuss a different example of a business cases of peak and off-peak times that would need to have the IT systems scale up and scale down.  We briefly mentioned: POS, airline boarding pass readers, social media streaming data, web server logs, etc.  You can choose one of these or make up one of your own.

Also, design a high level algorithm to programmatically do the following:
* Detect that we need more containers
* Detect that we need less containers
* Load balance 
* Figure out the minimum number of containers

Hint:  remember from our study of Linux that we can gather metrics such as percentage of CPU usage, percentage of memory usage, etc.





