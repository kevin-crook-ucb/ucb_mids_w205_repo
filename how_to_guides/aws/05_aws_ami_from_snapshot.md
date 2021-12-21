# How to Guide: AWS - Creating an AMI from a Snapshot of a VM, then creating a new VM from the AMI

Video: https://kevincrook.com/ucb/mids/w205/how_to_guides/aws/05_aws_ami_from_snapshot.mp4

Hopefully this won't happen to you, but in case it does:

Let's say your VM won't boot.  Somehow either you accidentally damaged it, or it somehow became corrupted.  It's rare, but not impossible.  Out of several hundred students per semester, a few will have this happen to them.  Hopefully you will have taken our advice and taken frequent snapshots, so you have a snapshot to restore from.

Essentially, the procedures below allow you to create a new VM from the most recent snapshot if your current VM is damaged or corrupted.

## Create an AMI from the snapshot

**AWS => N. Virginia => Services => Compute => EC2 => Elastic Block Store => Snapshots => select snapshot => Actions => Create image from snapshot**

Wait until the creation of the AMI is completed!  You may need to refresh to see the updates.

## Create (launch) a new VM from the AMI you just created

**AWS => N. Virginia => Services => Compute => EC2 => Images => AMIs => select AMI => Actions => Launch**

* **Step 1: Choose AMI** - Select the AMI you just created

* **Step 2: Choose an Instance Type** - t2.large, 2 vCPUs, 8 GiB memory

* **Step 3: Configure Instance Details** - Check "Protect against accidental termination"

* **Step 4: Add Storage** 

* **Step 5: Add Tags** - Add: Key: Name Value: UCB_MIDS_w205_01 (change the 01 to 02, 03, 04, etc. if you already have w205 VMs)

* **Step 6: Configure Security Group** - Select the existing security group that we previously created: UCB_MIDS_w205_Security. It can be shared by all instances.

* **Step 7: Review Instance Launch** - Launch  

**SSH Key Pairs** 

If you have an existing key pair that you want to use, you can certainly use it.  If you don't, you might want to create one called ucb or mids or w205.  You will want to save the private key to a place on your laptop where you will remember where it's at. You will need it to login to your VM.  If you loose it, you will loose access to your VM.  You may want to back it up to a external hard drive, Google gdrive, etc.  However, keep your private key private!  If someone gets access to your private key, they can login to your VMs and install and run malware, launch cyber attacks from your VM, etc.  

## Verify the Instance is running

**AWS => N. Virginia => Services => Compute => EC2 => Instances => Instances**

You should see your instance in the running state.  
