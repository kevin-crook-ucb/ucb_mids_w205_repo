# Instructions for Labs for Week 02

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









