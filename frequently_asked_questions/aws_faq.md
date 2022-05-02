# Moved to bCourses - all of the content in this page has been moved to bCourses, and as of April 15, 2022, is no longer being updated.  Please use bCourses for the most recent, up to date version. This repo will be deleted once we are sure we have moved everything to bCourses correctly.

# Amazon Web Services (AWS) - FAQ - Frequently Asked Questions

## Why are we using the cloud in w205?

One of the major feedbacks we have received from industry is that MIDS graduates need to know at least the basics of the cloud.  Most data science work is done in the cloud.  We don't want someone to graduate from MIDS without knowing the basics of the cloud.

## Why are we using AWS in w205?

There is actually a master plan where different courses will use different cloud vendors.  This will give students exposure to different cloud vendors.  

AWS is used by capstone, so since w205 is a required course, this will ensure that students go into capstone ready to use AWS.   Capstone will assume knowledge of AWS and not have time to cover it.

AWS has AMIs (Amazon Machine Images) which allow the instructor to do 20 to 30 hours of setup work on Linux and create an AMI.  Students can create a virual machine (VM) from the AMI saving 20 to 30 hours of setup time.   The other cloud vendors don't have an image system that is even close to the functionality of AMIs.  Since this is most student's first exposure to any cloud, we are trying to make the initial exposure as easy as possible.

## Can't I just use my desktop for w205 and skip using AWS?

No.  

AWS is a required element for w205.

## Can I use another cloud vendor in place of AWS?

You must complete all labs and projects using AWS.  If you want to gain experience using another cloud vendor, you are welcome to try porting your labs and projects over and running them there.  However, instructors and TAs won't be able to use class time or office hours time supporting this.  You would need to do it on your own.

## Does AWS cost money?

Yes.  

Amazon is a for-profit business that charges money for AWS to make profits for their shareholders.

## Do students have to pay for AWS?  

Yes.  

Students are responsible for paying for their AWS usage.

## Will 2U pay for AWS?

No.  

Previously 2U had an arrangement to give students AWS credits through one of their partners, but that arrangement expired in Summer 2020.  The 2U representative for UC Berkeley has told us that 2U has no plans to offer students AWS credits in the future.

## Will UC Berkeley and/or iSchool pay for AWS?

No.  

Under federal and state regulations, lab fees, which include computer lab fees, must be separate from tuition.  AWS would fall in the category of computer lab fees.

## Will AWS give us student credits?

Instructors will request credits.  There is no guarantee that they will be granted.  So, students should be prepared to pay their AWS fees without credits.  Credits have typically run around $50 to $200 per student.

## Will instructors let us know as soon as credits come in?  Do I need to keep asking every day or two just in case?

Yes.

Instructors will let students know as soon as they come in and the last day to add has passed.  

No.

There is no need to keep asking instructors if they have come in yet.  

## Do you know exactly how much w205 AWS usage will cost?

No.  

AWS is billed by usage.  Some students spend much less time than others and have much lower bills.  Others spend much more time than others and have much higher bills.

## Do you have an estimate of how much w205 AWS uage will cost?

Based on January 2020 pricing, which is subject to change without notice:

* The VM's EBS storage is 100 GiB.  EBS is 8 cents per GiB per month.  So, $8 a month.

* When the VM is running (assuming 2 CPUs and 8 GiB RAM) it is 9 cents per hour.  If you run your VM 10 hours a week it would be less than $1 a week.

* Snapshots are stored in S3.  Most snapshots will be a few GiB. S3 is billed at 2 cents per GiB.  We recommend that you take a snapshot once a week and keep the last 3.  Most students will want to keep more.  It's a small price to pay for the safety of a backup so you don't lose your work.

## Can I use a smaller VM size to save money?

No.

We have tested the VM with different sizes.  The recommended size is the minimum size.  If you try a smaller size, some processes will run out of memory and risk corruption of your VM.  If your VM corrupts, you will lose everything and have to restore from the last snaphot. 

## Can I use a larger size VM?

Yes.

The recommended size is the absolute minimum.  You can always safely run a larger size.

## Can I use spot instances to save money?

No.

Spot instances are cheaper, but can be terminated at any time. If they are terminated, you will lose your VM and have to create a new one from the last snapshot.  

Spot instances are suitable for people running processes that are frequently saving state to a location external to the VM.  

## What is the free tier?  How much will it cover of what we will need for w205?

In terms of EBS and S3 allowances, it's worth less than $1 a month.

In terms of VM's, you can use a 1 CPU, 1 GiB VM for free.  

The w205 VM will use all of the EBS allowance.   After 1 or 2 snapshots, you will have used your S3 allowance.  The w205 VM won't run in the free VM allowance.

## What is the free 1 CPU, 1 GiB VM good for?

* Learning Linux command line, admin, etc.:  
  * Small VMs will work for this.  You could create a VM and learn without worrying about messing up.  If you mess up, just throw away the VM and get a new one.
  * Practice Troubleshooting Linux: Curriculums can have AMIs with issues.  The students would create a VM from the AMI, and then find and fix the problem.  Great way to learn to how fix real linux problems.
* Cryptography experiments: They don't need a lot of cpu or memory to run and you want to run trillions of cases and add the results to summary tables.  If you have some experiments that don't need a lot of memory nor cpu that you want to run for a long time, it's great.
* QC (quantum computing) experiments - QML (quantum machine learning experiments) - similar to cyptography experiments.  We may want to run trillions of trials.

## I received a message from AWS that I was over the free tier limit.  What does this mean?  Should I be worried?

Once you go over a free tier limit, AWS notifies you.  The notifications are sent out once a day or so, so it may take a while before you are notified.

When you create the w205 VM, you will go over the EBS limit and be notified.  When you create the first or second snapshot, you will be over the S3 limit and be notified.  Since notifications go out once a day or so, you may get both in the same notification.

You do not need to be worried about these messages.  They are normal.
