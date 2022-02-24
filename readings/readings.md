# Readings for UC Berkeley, MIDS, w205 - Fundamentals of Data Engineering

Right now, we have not been able to find suitable readings for this course.  The challenge is that most reading for topics included in this course are at an undergraduate upper division computer science level.  They assume students are well versed in all the computer science terminology and theory. Most academic papers assume graduate level computer science knowledge and are highly theoretical.

We are currently exploring industry white papers to see if there are any suitable papers there.

## Optional suggested reading for students who want to learn more about the topics covered in this course

Reminder: this is 100% optional.  It is NOT required!

Some students have asked for suggested readings to learn more about the topics covered in this course.  

For books, some are available online from the Berkeley library.  If you need help to find them in the Berkeley library website, please open a ticket on the library website.  They are in the best position to help you with library questions and issues.  They will obviously know a lot more of what is available in the Berkeley library and how to access it than the w205 instructors or TAs will know.

https://www.lib.berkeley.edu/

Some of these books are occasionally offered as a free download from the vendor websites.  Please check with the vendor websites for more information.  

#### Anaconda
* Online documentation: https://docs.anaconda.com/

#### Python, Pandas, NumPy
* Book: McKinney, Python for Data Analysis 
  * Check for latest edition

#### Data modeling a database in third normal form (3NF)
* Book: Hoberman, Data Modeling Made Simple, A Practical Guide for Business and IT Professionals 
  * Check for latest edition
  * There are also specific editions for specific tools such as ERWin

#### SQL
* Online tutorial: https://www.w3schools.com/sql/
  * Free, codepen style, no need to install database, you can run all SQL right in the browser

#### PostgreSQL
* Online tutorial: https://www.postgresqltutorial.com/
* Book: Obe, PostgreSQL Up & Running 
  * Check for latest edition
  * Hasn't been updated in a while as of this writing

#### Linux Command Line
This is focused on how to use Linux on the command line.  It does not focus on Linux system admin tasks, which frankly, most data scientist will not need to know, unless they are working at a small startup, a small company, or a small research lab that cannot afford a Linux system admin, or doesn't have enough work for a Linux system admin, etc.
* Online tutorial: https://linuxcommand.org/
* Book: Sobell, Practicle Guide to Linux Commands, Editors, and Shell Programming 
  * Check for latest edition

#### Linux System Administration
This is generally not recommended for most students, but some have asked me for it.  If you want to be a Linux system admin, or know someone who does, Red Hat certification is generally the best path.  Other than wanting to become a Linux system admin, the other use for this knowledge would be a case such as a small startup, a small company, or a small research lab that cannot afford a Linux system admin, or doesn't have enough work for a Linux system admin, etc.
* Red Hat
  * Server oriented
  * CentOS - open source version
  * Amazon Linux - derived from CentOS
  * Online documentation: https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8
  * Book: Jang, RHCSA/RHCE Red Hat Enterprise Linux 8 Certification Study Guide  
    * New edition Summer 2022
    * I've taught corporate training, community college, and high school dual credit using older editions of this book.  It's geared towards the Red Hat certification.
* Ubuntu Linux
  * Desktop oriented
  * Derived from Debian, so some of the admin will be different from Red Hat
  * Online documentation: 
  * Book: Helmke, Ubuntu Linux UNLEASED 
    * 2021 edition
    * This seems to be the only Ubuntu book that has been updated in years. Since Ubuntu is so desktop oriented, there is a very small admin market for books.

#### git and GitHub 
Remember git runs on the Linux command line.  GitHub is a web based managed service that runs on top of git.
* git command line documentation and free online book: https://git-scm.com/
* GitHub online documentation: https://docs.github.com/en

#### Docker
* Online documentation: https://docs.docker.com/
* Book: Kane, Docker Up & Running: Shipping Reliable Containers in Production 
  * Check for latest edition

#### Neo4j
* Cypher query language
  * Online documentation: https://neo4j.com/docs/cypher-manual/current/
  * Book: Robinson, Graph Databases: New Opportunities for Connected Data
    * Check for latest edition
* Graph Data Science (gds) algorithms
  * Online documentation: https://neo4j.com/docs/graph-data-science/current/algorithms/
  * Book: Needham, Graph Algorithms: Practical Examples in Apache Spark and Neo4j 
    * Check for latest edition
    * Note that it covers Spark in addition to Neo4j and gives most examples in both products

#### MongoDB
* Tutorial online: https://docs.mongodb.com/manual/tutorial/getting-started/
* Book: Bradshaw, MongoDB: the Definitive Guide: Powerful and Scalable Data Storage
  * Check for latest edition
* Data modeling book: Hoberman, Data Modeling for MongoDB: Building Well-Designed and Supportable MongoDB Databases 
  * Check for latest edition
  * This seems to be a few years old, but the general concepts of modeling a document database that uses JSON-like documents still applies
  * As far as I know, it's the only data modeling book ever written for any NoSQL Document database from any vendor

#### Redis
* Online documentation: https://redis.io/documentation
* Book: Macedo, Redis Cookbook: Practical Techniques for Fast Data Manipulation
  * Check for latest edition
  * Several years old, but not that many Redis books out there

#### Flask
* Online documentation: https://flask.palletsprojects.com/en/2.0.x/
* Book: Grinberg, Flask Web Development: Developing Web Applications with Python
  * Check for latest edition

#### Green Unicorn
* Online documentation: https://gunicorn.org/#docs

#### NGINX ("engine X") 
* Online documentation (admin): https://docs.nginx.com/nginx/admin-guide/
  * Unless you are wanting to be a web server admin, you will probably only need the very basics of custom configuration similar to what we did in w205.  The online documentation should suffice for this.
* Book (admin): Dejonghe, NGINX Cookbook: Advanced Recipes for High-Performance Load Balancing
  * Just came out, 1st edition
  * This would be if you are trying to put a web server in production, which I'm guessing most data scientists won't do.

#### Kafka
* Online documentation: https://kafka.apache.org/documentation/
* Book: Shapira, Kafka, The Definitive Guide: Real-Time Data and Stream Processing at Scale
  * Check for latest edition

#### Data Lakes and Data Lakehouses
Not really any good options here.  Most books are several years old and data lakes have changed a lot in the last couple of years.  The new books are very vendor specific, and there isn't a clear dominant player in the data lakes / data lakehouse market, unlike most of the other technologies above where there is a clear winner.


