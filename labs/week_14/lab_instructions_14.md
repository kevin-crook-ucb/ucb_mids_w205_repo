# Instructions for Labs for Week 14

## Starting and stopping the Docker Cluster for Anaconda and Postgres

Starting:
```
cd ~/docker/clusters/anaconda_postgres

docker-compose up -d

docker ps -a

```

Stopping:
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
