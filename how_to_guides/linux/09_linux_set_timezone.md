# Moved to bCourses - all of the content in this page has been moved to bCourses, and as of April 15, 2022, is no longer being updated.  Please use bCourses for the most recent, up to date version. This repo will be deleted once we are sure we have moved everything to bCourses correctly.

# How to Guide: Linux - Setting the Local Time Zone in your VM

Video: https://kevincrook.com/ucb/mids/w205/how_to_guides/linux/09_linux_set_timezone.mp4

Amazon Linux puts everything in UTC with no local time zone set.  In the w205 AMI we set the local time zone to US Pacific.  If you are in another time zone and want to change your time zone, this will show you how.

See the current date and time:
```
date

```

See the current time zone:
```
timedatectl

```

Timezones use the tz database (in my humble opinion the most bizzare list of timezones ever created!):

https://en.wikipedia.org/wiki/List_of_tz_database_time_zones

See a list of time zones:
```
timedatectl list-timezones

```

Set a new timezone:
```
sudo timedatectl set-timezone America/Chicago

```

Set the timezone back to Pacific:
```
sudo timedatectl set-timezone America/Los_Angeles

```
