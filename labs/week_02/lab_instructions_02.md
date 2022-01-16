# Instructions for Labs for Week 02

## Week 1's labs are prerequisite to Week 2's labs

If you did not work through the week 1 labs, the week 2 labs will NOT work. 

Week 2 needs all of the setup work done in week 1: creating the VM, starting and stopping the VM, connecting to the VM to get a Linux command line, making snapshots, making backups, downloading files, etc.   

## Watching videos, FAQs, Troubleshooting Guides, etc.

As we covered in week 1:

* The lab videos will walk you through these instructions and explain them as it goes.  Attempting to just read the instructions for the labs without watching the videos will not be sufficient.  You will need to actually watch the videos and work through the labs using the videos.

* Attempting to skip the concepts and business cases videos and skip directly to the labs will not be sufficient.  The labs assume that you have watched the concepts and business case videos.  They will reference these concepts and business cases, and if you are not familiar with them, the labs will not make much sense.

* Certain tasks that are highly repetitve in nature will be found in how_to_guides.  Each how to guide has a link to a video at the top that will walk you through the how to guide.  Attempting to just read the instructions for the how to guides without watching the videos will not be sufficient.  You will need to actually watch the videos and work through the how to guides using the videos.

* FAQ - remember to check the FAQs for frequently asked questions

* Troubleshooting Guides - remember to check the troubleshooting guides if you run into any issues


## Review the ERD

**GitHub => ucb_mids_w205_repo => labs => week_02 => sales_db_erd_data_dict.md**

## Starting and stopping the Docker cluster

We will be covering Docker and Docker Clusters in weeks 4 and 5, with details about what every command means, variations of commands, etc.

For now, we will just be giving you a few simple commands to start and stop our first cluster.  

Our first cluster will have two Docker Containers: one for Anaconda and one for Postgres.  We will use Anaconda to run Jupyter Notebooks against a Python 3.x kernel, which will connect to our Postgres container.

Open a linux command line to the virtual machine.

Each cluster has its own directory.  Change to the directory for this cluster:
```
cd ~/docker/clusters/anaconda_postgres
```

If you have already run through this before, or have paused, verify that the cluster is not already running:
```
docker ps -a
```

If your cluster is not running, start it with the following command:
```
docker-compose up -d
```

Verify it's running with the following command:
```
docker ps -a
```

As long as your VM is running, you can safely keep the Docker cluster running.  However, before stopping the VM, always shutdown all Docker clusters:
```
docker-compose down
```

Verify it's down with:
```
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









