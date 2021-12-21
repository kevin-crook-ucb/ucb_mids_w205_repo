# How to Guide: Linux - Using SCP to transfer files between a Mac and the VM 

Video: https://kevincrook.com/ucb/mids/w205/how_to_guides/linux/07_linux_mac_scp_file_xfer.mp4

In AWS, get the Public DNS for your instance:

**AWS => N. Virginia => Services => Compute => EC2 => Instances => Instances => select instance => Connect => SSH Client => 4 click on copy icon to copy public DNS**

Open a Mac command line, and issue a command such as:

scp -i "xxx.pem" username@from_host:/remote/directory/file.txt username@to_host:/remote/directory/

Here is an example of copying a full backup file down to your laptop or desktop to the current directory:

scp -i "UCB.pem" w205@xxxxxx:/home/w205/backups/full/2021_12_20/w205_2021_12_20.tgz .

where xxxxx is your public DNS and . means current directory
 
 
