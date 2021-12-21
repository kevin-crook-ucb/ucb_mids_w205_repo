# How to Guide: Linux - Logging in using a SSH on a Mac Command Line

Video: https://kevincrook.com/ucb/mids/w205/how_to_guides/linux/06_linux_mac_ssh_login.mp4

In AWS, get the Public DNS for your instance:

**AWS => N. Virginia => Services => Compute => EC2 => Instances => Instances => select instance => Connect => SSH Client => 4 click on copy icon to copy public DNS**

Open a Mac command line, and issue a command such as:

 ssh -i "UCB.pem" w205@xxxxxxx
 
 where UCB.pem is the name of your key in pem format and xxxxx is your public DNS
 
 
