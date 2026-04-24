# Day 3 - Advanced Linux Command Cont

## Package Manager - Installing Software

A package manager is a tool that helps you

```
▪ Install software
▪ Update software
▪ Remove software
▪ Manage dependencies automatically
```
**Ubuntu** : apt(package manager)

**Use case:** Install webserver(nginx) (which is used to host web application)

**Commands:**

```
➢ sudo apt update # refresh package list
➢ sudo apt upgrade # upgrade all packages
➢ sudo apt install nginx # prompt with y/N
➢ sudo apt install -y nginx # auto approved
```
**Notes** :

**sudo** : elevated privileges. In linux sudo stands for "SuperUser Do". It is a
command used in linux which allows a normal user to execute commands with
elevated (administrator/root) privileges.

**Case Study 1: New Server Setup**

**Scenario** : Prepare a fresh linux server for development

**What you should think**

You need to update and upgrade system and install essential tools

```
Tool Why Needed^
git Version control^
curl API calls/downloads^
wget File downloads^
vim File editing^
```
# **Step 1: Update system**

sudo apt update

**#Step 2: Upgrade packages**

sudo apt upgrade -y

**#Step 3: Install essential tools**

sudo apt install -y git curl wget vim

**#Verify**

git --version

curl --version

vim --version

**Case Study 2: Web Server Deployment**

**Scenario** : Deploy a basic web server on linux

**What you should think**

Need to install and run web server (nginx/apache)

**Steps**

**# Install nginx**

sudo apt install -y nginx

**# Status of nginx**

sudo systemctl status nginx

**# Start the nginx if not running**

sudo systemctl start nginx

**How to test:** [http://<EC](http://<EC) 2 - Public-ip>

**Working with Vim Editor**

Vim (Vi Improved) is a terminal based text-editor used to

```
▪ Edit config files on servers
▪ Write scripts
▪ Debug logs
▪ Work over SSH (no GUI)
```

Vim has 3 main modes

```
Mode Purpose
Normal Navigation+Commands
Insert Typing text
Command Save, quit, actions
```
**Mode flow**

Normal -> (i)-> Insert -> (Esc) -> Normal-> (:)-> Command

**Basic Commands**

**# Open file**

vim <file-name>

**# Enter Insert mode**

i

**# Exit insert mode**

Esc

**# Save and quit**

:wq

**# Quit without saving**

:q!

**Exercise:** Create a text file with some test content using vim editor and display
the content on terminal window.

**Navigation Shortcuts**

Move Cursor

```
Key Action
h left
l right
j down
k up
```

**Word movement**

w -> next word

b -> previous word

**Line Movement**

0 - > start of line

$ -> end of line

**Jump**

gg ->top of file

G -> bottom of file

**Editing shortcut**

dd -> delete line

x -> delete character

**Copy and Paste**

yy -> copy line

p -> paste

**Search**

/error

n-> next match

N -> previous match

**Case Study 1: Creating a config file**

**Scenario** : Need to create config file for your app

**Case Study 2: Fixing a production bug**

**Scenario** : Your config has wrong port

port=3000 (wrong)


**Case Study 3: Delete and Replace lines**

**Scenario** : Remove a debug line

**Filters and Redirections**

**Filters**

Commands that process data (input -> output)

**Examples:**

```
▪ grep -> find text
▪ sort -> arrange data
▪ uniq -> remove duplicates
```
**Redirection**

Controls where input/output goes, Instead of just printing on screen

```
▪ Save to file
▪ Append to file
▪ Pass to another command
```
**Core Idea**

Command -> Output -> (redirect or filter) -> result

**Part 1: REDIRECTION**

1. > (Overwrite Output)

Send output to a file (and replace existing content)

**Example:**

ls -l > test.txt

**Use Case:**

```
▪ Save logs
▪ Store command output
```
**Note:** If the file exists -> it will be overwritten

2. >> (Append Output)

Adds output to the end of file (does not overwrite)

**Example:**

echo "Hello" >> file.txt

**Use case:**

Appending data

3. < (input Redirection)

Takes input from a file instead of keyboard

**Example:**

```
▪ cat < file.txt
▪ Same as
▪ cat file.txt
```
**Example:**

wc -l < file.txt

**Difference**

Without <

wc -l file.txt (# file.txt is having a content Hello Linux)

**Output**

1 file.txt

**With <**

**Output** : 1

Cleaner output (automation or in scripting)

**Use Case:**

Feeding input to scripts

4. | (Pipe)

Pass output of one command as input to another

**Example:**

cat file.txt | grep error

**Use Cases:**

log filtering

**Part 2: FILTER commands**

1. cat (View file)

Example usage:

cat file.txt (display content)

2. grep (search text)

Example:

grep "error" file.txt (finds line containing error)

3. sort

Example:

sort file.txt (sort lines alphabetically)

4. uniq (remove duplicates lines (only consecutive))

uniq file.txt

5. wc (Word Count)

wc -l file.txt (Count lines)

Users, Groups & Permissions

Linux is a multi-user system

. Multiple users can access the same machine
. Each user has controlled access

To manage this, linux has

. Users
. Groups
. Permissions

## USERS?

A user is an identity that can:

. Log into the system
. Own files
. Run commands

Types of users

Type Description

Root user Super admin (full access)

Normal user Limited access

System user used by services (like nginx)

Commands

Create user

sudo adduser <user-name>

Switch user

su <user-name>

Check current user

whoami

## GORUPS?

A group is a collection of users

Used to:

. Manage permissions easily
. Give access to multiple users

Commands

# Create group

sudo groupadd developers

# Add user to group

sudo usermod -aG developers <user-name>

# Check groups

groups <user-name>

# Command to check the list of users in a specific group

grep <group-name> /etc/group

Permissions

Every file has 3 permissions

Symbol Meaning

r read

w write

x execute

Permission structure

- rwxr-xr--

rwx owner(file creator) permissions

r-x group(assigned group) permissions

r-- others (everyone else)

Change Permissions

chmod

Numeric Method

Numbers Permissions

7 rwx

6 rw-

5 r-x

4 r--

Permission

r(read) = 4

w(write) = 2

x(execute) = 1

Example:

chmod 755 file.sh

Owner -> rwx

Group -> r-x

Others -> r-x

Symbolic method

chmod +x file.sh

Other Variations

Only Owner

chmod u+x file.sh

Only Group

chmod g+x file.sh

Only others

chmod o+x file.sh

Multiple

chmod ug+x file.sh


