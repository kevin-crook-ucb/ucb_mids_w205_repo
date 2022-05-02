# Moved to bCourses - all of the content in this page has been moved to bCourses, and as of April 15, 2022, is no longer being updated.  Please use bCourses for the most recent, up to date version. This repo will be deleted once we are sure we have moved everything to bCourses correctly.

# How to Guide: AWS - Create a Snapshot of a VM

Video: https://kevincrook.com/ucb/mids/w205/how_to_guides/aws/04_aws_vm_snapshot.mp4

A snapshot is a storage layer backup of your VM.

## Make absolutely sure your VM is stopped!

Before you create a snapshot, you need to make sure your VM has been stopped.  Linux uses buffered I/O which uses memory to cache parts of the file system, which makes it run much faster.  However, the trade off is that since part of the file system is in memory, the VM will need to be stopped so the cache is written to the storage layer before the snapshot is taken.

**AWS => N. Virginia => Services => Compute => EC2 => Instances => Instances**

Make sure the Instance State says Stopped.  If it is in progress, you will need to wait.  You may need to refresh the web page to get it to update the Instance State.

If it's running, please see the How to Guide: AWS - Starting and Stopping a VM

## Create a Snapshot of a VM

**AWS => N. Virginia => Services => Compute => EC2 => Elastic Block Store => Volumes => select volume => Actions => Create Snapshot**

Description: call it anything you like.  I like to put part of the instance name and the date so it's easy to find, such as w205_01_2021_12_20

Tags: Key: Name, Value: same name as above

## Wait until the snapshot is finished before starting the VM again

Wait until the snapshot is finished before starting the VM again, otherwise your snapshot will be no good!  You may need to refresh to see the updates.
