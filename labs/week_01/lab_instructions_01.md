# Instructions for Labs for Week 01

## Lab: VM Setup for this Course

This first lab will be atypical to most week's labs.  This lab will basically give you some "How To Guides" to go through.  Each "How To Guide" has its own video and instructions. 

### How To Guides for AWS (Amazon Web Services)

ucb_mids_w205_repo => how_to_guides => aws

Create a security group and set firewall rules for our virtual router for our virtual private cloud in Amazon Web Services
* 01_aws_security_filewall_rules.md

Create our VM (virtual machine) from the UCB MIDS w205 AMI (Amazon Machine Image)
* 02_aws_create_vm.md

How to start and stop our VM.  We are charged per minute while our VM is running:
* 03_aws_start_stop_vm.md

How to take a VM level backup called a snapshot:
* 04_aws_vm_snapshot.md

Optional: How to create your own VM from a snapshot (you may want to wait until later this semester and come back and do this one):
* 05_aws_ami_from_snapshot.md

### How To Guides for Linux

ucb_mids_w205_repo => how_to_guides => linux

#### For Windows Users:

PuTTY is a terminal emulator for Windows. How to download and install it:
* 01_linux_windows_putty_install.md

WinSCP is a file transfer and file editing program for Windows.  How to download and install it:
* 02_linux_windows_winscp_install.md

Private keys in pem format (used by AWS) need to be converted to Putty Key format, which is used for both PuTTY and WinSCP:
* 03_linux_windows_convert_key_putty.md

Login to Linux from Windows using PuTTY:
* 04_linux_windows_login_using_putty.md

Connect to Linux from Windows for file transfers and editing using WinSCP:
* 05_linux_windows_file_xfer_using_winscp.md

#### For Mac Users:

Connect to Linux from Mac using SSH login from the command line:
* 06_linux_mac_ssh_login.md

Transfer a file to / from Linux on the Mac using the command line:
* 07_linux_mac_scp_file_xfer.md

#### For All Users (both Windows and Mac):

Make Linux level backups (above we made VM level backups - we need both to be safe!):
* 08_linux_backup.md

Optional: The VM is set to Pacific time zone. If you want to set it to another time zone, here's how:
* 09_linux_set_timezone.md


