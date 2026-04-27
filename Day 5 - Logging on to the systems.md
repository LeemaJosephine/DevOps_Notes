# Day 5 - Logging on to the systems

Archiving: Combining multiple files/folders into a single file

## Windows Comparison

| Linux   | Windows             |
|---------|---------------------|
| .tar    | ZIP file            |
| .tar.gz | Compressed zip file |

## Archiving vs Compression

**Archiving:** Combining files

**Compression:** Reducing the size

### Examples

- `.tar` (tape archive) → archive only
- `.tar.gz` → archive + compressed
- `.tar.bz2` → Stronger compression

## Basic Syntax

```
tar [options] archive_name files_or_folder
```

| Option | Meaning              |
|--------|----------------------|
| `-c`   | Create archive       |
| `-x`   | Extract archive      |
| `-v`   | Verbose (show files) |
| `-f`   | Filename             |
| `-z`   | gzip compression     |
| `-j`   | bzip2 compression    |
| `-C`   | Extract to directory |

---

## Hands-on Exercise

### Step 1: Create test folder

```bash
mkdir demo
touch demo/file1.txt demo/file2.txt demo/file3.txt
ls -l
ls -l demo
```

### Step 2: Create archive (.tar)

```bash
tar -cvf demo.tar demo/
```

### Step 3: Check the content

```bash
tar -tvf demo.tar
```

### Step 4: Create compressed archive

```bash
tar -czvf demo.tar.gz demo/
```

### Step 5: Extract Archive

```bash
tar -xvf demo.tar
```

### Step 6: Extract compressed archive

```bash
tar -xzvf demo.tar.gz
```

### Step 7: Extract to a specific folder

```bash
mkdir output
tar -xvzf demo.tar.gz -C output/
```

---

## Mini Projects

### Mini Project 1: Backup Script

**Goal:** Create backup automatically

**Step 1:** Remove everything (cleanup)

```bash
rm -r <folder-names>
```

**Step 2:** Create a backup script to take the backup of all files in a folder

```bash
#!/bin/bash
tar -czvf backup_$(date +%F).tar.gz demo/
```

> **Note:** `%F` format specifier prints the current date in `YYYY-MM-DD` format

**Step 3:** Make your script executable and run it

```bash
ls -l backup.sh
chmod +x backup.sh
./backup.sh
```

---

### Mini Project 2: Send and Extract

#### Setup Virtual Machine using VirtualBox

**Step 1:** Install Oracle VM VirtualBox

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

**Step 2:** Download Ubuntu ISO (clone of a disk)

[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)

**Step 3:** Create VM

Open VirtualBox → Click New, then fill in:

- **Name:** ubuntu
- **Type:** Linux
- **Version:** Ubuntu (64-bit)

**Step 4:** Follow the Guided installation steps

---

## What is SSH?

**SSH is a secure protocol used to connect to another computer over a network.**

### Windows Comparison

| Linux SSH      | Windows Equivalent   |
|----------------|----------------------|
| Terminal Login | Remote Desktop (RDP) |
| CLI-based      | GUI-based            |

### How SSH Works

1. Client → requests connection
2. Server → verifies identity
3. Authentication (password/key)
4. Encrypted session starts

---

## SSH Authentication Methods

### 1. Password-based (basic)

```bash
ssh user@ip
```

A password prompt will appear. You need to enter the password.
> Less secure.

### 2. Key-based (recommended)

Uses a **private key** (client) and **public key** (server).

---

## Generate SSH Key Pair

```bash
ssh-keygen
```

### Output

| File       | Meaning     |
|------------|-------------|
| id_rsa     | Private Key |
| id_rsa.pub | Public Key  |

**Location:** `~/.ssh/`

---

## Demo: Establish Connectivity to EC2 Instance

*From Windows and Mac terminal after generating SSH key pair on EC2 instance*

**Step 1:** Connect to EC2 using Instance Connect

**Step 2:** Generate key inside EC2

```bash
ssh-keygen -t rsa -b 4096 -f ~/.ssh/mykey
```

| Flag              | Explanation                              |
|-------------------|------------------------------------------|
| `ssh-keygen`      | Tool to generate SSH key pairs           |
| `-t rsa`          | Use RSA encryption algorithm             |
| `-b 4096`         | Create a 4096-bit key                    |
| `-f ~/.ssh/mykey` | Save key to `~/.ssh/mykey`              |

**Step 3:** Add public key to Authorized Access

```bash
cat ~/.ssh/mykey.pub >> ~/.ssh/authorized_keys
```

**Step 4:** Download private key to your local system

```bash
cat ~/.ssh/mykey   # Copy entire output to a file on local and save it as mykey.pem
```
