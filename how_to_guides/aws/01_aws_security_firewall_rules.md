# How to Guide: AWS - Creating a Security Group and Adding Firewall Rules to the Security Group

Video: https://kevincrook.com/ucb/mids/w205/how_to_guides/aws/01_aws_security_firewall_rules.mp4

Every Virtual Machine (VM) in Amazon Web Services (AWS) is required to have a security group.  AWS has a default security group.  When you create (launch) a new VM, you can use the default security group, have it create a new security group, or use an existing security group.

It's best to first create a security group and add the firewall rules to the security group before we create our first VM.  All the VM's we create for w205 can use the same security group.  The instructions below will use the name **UCB_MIDS_w205_Security**.  You can use any name you want, however, if you use this name, all of our instructions will work as is.

## Create Security Group including Firewall Rules

**AWS => N. Virginia => Services => Compute => EC2 => Network & Security => Security Groups => Create New Security Group**

Security Group Name: UCB_MIDS_w205_Security

Description: UCB_MIDS_w205_Security

Inbound Rules: 

For all rules, we need to give a source IP address or address range or wildcards.  Here are a couple of common wildcards:
* 0.0.0.0/0 = wildcard for all IP addresses and subnets for IPv4 (IP version 4, the classic IP addresses)
* ::/0 = wildcard for all IP address and subnets for IPv6 (IP version 6, the new IP address scheme)

Here are the inbound rules we will need for the course.  For now, we will stick with IPv4.  (If you want to run IPv6, you will need to add the same rules for IPv6):

|IP Version|Type|Protocol|Port range|Source|Description|
|---|---|---|---|---|---|
|IPv4|SSH|TCP|22|0.0.0.0/0|SSH|
|IPv4|HTTPS|TCP|443|0.0.0.0/0|HTTPS|
|IPv4|Custom TCP|TCP|7473|0.0.0.0/0|Neo4j web interface using HTTPS|
|IPv4|Custom TCP|TCP|7687|0.0.0.0/0|Neo4j back end interface using Bolt|
|IPv4|HTTP|TCP|80|0.0.0.0/0|HTTP|
|IPv4|Custom TCP|TCP|8888|0.0.0.0/0|Jupyter Notebook server|

Outbound Rules: no changes needed

Tags: Key is Name, Value is UCB_MIDS_w205_Security

Click Create security group in lower right.

