# Moved to bCourses - all of the content in this page has been moved to bCourses, and as of April 15, 2022, is no longer being updated.  Please use bCourses for the most recent, up to date version. This repo will be deleted once we are sure we have moved everything to bCourses correctly.

# Connecting Browser to a Jupyter Notebook Server

## General checklist

* Double check that the VM is running.

* Double check that you are using the public IP address.  Remember that it can sometimes take a few minutes for the public IP address to be assigned.

* Double check that the VM has the correct security group.

* Double check that the security group has port 8888 in the inbound firewall rules.

* Double check the ULR and make sure it has port 8888 in it.  If it has 8889, 8890, 8891, etc. that means that you have already have a Jupyter Notebook server running.  Stop the JN server (or servers) that are not running on 8888.  Connect to the one running 8888.

* If possible, slack your URL to someone else and see if they can get in.  If they can get in, it means the issue is with your firewall:

  * Are you using a computer at work?  They may have blocked access to AWS or access to port 8888 in their firewall rules.  Check with your IT department to see if they will be willing to open access for you.
  
  * Do you have VPN software on your computer that you use to connect to work?  If so, the VPN may be blocking access to AWS or access to port 8888 in their firewall rules.  See if you can temporarily turn off the VPN while you are working in AWS.  This will usually work.  However, sometimes, the VPN may have a separate firewall software that is not turned off when the VPN is.

## Security Warnings

AWS is using self-signed security certificates.

These will generate warnings on browsers.  Different browsers have different messages.  Different versions of the same browser can have different messages.

The Chrome Mac version and the Chrome Windows version seem to give different messages with different procedures to bypass.

* The Chrome Windows version: Click the Advanced button and then click the proceed URL link.

* The Chrome Mac version:  simply type **thisisunsafe** on the keyboard.  It will not print on the screen.  

Jupyter Notebooks are developed and testing using Chrome.  That is why we are recommending Chrome for this course.  If you cannot get Chrome to work using the above methods, you can use another browser.

