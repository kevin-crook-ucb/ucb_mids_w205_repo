# Moved to bCourses - all of the content in this page has been moved to bCourses, and as of April 15, 2022, is no longer being updated.  Please use bCourses for the most recent, up to date version. This repo will be deleted once we are sure we have moved everything to bCourses correctly.

# Instructions for Labs for Week 06

## Starting and stopping the Docker cluster

Now that we have covered docker clusters, how to start and stop them, how to check for and cleanup stray containers, etc., we  will just provide the cluster start and stop commands from now on.

We will use the same Anaconda and Postgres cluster for both weeks of Data Wrangling.

Open a linux command line to the virtual machine.

Each cluster has its own directory.  Change to the directory for this cluster, start the cluster, and verify that it's up:
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

### Since we have a lot of files for this week's labs, here is a list of files:

* berkeley_logo.png - image file that we read in to encode in base 64

**temp subset of the sales data for a random subset of sales:**
* temp_random_sales.csv - loads into temp_random_sales table
* temp_stores.csv - loads into temp_stores table
* temp_sales.csv - loads into temp_sales table
* temp_line_items.csv - loads into temp_line_items table
* temp_customers.csv - loads into temp_customers table
* temp_products.csv - loads into temp_products table
* temp_holidays.csv - loads into temp_holidays table

**extractions of the temp tables (should match the above csv files):**
* temp_random_sales_2.csv - extracted from temp_random_sales table
* temp_stores_2.csv - extracted from  temp_stores table
* temp_sales_2.csv - extracted from temp_sales table
* temp_line_items_2.csv - extracted from temp_line_items table
* temp_customers_2.csv - extracted from temp_customers table
* temp_products_2.csv - extracted from temp_products table
* temp_holidays_2.csv - extracted from temp_holidays table

**flat json files from the temp tables:**

* temp_stores
    * temp_stores_no_header.json
    * temp_stores_header.json
    * temp_stores_big_data.json
* temp_sales
    * temp_sales_no_header.json
    * temp_sales_header.json
    * temp_sales_big_data.json
* temp_line_items
    * temp_line_items_no_header.json
    * temp_line_items_header.json
    * temp_line_items_big_data.json
* temp_customers
    * temp_customers_no_header.json
    * temp_customers_header.json
    * temp_customers_big_data.json
* temp_products
    * temp_products_no_header.json
    * temp_products_header.json
    * temp_products_big_data.json
* temp_holidays
    * temp_holidays_no_header.json
    * temp_holidays_header.json
    * temp_holidays_big_data.json

**csv files created from the corresponding flat json files (for each table, the csv files should match):**

* temp_stores
    * temp_stores_no_header.csv
    * temp_stores_header.csv
    * temp_stores_big_date.csv
* temp_sales
    * temp_sales_no_header.csv
    * temp_sales_header.csv
    * temp_sales_big_data.csv
* temp_line_items
    * temp_line_items_no_header.csv
    * temp_line_items_header.csv
    * temp_line_items_big_data.csv
* temp_customers
    * temp_customers_no_header.csv
    * temp_customers_header.csv
    * temp_customers_big_data.csv
* temp_products
    * temp_products_no_header.csv
    * temp_products_header.csv
    * temp_products_big_data.csv
* temp_holidays
    * temp_holidays_no_header.csv
    * temp_holidays_header.csv
    * temp_holidays_big_data.csv

**extracted flat json files from the temp tables (should match the previous json files, except for the filename and timestamp in the headers):**

* temp_stores
    * temp_stores_no_header_2.json
    * temp_stores_header_2.json
    * temp_stores_big_date_2.json
* temp_sales
    * temp_sales_no_header_2.json
    * temp_sales_header_2.json
    * temp_sales_big_data_2.json
* temp_line_items
    * temp_line_items_no_header_2.json
    * temp_line_items_header_2.json
    * temp_line_items_big_data_2.json
* temp_customers
    * temp_customers_no_header_2.json
    * temp_customers_header_2.json
    * temp_customers_big_data_2.json
* temp_products
    * temp_products_no_header_2.json
    * temp_products_header_2.json
    * temp_products_big_data_2.json
* temp_holidays
    * temp_holidays_no_header_2.json
    * temp_holidays_header_2.json
    * temp_holidays_big_data_2.json

**extracted nested json files from the temp tables:**

* temp_stores_nested.json
* temp_sales_nested.json
* temp_customers_nested.json

**extracted csv files from the temp_stores_nested.json file:**

* temp_stores_3.csv
* temp_customers_3.csv
* temp_sales_3.csv
* temp_line_items_3.csv
* temp_products_3.csv

**extracted nested json files from the temp tables, should match the previous:**

* temp_stores_nested_2.json - should match temp_stores_nested.json

**extracted Excel Workbook from temp tables:**

* temp_sale_report.xlsx

**extracted csv files from the Excel Workbook:**

* temp_sales_report_excel.csv
* temp_stores_excel.csv
* temp_customers_excel.csv
* temp_sales_excel.csv
* temp_line_items_excel.csv
* temp_products_excel.csv
* temp_holidays_excel.csv

**extracted Excel Workbook from the temp tables (should match temp_sales_report.xlsx):**

* temp_sales_report_2.xlsx
