# Moved to bCourses - all of the content in this page has been moved to bCourses, and as of April 15, 2022, is no longer being updated.  Please use bCourses for the most recent, up to date version. This repo will be deleted once we are sure we have moved everything to bCourses correctly.

# Mac SSH troubleshooting guide

**Replace**
* xxxx.pem with the name of your pem file.  
* dddd with your public DNS name.

## Warning: Identity file xxxx.pem not accessible: No such file or directory.

You are probably running ssh in a directory where you xxxx.pem file is not located.  Either copy the xxxx.pem file to your directory, or change to the directory where the xxxx.pem file is located.

## ssh: Could not resolve hostname dddd: Name or service not known

Verify that you are using the public DNS name and not the private DNS name.

Sometimes it takes a few minutes for the public DNS name to come up.  It will show you the private DNS name until a public DNS name is available. 

Verify that the VM is running.


## The authenticity of host 'ec2-18-215-166-145.compute-1.amazonaws.com (172.31.5.8)' can't be established.

Here is the full error message:
```
The authenticity of host 'ec2-18-215-166-145.compute-1.amazonaws.com (172.31.5.8)' can't be established.
ECDSA key fingerprint is SHA256:GlUU8C/ps3Z4k1EeFIgzQESyou4Vhpb9xvjSFTa1uZE.
ECDSA key fingerprint is MD5:cc:cb:ee:a1:42:27:49:11:2e:7e:a8:09:44:06:14:4d.
Are you sure you want to continue connecting (yes/no)? 

```

AWS is using a self signed certificate for ssh.  The message above is normal.  You should type `yes` and hit enter.

## WARNING: UNPROTECTED PRIVATE KEY FILE!

```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0664 for 'xxxx.pem' are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
Load key "xxxx.pem": bad permissions
Permission denied (publickey,gssapi-keyex,gssapi-with-mic).
 
 ```
 
 The Mac requires permissions to be set to 400 for all private key files.  Use the following command to change permissions:
 
 ```
 chmod 400 xxxx.pem
 
 ```
 
