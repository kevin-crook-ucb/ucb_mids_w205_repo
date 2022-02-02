# Instructions for Breakouts for Week 06

Several breakouts are provided each week. Generally there won't be time to get to all of them. Instructors will select which ones and in what order they would like to use for their class each week. Instructors may choose to do some breakouts at the whole class level instead of using breakout rooms. For breakouts that we don't get to in class, that you are interested in, you can always come to office hours and discuss with the instructor or TA.

## Breakout 1 - Old school ASCII for everything

Consider this scenario:

You have just taken a job as a data scientist as a company.  Your boss tells you one of the highest priority items is to start developing analytics from customer feedback surveys.  She points out that upper management has been waiting months for this and is eager to get analytics as soon as possible. 

It turns out that the company has been using a purchased 3rd party customer feedback software system.  The software is pretty good, very modern, and seems to support everything we need.  The interface supports UTF-8, including all the languages of the world, emojis, etc.

The company oursources its data engineering.  The outsourcing company has just spent several months, and a couple of million dollars in billing, building an interface, using the traditional waterfall methodology, to pull data on a daily basis and load it into a database.

You start looking at the data in the database.  You put in a few test comments of your own including emojis, and test a few commonly used "loan words" from other languages that include accent marks not used in English.  You notice that the emojis and accent marks are not showing up.  

You meet with the outsourcing company and ask what's up with that.  They reply that the interface API allows you to download in ASCII or UTF-8.  They didn't know what UTF-8 was, so they opted for ASCII.  You explain to them what UTF-8 is and why it's so important to analytics.  They check with their managment which points out that the written design that was signed off by your boss specifies that it would use ASCII, so they are under no obligation to change it without a signed change request and additional payment, which is hundreds of thousands of dollars.

Discuss the following:
* An explanation to your boss of how important UTF-8 is.
  * Include some examples of how emojis change the meaning of feedback comments
* Since you are new to the company, how would you handle the politics around:
  * Your boss has just spent a couple of million dollars.  She may not want to ask for extra hundreds of thousands of dollars in additional funds to fix it.
  * The initial work took months. Your boss has said her management is eager to get some analytics out of the data as soon as possible.  The fix may take weeks to get the money approved and weeks to get coded.

## Breakout 2 - Best practices for requesting data files

You are working at a company and we have identified data from 3rd party systems that we would really like to have to enhance our analytics.  We would want to ask for data in the format that makes the most sense for what we are planning on using it for.

Consider the following cases, recommend 1 or more formats, and discuss the advantages and disadvantages of each format:

* The data would be equivalent to a single table in a database and is going to be loaded into a relational database

* The data would be equivalent to multiple database tables, with parent/child relationships between them, and will be loaded into a relational database

* The data would be equivalent to a single table in a database and will be loaded into a big data platform that supports parallel loads

* The data would be equivalent to multiple database tables, with parent/child relationships between them, and will be loaded into a big data platform that supports parallel loads

* The data would be equivalent to a single database table in a database and will be used for two purposes:
  * The IT department will load it into a relational database
  * The business wants it in Excel on their desktop

* The data would be equivalent to multiple database tables, with parent/child relationships between them, and will be used for two purposes:
  * The IT department will load it into a relational database
  * The business wants it in Excel on their desktop

* The data would be equivalent to multiple database tables, with parent/child relationships between them, and will be used for three purposes:
  * The IT department will load it into a relational database
  * The IT department will load it into a big data platform that support parallel loads
  * The business wants it in Excel on their desktop

Come up with and discuss some simple best practices for requesting data files.

## Breakout 3 - Best practices for creating data files

As a full stack data scientist, you have created numerous beneficial analytical data and other IT groups, such as report writers, business intelligence analysts, etc. want the results of your work.  We learned in week 1 that this is called a "serving layer".

Putting on your data engineering hat, start with the list of best practices for requesting data files you created in breakout 2, and create a list of simple best practices for creating data files to be use in a serving layer.

## Breakout 4 - Benefits and dangers of Excel on the desktop

Anyone who has ever worked with the business side has heard the following comments numerous times:
* Can you put that in an Excel spreadsheet for me?
* I have that data, it's in an Excel spreadsheet?

The business side loves their Excel spreadsheets!  They have spent years learning and working with Excel in business school and at work.  It's very convenience for them to have all of their data in Excel spreadsheets on their desktop.

Discuss the benefits of Excel on the desktop.

Discuss the dangers and risks of Excel on the desktop.

A lot of companies try to lock down Excel by providing a system such as:
* An employee checks out an Excel file and it is copied to a special directory on their desktop (laptop)
* They work on the file on their desktop (laptop)
* When they are done, they check the file back in, and the system automatically deletes and wipes the Excel file from their desktop (laptop)
* Draconian messages of "YOU WILL BE FIRED IF YOU DON'T FOLLOW THIS PROCESS" are widely repeated in a million different ways to scare employees into using this system

These systems look and sound really good when presented with PowerPoint to executives, but in practice they rarely work. 

Discuss why these systems rarely work and how this directly impacts data science.
