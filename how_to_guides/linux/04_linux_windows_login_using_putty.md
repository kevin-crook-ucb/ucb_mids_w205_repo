# How to Guide: Linux - Logging into your VM using PuTTY from Windows

Video: https://kevincrook.com/ucb/mids/w205/how_to_guides/linux/04_linux_windows_login_using_putty.mp4

In AWS, get the Public DNS for your instance:

**AWS => N. Virginia => Services => Compute => EC2 => Instances => Instances => select instance => Connect => SSH Client => 4 click on copy icon to copy public DNS**

Start PuTTY: Windows system menu => PuTTY (64-bit) => PuTTY

Host Name: w205@xxxxx 
where xxxxx is your public DNS

Left panel => SSH => Auth => Private key click the Browse button and find your private key 

Left panel => Session (very top you may have to scroll)

Saved Sessions: UCB_MIDS_w205

Save

Exit PuTTY => start PuTTY => UCB_MIDS_w205 => Load => Open

Should now be logged into your VM !

