# Understanding the PATH Environment Variable
 
`PATH` is an environment variable that tells Linux: **"Where to look for executable commands"**
 
## Check Your PATH
 
```bash
echo $PATH
```
 
## How PATH Works
 
When you run a command like `ls`, the system checks directories in order:
 
```
/usr/local/sbin  → not found
/usr/local/bin   → not found
/usr/sbin        → not found
/usr/bin         → FOUND ✓
```
 
**Example:**
 
```bash
which ls
```

**Without PATH** — you must run:
 
```bash
/usr/bin/ls
```
 
**With PATH** — you just run:
 
```bash
ls
```
 
---
 
## Hands-on Demo
 
### Step 1: Create custom script
 
```bash
nano hello.sh
```
 
```bash
echo "Hello World"
```
 
### Step 2: Run Script
 
```bash
chmod u+x hello.sh
./hello.sh
```
 
### Try running directly (without `./`)
 
```bash
hello.sh
```
 
### Add Current Directory to PATH
 
```bash
export PATH=$PATH:$(pwd)
hello.sh
```

 
---
 
## Temporary vs Permanent PATH
 
**Temporary** (lost after logout):
 
```bash
export PATH=$PATH:$(pwd)
```
 
**Permanent** (add to `.bashrc`):
 
```bash
export PATH=$PATH:$(pwd)
source ~/.bashrc
```
 
---
 
# Writing a Shell Script to Host a Website
 
```bash
#!/bin/bash
PORT=$1
 
# Create website folder
mkdir -p website
cd website
 
# Create sample HTML file
cat <<EOF > index.html
<html>
<head><title>My Website</title></head>
<body>
<h1>Welcome to My Website</h1>
<p>Hosted using shell script</p>
</body>
</html>
EOF
 
# Start server
echo "Starting Website on Port $PORT"
nohup python3 -m http.server $PORT > server.log 2>&1 &
echo "Website is running at http://13.206.81.151:$PORT"
```
 # Create, Delete and Persist Environment Variables in Linux (Bash)
 
## What is an Environment Variable?
 
A variable available to the current shell and child processes.
 
Examples: `PATH`, `HOME`, `USER`
 
---
 
## Create Environment Variable (Temporary)
 
```bash
export MY_VAR="Learning DevOps"
echo $MY_VAR
```
 
**Check in Environment:**
 
```bash
env | grep MY_VAR
# MY_VAR=Learning DevOps
```
 
> **Note:** This variable exists only in the current session and is lost after logout.
 
---
 
## Delete Environment Variable
 
```bash
unset MY_VAR
echo $MY_VAR   # prints nothing
```
 
---
 
## Persist Variable (User Level)
 
### Step 1: Open .bashrc
 
```bash
nano ~/.bashrc
```
 
### Step 2: Add line
 
```bash
export MY_VAR="Persistent_Value"
```
 
### Step 3: Apply
 
```bash
source ~/.bashrc
```
 
### Step 4: Verify
 
```bash
echo $MY_VAR1
```
 
---
 
## Persist Variable (System-Wide)
 
### Step 1: Open file
 
```bash
sudo nano /etc/environment
```
 
### Step 2: Add
 
```
MY_GLOBAL_VAR="Hello_ALL"
```
 
### Step 3: Reload
 
```bash
source /etc/environment
```
 
### Step 4: Verify
 
```bash
echo $MY_GLOBAL_VAR
```
 
---
