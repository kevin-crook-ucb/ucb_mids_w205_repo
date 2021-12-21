# How to Guide: Linux - Running a Backup

Video: https://kevincrook.com/ucb/mids/w205/how_to_guides/linux/08_linux_backup.mp4

## Backup Scripts

There is an alias created to run backups.  To see aliases:
```
alias

alias | grep backup

```

To see the scripts:
```
cd /home/w205/scripts

ls -l

```

To see the backups after they have run:
```
cd /home/w205/backups

ls -l 

cd /home/w205/backups/full

ls -l 

cd /home/w205/backups/partial

ls -l

```

## Full Backup

It is recommended that you make a full backup once a week and download it to your laptop or desktop. 

Full backups will be around 1 GiB, so weekly backups will start to add up on using disk space in your VM.  You may only want to keep 3 or so full backups and delete the oldest one when you get to 4.  Since you have copied it to your laptop, you have a safe copy elsewhere.

To run a full backup:
```
backup_full

```

## Partial Backup

Partial backups are automatically made every time you start your VM.  If you leave your VM running overnight, it will automatically make a partial backup at 2am Pacific time.

It is recommended that you periodically download the partial backups to your laptop or desktop.

Partial backups are very small.  They do not backup the data files that are used to load the databases and the actual database files, all of which are large.  Since they are so small, you can run them and keep them around without deleting them.  

When you finish a big piece of work, you should run a partial backup.  For example, say you have been working on your project for 3 hours and are at a stopping point, you should run a partial backup to be safe from losing your work.

To run a partial backup:
```
backup_partial

```
