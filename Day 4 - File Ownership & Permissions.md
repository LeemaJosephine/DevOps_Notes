#Day 4 -File Ownership & Permissions

Every file/directory in linux has 3 ownership attributes

**Owner (User)**

- The person who created the file
- Has primary control

**Group**

- A set of users
- Group members can share access

**Others**

- Everyone else on system

**Check ownership using:**

```
▪ ls -l
```
**Mini Exercise**

**Exercise 1: Check ownership and permissions**

echo “this is a test file” >> file.txt

ls -l

**Output:**

- Owner
- Group
- Permission String

**Exercise 2: Change Permission**

**Goal:**

Give

- Owner: read+ write+ execute
- Group: read
- Others: no access

**Solution:**

**Exercise 3: Symbolic method**

**Goal:**

```
▪ Add execute permission to user
▪ Remove read from others
```
**Solution:**

**Exercise 4: Real DevOps Scenario**

**Create script:**

vim deploy.sh

**Save and run**

./deploy.sh

chmod +x deploy.sh

Linux File System

Linux follows a hierarchical structure (tree-like) starting from

/ # root(/) is the top most directory everything lives under it

Linux Directory Structure

/ (Root)

Base of everything

/home

User personal directory

Example: /home/ubuntu

/root

Home directory of root user (admin)

/bin

Essential commands

Example: ls, cp, mv

/sbin

System admin commands

Example: reboot, shutdown

/etc

Configuration files

Example: passwd, ssh, config

/var

Variables data (logs, cache)

Example: /var/log

/tmp

Temporary files (auto deleted)

/usr

User-installed software and libraries

/dev

Device files (hardware like disk, USB)

/proc

Virtual filesystems (system/process info)

/mnt & /media

Mount external drives

/boot

The folder that helps your system turn ON and load linux

**Navigation Commands**

pwd # current directory

ls # list files

cd /path # change directory

cd .. # go back

cd ~ # go to home

**Mini Exercises**

**Exercise 1: Explore Root Structure**

**Steps:**

cd /

ls -l

**Exercise 2: Navigate user directory**

cd /home

ls -l

cd ~

pwd

**Exercise 3: Create your own structure**

**Goal:** Create project folder structure

myproject (code, logs, data)

**Exercise 4: Create files in different directory**

touch myproject/code/app.txt

touch myproject/logs/app.log

touch myproject/data/input.txt

**Note: tree command in linux is used to display the directory structure in a
hierarchical (tree-like) structure**

**Installation instructions:**

sudo apt update

sudo apt install -y tree

**Additional Pointers**

**Everything is a file**

Almost everything is treated as file: even hardware, processes and system info

Examples

```
Type Example Meaning
Regular file file.txt Normal data
Directory /home Folder
Device /dev/sda Hard disk
Process info /proc/cpuinfo CPU Details
```
**Absolute vs Relative Path**

**Absolute path**

Full path from root /

/home/ubuntu/file.txt

**Relative path**

Path based on current location

file.txt

../file.txt

```
Symbol Meaning
```
. current directory
.. parent directory
~ home directory

**Hidden files**

Files starting with. are hidden

Example:

.gitignore

.ssh

**Real Use**

Store configs

Keep system files clean

Cron Job

**What is a Cron Job?**

A cron job is used to schedule tasks automatically in Linux

**Windows Comparison**

**Linux Windows**

Cron job Task schedular

Crontab Scheduled Tasks UI

**Cron System Components**

**Key parts:**

```
▪ cron daemon (crond): runs in background
▪ crontab file: store scheduled jobs
▪ command/script: What you want to run
```
**Crontab Syntax**

**Examples:**

```
Schedule Meaning
* * * * * every minute
0 * * * * every hour
0 0 * * * daily at midnight
0 9 * * 1 every Monday 9 AM
```
**Basic Commands**

crontab -e # edit cron jobs

crontab -l # list jobs

crontab -r # remove all jobs

**Exercise 1: Run command every minute**

**Step 1:** crontab - e (# It will ask you to choose editor)

**Troubleshooting:**

If not getting the output, follow below steps

```
▪ Check if cron service is running or not
sudo systemctl status cron
```
Check cron logs

sudo grep CRON /var/log/syslog

List the jobs

crontab -l

**Exercise 2: Runs Every 5 minutes**

***/5 * * * * echo “Hello Again” >> /home/ubuntu/cron.txt**

**Exercise 3: Runs at 5th minute of every hour**

**5 * * * * echo “Hello Again” >> /home/ubuntu/cron.txt**

**Exercise 4: Run Script every minute**

Security and System Administration

**What is Linux Security?**

Protecting system, data and users from unauthorized access

**Key Pillars**

Authentication (who are you?)

Authorization (what can you do?)

Auditing (what did you do?)

**User and Group Management**

```
▪ Create user
▪ Set password
▪ Create group
▪ Add user to group
```
**File Permissions and Ownership**

```
▪ Secure application files
▪ Restrict access to configs
```
**Sudo (Superuser Access)**

sudo allows run commands as admin(root)

**SSH (Secure Remote access)**

SSH is used to connect to remote servers securely

**Firewalls (System Protection**

Firewall controls incoming/outgoing traffic

**Process Management**

```
▪ Process = running programs
ps aux # view all processes (shows snapshot of all running
processes)
top # Live process monitor
kill <pid> # Stop process
```
**Package Management**

```
▪ Install/update software
sudo apt update
sudo apt upgrade
sudo apt install <package-name>
```
**Logs Management**

```
▪ System activity records
Location
/var/log
```
**Service Management**

```
▪ Manage system services
sudo systemctl status <service-name>
sudo systemctl stop <service-name>
sudo systemctl start <service-name>
```
