# How to Guide: AWS - Create (Launch) a Virtual Machine (VM) from the w205 Amazon Machine Image (AMI)

Video: https://kevincrook.com/ucb/mids/w205/how_to_guides/aws/02_aws_create_vm.mp4

An AMI is an image that VMs can be created from.

An AMI has been created based on Amazon Linux with packages installed, configured, users created, groups created, directories created, ssh keys setup, etc.  AMIs save you the effort of starting with base Amazon Linux and going through many pages and hours to get it configured for w205.  

Amazon Linux is derived from CentOS which is the open source version of Red Hat Linux.  So, essentially we are using Red Hat Linux, which for professional server room use, is the dominant distribution.

If you are interested in creating the w205 VM from scratch instead of using the AMI, a how to guide is provided, but this is not recommended for beginners.  After the semester is over, or maybe later in the semester, you may want to go through that how to guide. 

Generally, you only need to create a VM once.  Once it is created, unless it get corrupted or damaged, you should not need to create another one. You will keep using the same VM, but start and stop it on an as needed basis (covered in another how to guide).  Whenever the VM is running, you are charged by the minute.  

## Create (launch) a new VM from the AMI

**Current AMI: UCB_MIDS_w205_AMI - ami-078244910baf8cbe6**

This may change as we fix issues with the AMI.  Always go by the current AMI in this document.  Always verify the ami number.  Anyone can create an AMI with the same name as mine.  The only way to verify is if the ami number matches!  Also, AMIs are local to a region, so make sure you are in N.Virginia or you won't find it!

**AWS => N. Virginia => Services => Compute => EC2 => Instances => Instances => Launch Instances => Launch Instances**

* **Step 1: Choose AMI** 

* **Step 2: Choose an Instance Type** - t2.large, 2 vCPUs, 8 GiB memory

* **Step 3: Configure Instance Details** - Check "Protect against accidental termination"

* **Step 4: Add Storage** 

* **Step 5: Add Tags** - Add: Key: Name Value: UCB_MIDS_w205_01 (change the 01 to 02, 03, 04, etc. if you already have w205 VMs)

* **Step 6: Configure Security Group** - Select the existing security group that we previously created: UCB_MIDS_w205_Security. It can be shared by all instances.

* **Step 7: Review Instance Launch** - Launch.   

**SSH Key Pairs** 

If you have an existing key pair that you want to use, you can certainly use it.  If you don't, you might want to create one called ucb or mids or w205.  You will want to save the private key to a place on your laptop where you will remember where it's at. You will need it to login to your VM.  If you loose it, you will lose access to your VM.  You may want to back it up to a external hard drive, Google gdrive, etc.  However, keep your private key private!  If someone gets access to your private key, they can login to your VMs and install and run malware, launch cyber attacks from your VM, etc.  

## Verify the VM is Running

**AWS => N. Virginia => Services => Compute => EC2 => Instances => Instances**

You should see your instance in the running state.  

## Always let a new VM run for at least 15 minutes (or longer) before stopping it - it has a lot of setup that runs when it is booted the first time

## Stop the VM

When you create a new VM, it is running.  

Whenever the VM is running you are charged by the minute.  If you are not going to use it until the next day or later, you may want to stop it to save billing.

There is a separate how to guide on starting and stopping the VM.

