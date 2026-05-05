# Day 9 - Introduction to Scripting

# Introduction to Shell Scripting

## What is Shell Scripting?

Writing a sequence of Linux commands in a file to automate tasks.

## What is a Shell?

A shell is a program that:
- Takes your commands
- Executes them on the system

## Common Shells

- **Bash** (mostly used)
- Zsh
- Sh

## Example: Manual vs Automated

```bash
# Manual
sudo apt update
sudo apt install nginx -y
```

```bash
# Automate using Shell Script
#!/bin/bash
sudo apt update
sudo apt install nginx -y
```

## Basic Structure of a Script

```bash
#!/bin/bash
echo "Hello World"
```

**Explanation:**
- `#!/bin/bash` — **shebang** → tells system to use Bash
- `#` → Comment
- `echo` → prints output

---

## Hands-on: Exploring Shell Scripting on EC2 (Ubuntu) Instance

### Step 1: Create a Script File

```bash
nano script.sh
```

### Step 2: Add Content

```bash
#!/bin/bash
echo "Hello from EC2"
```

### Step 3: Make Executable

```bash
chmod +x script.sh
```

### Step 4: Run Script

```bash
./script.sh
```
---

## Shell vs sh vs bash

**Shell** = category (not a specific tool)

### What is sh?

**sh = Bourne shell**
- One of the oldest Unix shells
- Basic and minimal

**Features:**
- Simple scripting
- Limited functionality

### What is bash?

**Bash = Bourne Again Shell**
- Improved version of sh
- Default shell in most Linux systems

**Features:**
- Variables
- Arrays
- Loops
- Advanced Scripting
- Auto-completion

**Example: Check current shell**

```bash
echo $SHELL
```

---

## Experiment: What Bash Supports That sh Does Not

```bash
#!/bin/bash
arr=(1 2 3)
echo ${arr[0]}
```

**Run with bash:**

```bash
bash demoscript.sh
```

**Run with sh:**

```bash
sh demoscript.sh
```

> sh does not support arrays — it throws a syntax error.

---

# Variables in Shell Scripting

## What is a Variable?

A variable is a container to store data (text, numbers, command output)

```bash
name="Leema"
```

**Basic Syntax:**

```bash
variable_name=value
```

## Hands-on: Defining Variables in a Script File

```bash
#!/bin/bash
name="Leema"
profession="Cloud Architect"
echo "Name is $name"
echo "Profession is $profession"
```


**Give permissions:**

```bash
chmod a-x script.sh
chmod u+x script.sh
```

**Run the script:**

```bash
./script.sh
```

---

## Types of Variables in Shell Scripting

Variables are classified based on: **who defines them + where they are used + how long they exist**

### 1. User-Defined Variables

Variables created by the user inside scripts
- Defined manually
- Used for storing custom values
- Scope = current script/session

### 2. System Variables (Predefined Variables)

Variables already defined by the system (OS)
- Provided by Linux
- Used to get system info

| Variable | Meaning              |
|----------|----------------------|
| `$HOME`  | Home directory path  |
| `$USER`  | Current username     |
| `$PWD`   | Present working dir  |
| `$SHELL` | Current shell path   |

### 3. Environment Variables

Variables available to all processes and child processes
- Global scope
- Inherited by child processes
- Set using `export`

**Example:**

```bash
export MY_VAR="Hello"
echo $MY_VAR
```

**Check all environment variables:**

```bash
env
```

**Use Cases:**
- Configure applications
- Set PATH
- Store API URLs

---

## Demo: Environment Variable vs User-Defined Variable

- **User-defined variables →** local to current shell (not inherited)
- **Environment variables →** exported + visible to child processes

### Part 1: User-Defined Variable (Local Scope)

**Step 1: Create a variable**

```bash
my_var="Hello_User"
echo $my_var
```

**Step 2: Check if it's in the environment**

```bash
env | grep my_var
```


**Explanation:**
- Variables exist in the current shell only
- Not part of the environment

**Step 3: Spawn a child shell**

```bash
sudo bash
```

> **Note:** To check the process ID of the current shell: `echo $$`

**Step 4: Inside new shell, check the variable**

```bash
echo $my_var
```

> **Conclusion:** User-defined variable is **NOT** inherited by child process.

---

### Part 2: Environment Variable (Global Scope)

