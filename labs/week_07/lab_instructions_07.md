# Moved to bCourses - all of the content in this page has been moved to bCourses, and as of April 15, 2022, is no longer being updated.  Please use bCourses for the most recent, up to date version. This repo will be deleted once we are sure we have moved everything to bCourses correctly.

# Instructions for Labs for Week 07

## Starting and stopping the Docker cluster

We will use the same Anaconda and Postgres cluster for both weeks of Data Wrangling.

Open a linux command line to the virtual machine.

Change to the directory for this cluster, start the cluster, and verify that it's up:
```
cd ~/docker/clusters/anaconda_postgres

docker-compose up -d

docker ps -a

```

Remember to stop the docker cluster and verify it's down before stopping the VM:
```
docker-compose down

docker ps -a

```

## Find the external IP address of your virtual machine in Amazon Web Services:

**AWS => N. Virginia => Services => Compute => EC2 => Instances => Instances => select instance => Connect => EC2 Instance Connect => Public IP address**

If you are using Windows, copy it to notepad.

If you are using Mac, copy it to TextMate.  It is available to Berkeley students for free:
https://software.berkeley.edu/textmate

## Start a Jupyter Notebook server in the Anaconda container:

```
docker-compose exec anaconda jupyter notebook --notebook-dir=/user --ip='*' --port=8888 --no-browser --allow-root
```

Pull out the URL, copy and paste it to notepad (Windows) or TextMate (Mac).   Change the IP address.  Open an incognito Chrome browser and paste it in.  

## Now you can open the Jupyter Notebooks needed for this lab!

## Remember to shutdown the Docker cluster before stopping the VM!

### Here is a list of staging tables:

**stage 1 tables are all varchar(100) data types so bad data can be loaded:**

* stage_1_customers
* stage_1_sales
* stage_1_line_items

**stage 2 tables have the actual data types and only data with the correct data type can be copied from stage 1 tables:**

* stage_2_customers
* stage_2_sales
* stage_2_line_items

**stage 3 tables have dirty data so we can learn to detect and clean it:**

* stage_3_customers
* stage_3_sales
* stage_3_line_items

### Here is a list of files:

* temp_sales_nested.json
* temp_customers_nested.json
* temp_customers_nested_2.json

**clean data in the clean_date directory:**

* clean_customers.csv loads into table stage_1_customers
* clean_sales.csv loads into table stage_1_sales
* clean_line_items.csv loads into table state_1_line_items

**dirty data in the dirty_date directory:**

* dirty_customers loads into table stage_3_customers
* dirty_sales loads into table stage_3_sales
* dirty_line_items loads into table stage_3_line_items
