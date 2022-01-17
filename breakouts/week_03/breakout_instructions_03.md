# Instructions for Breakouts for Week 03

Several breakouts are provided each week.  Generally there won't be time to get to all of them. Instructors will select which ones and in what order they would like to use for their class each week.  Instructors may choose to do some breakouts at the whole class level instead of using breakout rooms.  For breakouts that we don't get to in class, that you are interested in, you can always come to office hours and discuss with the instructor or TA. 

## Breakout 1 - Choosing which Linux distro to use

In the Asynch, we discussed how Linux is highly configurable, especially compared to other OSs, from small to huge, for example:
* A small, pared down version of Debian running on an IoT device without a GUI - just the absolute minimum.
* A desktop computer running Ubuntu with full GUI, optimized for desktop usage, and drivers for numerous devices: camera, headset, printer, etc.
* A server in a computer room, running Red Hat, "headless", with no GUI, optimized to run the server part of a huge application.

There are lots of Linux distros.  We discussed the major distros (major by market share):

* **Red Hat** - stable, large, corporate, server oriented, paid
    * **CentOS** - free version of Red Hat
        * **Amazon Linux** - CentOS optimized for AWS
        * **Oracle Linux** -CentOS optimized for Oracle
    * **Fedora** - experimental, new features of Red Hat tested
* **Debian** - stable, lean, mean
    * **Ubuntu** - Debian plus packages, drivers, desktop oriented
        * **Lubuntu** - pared down, old computers, desktop VMs
    * **Raspberry Pi OS** (formerly Raspbian) 
    * **IoT**

For each of the following scenarios, select what you think the best Linux distro to use would be. You can use one of the above, or another distro you are familiar with that we didn't cover:

* A startup company is provisioning a small server room.  They have just purchased new, top of the line, servers.  They just received a big round of VC (venture capital) funding and are flush with money.

* A startup company is provisioning a small server room.  They have just purchased new, top of the line, servers.  They received a small first round of VC, and after the server purchase, they are a bit strapped for money at present.

* A startup company is provisioning a small server room.  They have not received any VC money yet.  They bought servers that are 6 years old really cheap (they came off of their second 3 year corporate lease).  

* You have a PC that is only a couple of years old and you want to run Linux on the desktop.

* You have a PC that is 8 years old and too slow for Windows latest release.  You want to run Linux and use it for family members to surf the web and connect it to a TV and watch videos, steam music, etc.  Or maybe donate it to charity.

* You have a PC that is 8 years old and too slow for Windows latest release.  You want to run Linux and use it as a server to run AI, ML, DL, etc. experiments on.

* You have a PC that is only a couple of years old and you want to run VM Ware on top of Windows and run Linux on top of that.

* You are a Linux guru.  You want the latest and greatest Beta releases of everything a year or two before it makes it to Red Hat, Debian, Ubuntu, etc.  

* A startup company is developing an IoT device with an ARM processor.  It has very small RAM and SSD internal to the device.  You need to run Linux on the ARM processor.

* A startup company has a new AI model for a very specific industry that is ready for Beta release.  They want to ship it using a container image.  What Linux should they use for the container image.  (We will cover containers next week.  For now, just assume that containers need a small, lean, mean Linux similar to an IoT device.)

* You are setting up an Oracle server.

* You are creating a VM in AWS.

## Breakout 2 - Types of backups and importance of backups

During week 1's labs, you were introduced to 3 types of backups for Linux.  During this week's labs, you were shown the source code for the full and partial Linux level backups:
* Snapshots
   * Storage layer backup at the VM level
   * Recommended to make at least once per week
   * Recommended to keep at least the last 3
   * Can delete old ones to save space
   * VM must NOT be running while the snaphot is running
* Full backup 
   * Backup of the w205 directory into a versioned tar ball file
   * Run from the Linux command line
   * Recommended to make at least once per week
   * Recommended to keep at least the last 3
   * Can be large (up to 1 GiB)
   * Recommended to copy down to your laptop, desktop, etc.
* Partial backup 
   * Backup of the files you are most likely to change: Jupyter Notebooks, Dockerfiles, docker-compose.yml, etc.
   * Versioned tar ball file
   * Run from the Linux command line
   * Automatically made when you start your VM (crontab)
   * Automatically made at 2am Pacific if you leave your VM running overnight (crontab)
   * Can manually run anytime
   * Small, a few MiB 
   * Recommended to copy down to your laptop, desktop, etc.

In addition to backups, as you learned in the Python prerequisite course, every time you stage, commit, and push to GitHub, a copy of your repo is saved in GitHub and can be cloned down later, serving as another type of backup.

Backups are extremely important.  Consider the following scenarios. Assume that you are making the backups as recommended, and that you are regularly pushing to GitHub.  What course of action would you take?  How much work would you lose?  Are the answers the same for each or close for each?

* You tried to start your VM and it will not start and receives boot errors.

* You used a AWS spot instance to save money.  AWS gives spot instances at low cost with the right to terminate at any time.  AWS terminates your spot instance.

* You skipped the step to turn on termination protection for your VM when creating it.  You were trying to stop it, and accidentally chose terminate instead of stop.

* You made a major typo in a Linux command and deleted a bunch of Jupyter Notebooks for your latest project.

* You forgot to shutdown the Docker cluster running a database before stopping the VM.  The database is corrupted.


## Breakout 3 - Space management of your VM

In the week 3 labs, we saw the command:

```
df -h

```
Which produces output similar to:
```
Filesystem      Size  Used Avail Use% Mounted on
devtmpfs        3.9G     0  3.9G   0% /dev
tmpfs           3.9G     0  3.9G   0% /dev/shm
tmpfs           3.9G  492K  3.9G   1% /run
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/xvda1      100G   19G   82G  19% /
tmpfs           798M     0  798M   0% /run/user/1001

```

In the week 3 labs, we also saw a Python program that can help with space management:

```
cd ~/scripts

sudo ./walk_directory_tree.py

```
Which will show you the options below:
```
walk_directory_tree.py

usage: walk_directory_tree directory option
option 1: print directories in alphabetical order
option 2: print directories and sizes sorted ascending
option 3: print directories and sizes sorted descending
option 4: print files in alphabetical order
option 5: print files and sizes sorted ascending
option 6: print files and sizes sorted descending

```

Discuss as a group how you can use these two tools to help with space management and design a simple space management plan for your VM for this semester.  Include the following in your discussion:
* How much storage space is in the VM above?
* How much storage space has the VM above used: in GiB?  percent?
* Why do we have to run the walk_directory_tree.py program using sudo?

## Breakout 4 - Project 1 - Holiday Analytics Ideas

For the Project 1 Holiday Analytics, discuss some ideas you are looking at.

## Breakout 5 - Project 1 - Best Customer Analytics Ideas

For the Project 1 Best Customer Analytics, discuss some ideas you are looking at.

## Breakout 6 - Project 1 - Best Recommendation

For the Project 1 Best Recommendation, discuss some ideas you are looking at.