**Step 1: Export Variable**

```bash
export my_env="Hello Env"
echo $my_env
```

> **Note:** Define global variable in `.bashrc` for it to be permanent across sessions.

**Step 2: Spawn a child shell**

```bash
bash
```

**Step 3: Test the variable again**

```bash
echo $my_env
```

> **Conclusion:** Exported environment variables **ARE** inherited by child processes.

---

## Exercise: Make Variables Persistent System-wide (For All Users)

### Method 1: Edit Global Environment Variables for All Users

```bash
sudo nano /etc/environment
```

Add your variable in the format:

```
MY_GLOBAL_VAR="value"
```

Save and reload: changes take effect on next login for all users.
# Basic Operators

Helps you perform calculations, comparisons and logical decisions in scripts

## Types of Operators in Shell

- Arithmetic Operators
- Relational (Comparison) Operators
- Logical Operators
- String Operators
- File Test Operators

---

## Arithmetic Operators

Used for calculations (numbers)

**Example:**

```bash
a=10
b=5
echo $((a + b))
echo $((a - b))
echo $((a * b))
echo $((a / b))
```

---

## Relational (Numeric Comparison)

Used in `if` conditions

| Operator | Meaning          |
|----------|------------------|
| `-eq`    | equal            |
| `-ne`    | not equal        |
| `-gt`    | greater than     |
| `-lt`    | less than        |
| `-ge`    | greater or equal |
| `-le`    | less or equal    |

**Example:**

```bash
#!/bin/bash
a=10
b=5
if [ $a -gt $b ]
then
  echo "a is greater"
fi
```

<img width="826" height="323" alt="image" src="https://github.com/user-attachments/assets/d78e185d-e65b-4509-b0a6-16b87f28662b" />
</br>

<img width="616" height="57" alt="image" src="https://github.com/user-attachments/assets/728f2e4d-bb34-4adf-908f-434b9adf0e50" />
</br>

---

## Logical Operators

Combine conditions

**Example:**

```bash
#!/bin/bash
a=10
b=5
if [ $a -gt 5 ] && [ $b -lt 10 ]
then
  echo "both true"
fi
```

<img width="545" height="226" alt="image" src="https://github.com/user-attachments/assets/ebf6ab1e-23cd-4621-a22c-cdd07fec00e8" />
</br>
<img width="586" height="60" alt="image" src="https://github.com/user-attachments/assets/8dbc4d69-c00a-47bd-a977-74c344f29b92" />
</br>

| Operator   | Behavior                   |
|------------|----------------------------|
| `&&` (AND) | Both conditions must pass  |
| `\|\|` (OR)  | Any one condition passes   |
| `!` (NOT)  | Reverses the result        |

---

## String Operators

Work with text

```bash
#!/bin/bash
name="Leema"
if [ "$name" = "Leema" ]
then
  echo "Match"
fi
```

| Operator | Meaning      |
|----------|--------------|
| `=`      | Equal        |
| `!=`     | Not equal    |
| `-z`     | Empty string |
| `-n`     | Not empty    |

---

## File Test Operators

Check files/directories

| Operator | Meaning          |
|----------|------------------|
| `-f`     | File exists      |
| `-d`     | Directory exists |
| `-r`     | Readable         |
| `-w`     | Writable         |
| `-x`     | Executable       |

```bash
if [ -f file.txt ]
then
  echo "File exists"
fi
```

---

## Hands-on 1: Disk Space Alert

**Goal:** Monitor disk usage and trigger alert when usage crosses threshold

- Disk full → app crashes
- Logs stop writing
- Database fails

### Step 1: Check disk usage manually

```bash
df -h
```

- `df`: disk filesystem info
- `-h`: human readable (GB/MB)

### Step 2: Extract the usage %

```bash
df / | awk 'NR==2 {print $5}'
```

### Step 3: Remove % Symbol

```bash
df / | awk 'NR==2 {print $5}' | sed 's/%//'
```

### Step 4: Add script code

```bash
#!/bin/bash
THRESHOLD=80
usage=$(df / | awk 'NR==2 {print $5}' | sed 's/%//')
echo "Current disk usage: $usage%"
if [ $usage -gt $THRESHOLD ]
then
  echo "ALERT: Disk usage is above $THRESHOLD%"
else
  echo "Disk usage is under control"
fi
```

