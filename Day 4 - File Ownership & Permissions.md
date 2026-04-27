# Day 4 -File Ownership & Permissions

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

<img width="406" height="51" alt="image" src="https://github.com/user-attachments/assets/60a9fd55-9ac2-43a2-8e76-cc6e7724c37b" />
</br>

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
<img width="395" height="54" alt="image" src="https://github.com/user-attachments/assets/25805407-782e-473d-bfde-f7d5f13afde9" />

</br>

**Exercise 3: Symbolic method**

**Goal:**

```
▪ Add execute permission to user
▪ Remove read from others
```
**Solution:**
<img width="395" height="68" alt="image" src="https://github.com/user-attachments/assets/8135562d-61f6-4417-bf76-dd2aba6b16bb" />
</br>

**Exercise 4: Real DevOps Scenario**

**Create script:**

vim deploy.sh
<img width="317" height="209" alt="image" src="https://github.com/user-attachments/assets/336879b4-f6d1-4bd7-b5e5-c86a149cff4c" />
</br>
**Save and run**

./deploy.sh
<img width="394" height="58" alt="image" src="https://github.com/user-attachments/assets/0fd47fff-85fc-432f-8d13-6e273c4806e9" />
</br>

chmod +x deploy.sh
<img width="396" height="78" alt="image" src="https://github.com/user-attachments/assets/0d274f48-e9e3-4135-b3cc-8b23796a8a97" />
</br>

## Linux File System

Linux follows a hierarchical structure (tree-like) starting from

/ # root(/) is the top most directory everything lives under it

Linux Directory Structure

/ (Root)

Base of everything

/home

User personal directory

**Example: /home/ubuntu**

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
<img width="453" height="389" alt="image" src="https://github.com/user-attachments/assets/e3b355f4-ea17-4a06-a509-21948ccc01a1" />
</br>

**Exercise 2: Navigate user directory**

cd /home

ls -l

cd ~

pwd
<img width="371" height="96" alt="image" src="https://github.com/user-attachments/assets/90e4cd0c-f80c-4598-8079-0462d6c5e06d" />
</br>

**Exercise 3: Create your own structure**

**Goal:** Create project folder structure

myproject (code, logs, data)
<img width="1009" height="270" alt="image" src="https://github.com/user-attachments/assets/a27d1491-ad28-43f7-9d26-4d1bd55f2d89" />
</br>
**Exercise 4: Create files in different directory**

touch myproject/code/app.txt

touch myproject/logs/app.log

touch myproject/data/input.txt

<img width="900" height="189" alt="image" src="https://github.com/user-attachments/assets/c30f40fc-1b8f-4875-bb96-cc2565426321" />
</br>
**Note: tree command in linux is used to display the directory structure in a
hierarchical (tree-like) structure**

**Installation instructions:**

sudo apt update

sudo apt install -y tree
<img width="739" height="293" alt="image" src="https://github.com/user-attachments/assets/478c7821-f0d0-4dc7-907e-9bfc9b04b89a" />
</br>

**Additional Pointers**

**Everything is a file**

Almost everything is treated as file: even hardware, processes and system info

Examples


| Type | Example | Meaning |
|------|---------|---------|
| Regular file | file.txt | Normal data |
| Directory | /home | Folder |
| Device | /dev/sda | Hard disk |
| Process info | /proc/cpuinfo | CPU Details |

**Absolute vs Relative Path**

**Absolute path**

Full path from root /

/home/ubuntu/file.txt
<img width="1019" height="69" alt="image" src="https://github.com/user-attachments/assets/b0c00901-7414-4518-9934-e05fa7b67e4a" />
</br>

**Relative path**

Path based on current location

file.txt

../file.txt

| Symbol | Meaning |
|--------|---------|
| . | current directory |
|.. | parent directory |
|~ | home directory |

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

| Linux | Windows |
|-------|----------|
|Cron job| Task schedular|
|Crontab| Scheduled Tasks UI|

**Cron System Components**

**Key parts:**

```
▪ cron daemon (crond): runs in background
▪ crontab file: store scheduled jobs
▪ command/script: What you want to run
```
**Crontab Syntax**
<img width="1004" height="495" alt="image" src="https://github.com/user-attachments/assets/ebe820b2-9c5d-4844-bc2f-6d56ae174568" />
</br>
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
<img width="1253" height="420" alt="image" src="https://github.com/user-attachments/assets/1baf70c6-dbdf-4702-92d5-a8b4af082794" />
</br>

**Troubleshooting:**

If not getting the output, follow below steps

▪ Check if cron service is running or not
sudo systemctl status cron
<img width="1253" height="432" alt="image" src="https://github.com/user-attachments/assets/e677785e-5a85-4efa-9699-232b991afb84" />
</br>
Check cron logs

sudo grep CRON /var/log/syslog
<img width="1253" height="435" alt="image" src="https://github.com/user-attachments/assets/8f920bf9-0760-4e5f-8516-6474c723e111" />
</br>
List the jobs

crontab -l

**Exercise 2: Runs Every 5 minutes**

***/5 * * * * echo “Hello Again” >> /home/ubuntu/cron.txt**
<img width="1253" height="486" alt="image" src="https://github.com/user-attachments/assets/309bbcb2-565e-4d75-a99c-15698cad8e1e" />
</br>

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
