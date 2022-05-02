# Moved to bCourses - all of the content in this page has been moved to bCourses, and as of April 15, 2022, is no longer being updated.  Please use bCourses for the most recent, up to date version. This repo will be deleted once we are sure we have moved everything to bCourses correctly.

# Additionally - we are going to be making substantial changes to project 2 based on feedback from students from the Spring 2022 semester.  Please wait until the new version of this project is given before starting on it.

# Project 2 Instructions

## Labs 6 and 7

After completing lab 6, you will be able to get started on this project.  After completing lab 7, you will have everything you need to complete the project.  Use the labs as a guide as to how to complete the project.  When the instructions here don't specify something explicitely, always defer to the way it was shown in the labs. 

## Videos

**It is strongly recommended that you watch these videos to walk you through the project!**

* [Walkthrough of the Project](https://kevincrook.com/ucb/mids/w205/projects/project_2/project_2_01.mp4)
* GitHub Procedures
   * [Creating a private repo](https://kevincrook.com/ucb/mids/w205/projects/project_2/project_2_02.mp4)
   * [Putting a link to your repo in the Google form](https://kevincrook.com/ucb/mids/w205/projects/project_2/project_2_03.mp4)
   * [Cloning your repo to the VM, creating a branch, checking out the branch, downloading the Jupyter Notebooks](https://kevincrook.com/ucb/mids/w205/projects/project_2/project_2_04.mp4)
   * [Staging files, committing files, pushing files](https://kevincrook.com/ucb/mids/w205/projects/project_2/project_2_05.mp4) 
   * [Granting collaborator access to instructor and grading pool](https://kevincrook.com/ucb/mids/w205/projects/project_2/project_2_06.mp4)
   * [When you are finished, turn in the project by creating a pull request](https://kevincrook.com/ucb/mids/w205/projects/project_2/project_2_07.mp4)


## Introduction

Project 2 will be an individual project involving Data Wrangling to load sales data from a third party sales channel with some preliminary analytics on the loaded data.  

You will be working in Cloud, specifically in Amazon Web Services, in the official w205 VM, in a docker cluster running one container for Anaconda (Python distro) and one container for Postgres (SQL-based relational database).   You will be writing Python, Pandas, and SQL code in a Jupyter Notebook for your analysis and will be creating data visualizations to enhance your analytics.

## Additional Experience

In this project, you will gain additional experience with:
* GitHub on the Linux command line, including branches, pull requests, etc.
* SQL queries
* Functional programming using Python and SQL
* Linux command line
* Cloud (AWS)
* VM in the cloud instead of a physical computer
* Cluster of Docker containers running inside a VM in the cloud
* Enhancing a primary dataset with a secondary dataset
* Executive summaries

## New Skills

In this project, you will gain new skills:
* Design and create a mapping table to assist with integrating 3rd party IDs with primary database IDs
* Recursive walk through a nested JSON file to help understand the structure
* Parse a nested JSON files to produce CSV files with proper parent / child table linkeage
* Design and create staging tables that can accept dirty data from CSV files
* Load dirty data into staging tables from CSV files
* Validate data in staging tables 
* Validate data in staging tables matching against primary database tables 
* Validate data in staging tables matching against secondary database tables 
* Data exploration in staging tables
* Cleansing data in staging tables 
* Preliminary analytics from staging tables

## Business Case Scenario

Assume you are a full stack data scientist at Acme Gourmet Meals (AGM).

AGM executives are considering adding a delivery option, with the hopes of increasing sales, growing the customer base, and increasing profitability.   

Management decided to do a proof of concept (POC) in the form of a three month trial run using one delivery service at the Berkeley store.  

Management chose Peak Deliveries primarily because it's a newer operation with a model that takes a percentage cut of the product pricing instead of charging customers a delivery fee.  Peak's cut is 18 %. So, for each $ 12 meal, approximately $2.16. Customers may tip the delivery driver if they wish. AGM is not given any visibility into customer tips.  (Peak is protecting its data on good tippers.)  Peak has an outstanding reputation for great, fast, and efficient deliveries, with excellent customer service.  Peak will only deliver to zip codes within a 5 mile radius of the store.

Integration with any third party sales channel always comes with its challenges.  For large companies, like McDonalds, the delivery companies are willing to integrate and modify their computer systems as needed to get the contract.  For small companies, like AGM, our only option is to use Peak's API to send and receive data.  However, that would require us to write a lot of code, which management does not want to spend money on until the POC has proven successful. Peak can provide us with a JSON file at the end of each day with detailed sales information for that day.  Management has decided to go with the daily JSON option for now for the POC. 

For products, AGM will enter products into Peak's system.  Peak will assign an ID in their system to the product.  We will need to create a mapping table to map Peak's IDs to AGM's IDs.  In AGM's case all products cost $12 and are tax exempt.  AGM will mark them as exempt from sales tax.

Regarding the customer list, AGM does not want to give out their full customer list to third parties.  Customers will have to sign up with Peak, either using the website, the app, or by telephone.  Our executives anticipate and understand that the trade off to not giving them our customer list is that we will probably have to validate and/or cleanse the customer data.  Peak will assign their customer ID to each customer.

Regarding the store list.  In this POC we will only have 1 store and it will be the Berkeley store. Peak will create a pickup location for the store and assign their own location ID to it.  Even though all data will have the same store for now, we still want to receive it so we can plan for possible future expansion to other stores and/or pickup locations.

Assume today is the day after the first day of sales.  The first day of sales was October 3, 2020.  The JSON file came in very early this morning.  You need to get started with parsing, staging, validating, etc. the file as soon as possible.  The executives are very anxious to understand how dirty the customer data is going to be and also to get some preliminary analytics.

In part 2.1, you will be creating and loading the product mapping table (objective)

In part 2.2, you will be parsing Peak's sales JSON files into CSV files (objective)

In part 2.3, you will create and load staging tables (objective)

In part 2.4, you will validate data in the staging tables using SQL (objective)

In part 2.5, parts 2.5.1 through 2.5.3, you will run SQL queries to explore cleansing of the customer data (objective)

In part 2.5, part 2.5.4, you will write an executive summary on customer data, and recommend to the executives whether or not to give customer data to Peak (subjective)

In part 2.6, you will perform some preliminary analytics on data in the staging tables to answer specific questions from executives (objective)

In part 2.7, you will write an executive summary on what you feel is the most important aspect (or aspects) that you feel the executives would want to know (subjective)

Specific details for the above will be contained in the Jupyter Notebooks 

**Coding Guidelines**

You may freely use any code from the labs.  You do not have to cite code from the labs.

For the remainder of the code, you need to write your own.  

You are allowed to look at example code from other sources.  If it's a trivial snippet of code, that would be too small to rewrite, it's fine to use it.  If it's non-trivial code, you will need to rewrite the example code to make it your own.

You **MUST** code using functional programming using Python, Pandas, and SQL.  Review week 1 if you are unsure of what functional programming is.  It must be Python calling a module or package (API) for software running in Docker in your VM in AWS.

The code written for 205 should be considered prototype quality.  It does not have to be production quality code. The idea is that you are creating ad hoc analytics, and later whatever you want to keep, you will convert to production quality.  There are no set coding standards, as long as you code is reasonably readable. SQL queries should have some simple formatting, such as was done in the labs. You can code for the "happy path", assuming everything goes right.  You do NOT have to code exception conditions.  The idea is for you to focus more on the analytics rather than making code production quality.

## GitHub Procedures

**Create a private repo**

Note: this procedure only needs to be once.

The video will walk you through the process of creating a private repo.  The repo needs to be private to prevent other students from seeing your work. 

Please name your repo **ucb_mids_w205_project_2** so the grading scripts can download your repo correctly for grading.

**Enter a link to your repo into the Google form**

Note: this procedure only needs to be done once.

You will need to enter a link to your repo into a Google form.  This will allow us to run the grading scripts to pull your repo.  The video will walk you through this process.

[Google form to enter the link to your GitHub repo](https://forms.gle/Xy766NsF76MeY6K16)

**Clone you repo to the VM, create a branch, check out the branch, download the JSON file and Jupyter Notebooks**

Note: this procedure only needs to be done once.

The video will walk you through these processes.  Here are examples of the commands you will be using:

Change to the projects directory:
```
cd ~/user/projects

```

Clone the repo:
```
git clone xxxxx

```

Change to the repo directory:
```
cd ucb_mids_w205_project_2

```

Show the status of the repo.  You will use this command numerous times:
```
git status

```

Create a branch called **project**.  Please use this exact name so the autograding scripts can find your branch!
```
git branch project

```

Checkout the project branch:
```
git checkout project

```

Verify that you are on the project branch:
```
git status

```

Download the JSON file and starter Jupyter Notebooks:
```
curl -o peak_sales_2020_10_03.json https://raw.githubusercontent.com/kevin-crook-ucb/ucb_mids_w205_repo/main/projects/project_2/peak_sales_2020_10_03.json

curl -o project_2_1.ipynb https://raw.githubusercontent.com/kevin-crook-ucb/ucb_mids_w205_repo/main/projects/project_2/project_2_1.ipynb
curl -o project_2_2.ipynb https://raw.githubusercontent.com/kevin-crook-ucb/ucb_mids_w205_repo/main/projects/project_2/project_2_2.ipynb
curl -o project_2_3.ipynb https://raw.githubusercontent.com/kevin-crook-ucb/ucb_mids_w205_repo/main/projects/project_2/project_2_3.ipynb
curl -o project_2_4.ipynb https://raw.githubusercontent.com/kevin-crook-ucb/ucb_mids_w205_repo/main/projects/project_2/project_2_4.ipynb
curl -o project_2_5.ipynb https://raw.githubusercontent.com/kevin-crook-ucb/ucb_mids_w205_repo/main/projects/project_2/project_2_5.ipynb
curl -o project_2_6.ipynb https://raw.githubusercontent.com/kevin-crook-ucb/ucb_mids_w205_repo/main/projects/project_2/project_2_6.ipynb
curl -o project_2_7.ipynb https://raw.githubusercontent.com/kevin-crook-ucb/ucb_mids_w205_repo/main/projects/project_2/project_2_7.ipynb

```

Verify the Jupyter Notebooks downloaded correctly:
```
ls -l

```

Verify that the Jupyter Notebooks have been detected in the repo:
```
git status

```

**Stage files, commit files, push to GitHub**

Note: this procedure will be done numerous times.  Everytime you complete a logical unit of work, say every couple or hours, you will want to stage, commit, and push to save your work to GitHub.  Remember "stage, commit, and push: early and often".

The video will walk you through these processes.  Here are examples of the commands you will be using:

Do NOT stage any unnecessary files.  Follow the commands given below.  Do NOT do a "git add * " as it will add unnecessary files.  

Stage the JSON file and the Jupyter Notebooks:
```
git add peak_sales_2020_10_03.json

git add project_2_1.ipynb 
git add project_2_2.ipynb
git add project_2_3.ipynb
git add project_2_4.ipynb
git add project_2_5.ipynb
git add project_2_6.ipynb
git add project_2_7.ipynb

```

AFTER you are working on your project, you will need to check in the CSV files you create.  For now, you don't have these files, so these commands will not find the files that do not exist yet.  Once you have created these files, these commands will work:
```
git add peak_product_mapping.csv
git add peak_sales.csv
git add peak_stores.csv
git add peak_customers.csv
git add peak_line_items.csv

```

Verify the staging:
```
git status

```

Commit the staged files:
```
git commit -m "updates"

```

Verify the commit:
```
git status

```

Push the local commit on the branch up to GitHub.  Since it's a :
```
git push origin project

```

Using the GitHub web interface in your browser, verify the branch push worked and all files are present.

**Grant collaborator access to instructor and grading pool**

Note: this procedure only needs to be done once.

Grant collaborator access to your instructor and to the grading pool.  The instructor GitHub username and grading pool username will be provided in the datasci-205 slack channel.  The video will walk you through this process.

**When you are finished, turn in the project by creating a pull request**

Note: this procedure only needs to be done once.

The video will walk you through the process of creating a pull request that compares the project branch to the main branch with the grading pool as a reviewer.

## Docker and Jupyter Notebook Procedures

Follow the instructions for the lab for week 6: start the Docker cluster, start the Jupyter Notebook server in the Anaconda container, and connect the web browser to the Jupyter Notebook server.  Navigate to the project directory you cloned above and open the Jupyter Notebooks.  The Jupyter Notebooks include further specific instructions.

## Acknowledging Feedback

After you have received your grade and feedback from project 2, we want to make sure that every student has read their feedback. Often students make a mistake in project 2, get feedback on the mistake, don't read the feedback, and then make the same mistake on project 3. So 1% of your semester grade, separate in the gradebook from project 2, is acknowledging feedback from project 2. 

Acknowledge that you have read the feedback using this Google form:

[Google form to acknowledge feedback](https://forms.gle/T8sor8qosobTAMta6)

## Grading Rubrics

Semester Weighting
* Project 2
  * 29%
* Project 2 Feedback Acknowledgement
  * 1%

Late Submissions
* Submission time will the date and time the final pull request was created
* If a student forgot to create the pull request, but their last commit was before the due date and time, they will be allowed to create a pull request with a penality of -1 in lieu of the hours based late submission penalty
* 1 second late to 24 hours late: penalty -5
* 24 to 48 hours late: penalty -10
* 48 to 72 hours late: penalty -15
* 72 to 96 hours late: penalty -20
* No submissions will be accepted after 96 hours late

Objective 
* 80% 
* Right or wrong
* GitHub procedures
* CSV files
* Parts 2.1, 2.2, 2.3, 2.4, 2.5.1, 2.5.2, 2.5.3, 2.6

Subjective 
* 20% 
* Personal opinion
* Parts 2.5.4, 2.7

**Objective Items 80%**

GitHub procedures
* Maximum deduction for GitHub procedures: -3
* Did not name the repo the name given in proper case, penalty -1
* Did not name the branch the name given in proper case, penalty -1
* Altered the main branch, penalty -1
* Did not name the Jupyter Notebooks the names given in proper case, penalty -1
* Did not check in the peak_sales_2020_10_03.json file, penalty -1
* Non-essential files were checked in, such as checkpoint files and directories, penalty -1
* More than 1 open pull reqeust, penalty -1

CSV files
* peak_product_mapping.csv
* peak_sales.csv
* peak_stores.csv
* peak_customers.csv
* peak_line_items.csv

CSV File Rubrics
* File is checked in and correct in terms of format and/or data, but not named correctly, penalty -1
* File is checked in, but not correct in terms of format and/or data, penalty -2
* Did not check in the file, penalty -3

Parts 2.1, 2.2, 2.3, 2.4, 2.5.1, 2.5.2, 2.5.3, 2.6
* Provided an answer, but answer was wrong or partially wrong, penalty -1
* Did not provide an answer, penalty -2

**Subjective Items 20%**

Grader will evaluate the quality of the executive summaries for parts 2.5.4 and 2.7.

Here are the main scores and their criteria.  Grader may award scores in between if they feel a submission was in between.

Above 15/20 is very hard and very rare to achieve.

20/20
* Absolute perfection in all aspects
* Publication quality - similar to what would be published in an industry journal
* If reviewed by a data science team prior to presentation, no minor edits would be suggested
* Both executive summaries provided

17/20
* Excellence above and beyond
* Publication quality - similar to what would be published in an industry journal
* If reviewed by a data science team prior to presentation, no more than two minor edits would be suggested
* Both executive summaries provided

15/20
* Excellence above and beyond
* Publication quality - similar to what would be published in an industry journal
* If reviewed by a data science team prior to presentation, several minor edits would be suggested, but no major edits would be suggested
* Both executive summaries provided

13/20
* Excellent work
* Very high quality
* Very strong arguments
* If reviewed by a data science team prior to presentation, several minor edits would be suggested, but no more than one major edit would be suggested
* Both executive summaries provided

10/20
* High quality
* Very strong arguments
* Both executive summaries provided

7/20
* High quality
* Strong arguments
* At least one of the executive summaries provided

4/20
* Low quality
* Weak arguments
* At least one of the executive summaries provided

0/20
* No submissions for any of the executive summaries