### Positive Scenario (Normal Usage)

<img width="690" height="114" alt="image" src="https://github.com/user-attachments/assets/a3fc1a7d-94f1-4036-bf1a-0451ac2a7678" />
</br>

### Negative Scenario — Simulate High Usage

```bash
fallocate -l 5G bigfile
```

<img width="1190" height="624" alt="image" src="https://github.com/user-attachments/assets/17ae4ad4-3355-4e53-934e-d5ee105df33c" />
</br>

---

## Hands-on 2: File Backup Automation

**Goal:** Backup file only if it exists

- Avoid error during automation
- Prevent copying non-existent files

### Step 1: Create a file

```bash
touch file.txt
```

### Step 2: Create a script

```bash
nano backup.sh
```

```bash
#!/bin/bash
FILE="file.txt"
if [ -f "$FILE" ]
then
  cp $FILE backup.txt && echo "Backup successful"
else
  echo "File not Found"
fi
```
---

## Hands-on 3: Port Check Before Starting the App

**Goal:** Start a server (service) only if port is free, otherwise prevent conflict

### Step 1: Check if port is in use

```bash
ss -tuln | grep 8080
```

- `ss`: shows network sockets
- `-t`: TCP
- `-u`: UDP
- `-l`: listening ports
- `-n`: Numeric (no DNS)
- `grep 8080`: filter for port 8080

### Step 2: Create Script

```bash
nano port_check.sh
```

```bash
#!/bin/bash
PORT=8080
if ss -tuln | grep -q ":$PORT"
then
  echo "Port $PORT already in use"
else
  echo "Starting server"
  python3 -m http.server $PORT
fi
```

### Testing Positive Scenario

<img width="995" height="498" alt="image" src="https://github.com/user-attachments/assets/46d907ea-0e36-4b0a-863f-b9dfa00c240a" />
</br>

### Negative Scenario

<img width="663" height="94" alt="image" src="https://github.com/user-attachments/assets/c4578936-77d7-44bd-a037-b903c5d4c8f2" />
</br>

---

## Read User Input

**What is `read`?**  
A command used to take input from the user (keyboard).

**Basic Syntax:**

```bash
read variable_name
```

### Hands-on: Read User Input

**Step 1: Create script**

```bash
nano input.sh
```

```bash
#!/bin/bash
echo "Enter your name:"
read name
echo "Hello $name"
```

### Reading Multiple Inputs

```bash
echo "Enter first and last name"
read first last
echo "First: $first"
echo "Last: $last"
```

### Read Input with Prompt

```bash
read -p "Enter your Age: " age
echo "Age is $age"
```

> **Note:** `-p` displays prompt message inline


### Hidden Input (Password)

```bash
read -s -p "Enter password: " pass
echo
echo "Password received"
```


### Default Value Handling

```bash
read -p "Enter your city: " city
city=${city:-"Delhi"}
echo "City: $city"
```

> **Note:** If user enters nothing → default value is used


---

## Quiz

**Which command is used to take user input?**
- A. echo
- B. input
- C. **read** ✅
- D. scan

**Which symbol is used to access a variable value?**
- A. @
- B. **$** ✅
- C. #
- D. %

**Which is a correct variable declaration?**
- A. name=Yash
- B. **name="Yash"** ✅
- C. $name="yash"
- D. var name="Yash"

**Which variable is available to child processes?**
- A. Local variable
- B. User variable
- C. **Environment Variable** ✅
- D. Read-only variable

**Which command makes a variable global?**
- A. set
- B. **export** ✅
- C. env
- D. global

**What does `cmd1 && cmd2` mean?**
- A. Run both always
- B. Run cmd2 only if cmd1 fails
- C. **Run cmd2 only if cmd1 succeeds** ✅
- D. Ignore cmd1

**Which command checks open ports?**
- A. ls
- B. **ss** ✅
- C. pwd
- D. cat

**`cp file.txt backup.txt && echo "Done"` — When will "Done" print?**
- A. Always
- B. Only if copy fails
- C. **Only if copy succeeds** ✅
- D. Never

**What will happen? `grep "error" log.txt || echo "No errors"`**
- A. Always prints "No errors"
- B. **Prints only if grep fails** ✅
- C. Never prints
- D. Delete files
