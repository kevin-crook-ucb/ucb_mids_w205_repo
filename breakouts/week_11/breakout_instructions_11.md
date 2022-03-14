# Instructions for Breakouts for Week 11

Several breakouts are provided each week. Generally there won't be time to get to all of them. Instructors will select which ones and in what order they would like to use for their class each week. Instructors may choose to do some breakouts at the whole class level instead of using breakout rooms. For breakouts that we don't get to in class, that you are interested in, you can always come to office hours and discuss with the instructor or TA.

## Breakout 1 - Designing a data science portfolio using Bootstrap and GitHub

For data science job hunting purposes, a data science portfolio is typically expected for cases where you don't have paid work experience.

If you already have paid work experience as a data scientist, you probably don't need a portfolio, as paid work experience is generally considered more relevant.  The exception to this might be if you haven't done something that a job you are applying for requires.  For example, if you haven't used Neo4j at work before, and the job you are applying for requires Neo4j, you might want to create examples of Neo4j for your portfolio.

For data science portfolios, students typically use two pieces:
* A single GitHub repo, well organized by subject matter into folders, Jupyter Notebooks, with a title and an executive summary of what skills the code cells are demonstrating, followed by code cells, output cells, markdown cells, etc.
* A website with contact information, information about you, a link to your resume, a link to your LinkedIn profile, and for each project in the GitHub repo, a title and a couple of sentences explaining with a link to the item in your repo

Some tips:
* Always make sure your Jupyter Notebook cells are executed with output displayed.  Make sure there are no stack traces.
* A website will allow non-technical HR people, managers, and business analysts who may be looking at your portfolio to understand it.  A GitHub repo without a website will be well above the knowledge level of non-programmers.
* For technical users, reading through an entire GitHub repo will probably be too time consuming, so having a website in front of it will make it much easier for them to see what projects they are interested in looking at.
* Make sure contact info is easy to find.  Once they decide they want to talk to you it should be really easy for them.
  * Consider a burner phone number and burner email that you use for job hunting. Publicly posting them will cause a lot of spam.
* Use a Responsive Web Design (RWD), such as Bootstrap, which is used by most websites.  It will look more professional.
* If you are not familiar with web design, and don't want to invest the time, considering hiring someone from one of the freelancer websites, or ask a local community college for students who are taking web design, or a local computer science department, etc.

In the labs, we saw that the bootstrap examples were loaded into our web server.  These same examples are also available at the following link:

https://getbootstrap.com/docs/5.1/examples/

Discuss a high level design for a data science portfolio website to put in front of a GitHub repo.  
* What components would you use?  
* What would type of things would you put in them?

There is one remaining issue: compliance with the Berkeley Honor Code for Academic Integrity, which forbids students from sharing or publicly posting solutions to homework, assignments, projects, exams, etc.   

How can students leverage their homework, assignments, projects, etc. from MIDS to build a data science portfolio without violating the Berkeley Honor Code?  Here are some suggestions:
* Create a separate GitHub repo just for your portfolio.  Name it something like data-science-portfolio.  If you are using a repo or repos with names from your courses, it can be taken that you are posting solutions.
* Rename files, especially Jupyter Notebooks to more generic names, such as neo4j_path_examples.ipynb
* Remove headers that specify it's for a course and replace with a title, your name, and an executive summary of all the skills you are demonstrating, removing all mentions that it was coursework.
* For datasets
  * If your instructor is using a public dataset that can be downloaded by anyone, that should be ok to use.
  * If your instructor is using a custom built dataset, then you should make some minor modifications to it.  Random number generators are good for this.
* For objective questions, with a right or wrong answer, make a small adjustment to the question, reword it, and adjust the answer.  Be sure and remove headers, problem numbers, etc.
* For subjective, open ended questions, since these are unique to you, make a small adjustment, rewording, etc. such that another student cannot wholesale copy it and use it.

Discuss any other suggestions for how you can leverage coursework without violating the Berkeley Honor Code.

Discuss how you can leverage the w205 curriculum for your data science portfolio.

## Breakout 2 - URLs

In the asynch and labs, we learned that a URL can have any or all of the following parts specified, and that there are rules for when we don't specify a part:
* protocol
* username
* password
* hostname (or IP address)
* port
* directory
* file
* parameters and values

For each of the following URLs, discuss for above parts, what part it is, if it has an explicit value, an implicit value, or no value:
```

https://google.com

http://google.com

https://user173283.compute1.amazonaws.com/user/data.json

https://35-171-163-28:7473

bolt://w205:iH8Liu3nP@35-171-163-28:7687

neo4j://neo4j:7687

https://35-171-163-28/user/bin/getstore

https://user173283.compute1.amazonaws.com/user/bin/getstore?store=3

https://user173283.compute1.amazonaws.com/user/bin/getsales?store=3&year=2021&month=11

https://w205:iH8Liu3nP@user173283.compute1.amazonaws.com:8888/user/mods/funct1?state=11&cursor=0&feedback=loop

file://35-171-163-28/home/w205/user/labs/week_11/web_server.ipynb

file:///home/w205/user/labs/week_11/web_server.ipynb

file://localhost/c:/WINDOWS/clock.json

file:///c:/WINDOWS/clock.json

```

## Breakout 3 - Static or dynamic

In the asynch and labs, we learned about the differences between static content and dynamic content, and that static content is much less intensive in terms of CPU and memory to serve.

Discuss for each of the following examples if it would be static or dynamic, or if it's dynamic and we can find a work around to make it static.  For each one, consider the case where it's public (no login needed) or private (login needed):

* HTML
* CSS
* Images
* Audio
* Video
* Javascript (client side scripts)
* JSON data not based on parameters
* JSON data based on parameters

## Breakout 4 - SQL or MongoDB

In the asynch and labs for this week, we used SQL and a relational database to create JSON for GET or POST calls with parameters.

In the asynch and labs for last week, we learned that MongoDB can be used in place of SQL relational tables to speed up queries that can be stored as key / value pairs with JSON as the value.

We typically start with SQL relational tables, and only move to MongoDB if we have to, or if we know we will have to. 

When a web API server retrieves from MongoDB, does it have to spend resources, CPU and memory, to create the JSON?

When a web API server returns JSON, where is the processing run to parse and extract the data from the JSON?

For each of the following examples, assume we are using SQL relational tables, and discuss if we should move to MongoDB or not:

* A website for a big box store
* An internal website at a small company with a few hundred employees
* An internal website at a large company with tens of thousands of employees
* A project for a course in MIDS 
* A startup company only has a few hundred customers, but made the cut to present on one of those TV shows where billionaire entrepreneurs who make investment offers to startups.
