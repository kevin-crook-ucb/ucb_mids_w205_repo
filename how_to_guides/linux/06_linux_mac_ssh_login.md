# Moved to bCourses - all of the content in this page has been moved to bCourses, and as of April 15, 2022, is no longer being updated.  Please use bCourses for the most recent, up to date version. This repo will be deleted once we are sure we have moved everything to bCourses correctly.

# How to Guide: Linux - Logging in using a SSH on a Mac Command Line

Video: https://kevincrook.com/ucb/mids/w205/how_to_guides/linux/06_linux_mac_ssh_login.mp4

In AWS, get the Public DNS for your instance:

**AWS => N. Virginia => Services => Compute => EC2 => Instances => Instances => select instance => Connect => SSH Client => 4 click on copy icon to copy public DNS**

Open a Mac command line, and issue a command such as:

 ssh -i "UCB.pem" w205@xxxxxxx
 
 where UCB.pem is the name of your key in pem format and xxxxx is your public DNS
 
 
