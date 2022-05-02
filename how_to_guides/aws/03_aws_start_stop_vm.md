# Moved to bCourses - all of the content in this page has been moved to bCourses, and as of April 15, 2022, is no longer being updated.  Please use bCourses for the most recent, up to date version. This repo will be deleted once we are sure we have moved everything to bCourses correctly.

# How to Guide: AWS - Starting and Stopping a VM

Video: https://kevincrook.com/ucb/mids/w205/how_to_guides/aws/03_aws_start_stop_vm.mp4

### Starting the VM

**AWS => N. Virginia => Services => Compute => EC2 => Instances => Instances => select instance => Instance State => Start Instance**

### Verify the VM is Running

**AWS => N. Virginia => Services => Compute => EC2 => Instances => Instances**

You should see your instance in the running state.

### Stopping the VM

First, make sure you have no Docker containers or clusters running.  If you stop the VM while a Docker container or cluster is running you might corrupt the mounted volumes.  For example, if the VM is stopped while Postgress is running, the Postgress mounted volume may corrupt and your database may be corrupted and unusable, and you will have to create a new database from scratch.

**AWS => N. Virginia => Services => Compute => EC2 => Instances => Instances => select instance => Instance State => Stop Instance**

**Suggestion:** since you have just stopped your VM, it's a great time to create a snapshot for a storage layer backup of your VM!
