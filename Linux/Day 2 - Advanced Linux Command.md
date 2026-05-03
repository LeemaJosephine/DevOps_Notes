# Day-2 Advanced Linux Command

## Launch a Virtual Machine (Ubuntu based VM)

Virtual Machine: Computer within a Computer  
Goal: To practice Linux  

## 2 ways to do this task:

### Method 1: AWS (Recommended for Office Laptops)
- Create AWS account and give payment option. This payment option can be cancled in the later point as we will using the provided initial credits.
- Launch VM using EC2

### Method 2: Local Setup
- Install VirtualBox: https://www.virtualbox.org/
- Download Ubuntu ISO: https://ubuntu.com/download/desktop

### Mac Users
- Use Terminal to practice Linux commands  
- Limitation: Office laptops may restrict installations  

**Go with Method 1**

---

# Method 1 Demo: Launch an ubuntu virtual machine in AWS

**EC2: Elastic Compute Cloud** (Virtual servers in the cloud)  
**Region:** Geographical location where AWS has its presence  

**Recommendation:** Always perform all your exercises in a single region till the time there is no limitation or constraint specific to the region. Choose Mumbai in case you are using India sever.

**Amazon EC2 (Elastic Compute Cloud) = Virtual Servers in the Cloud**  

---

## Step 1: Login to AWS Console
- Go to: https://aws.amazon.com/console/  
- Sign in to your AWS account  

## Step 2: Go to EC2 Dashboard
- Search for EC2 in the search bar  
- Click on EC2 (Elastic Compute Cloud)  

## Step 3: Configure Basic Details
- Name: Give your instance a name  
- AMI (Amazon Machine Imgae) (OS): Choose OS (Ubuntu)  
- Instance Type: Select (e.g., t3.micro - free tier)  

## Step 4: Key Pair
- Proceed without a key par

### Step 5: Launch Instance
- Click Launch Instance  

## Step 6: Connect to Instance
- Click on Connect button  
- Use EC2 instance connect option to connect  

---

## Analogy:
- Apartment building  
- Instance: Rented House  
- Instance type: Different house sizes (1BHK, 2BHK, 3BHK)  
- AMI (Amazon Machine Image): Prefurnished house  
- Key Pair: House Key

---

# Linux Commands

Text-based instructions that you type into a terminal (command line) to tell the linux operating system what to do  

---

# Task 1: Navigate the system (Where am I?)

**Goal: find your current location and move around**

```bash
pwd          # Show current directory
ls           # List files/folders
ls -a        # Include hidden files
ls -l        # Detailed list
cd /home     # Go to /home
cd ..        # Move one level up
cd ~         # Go to home directory
```

# Task 2: File & Folder Management

**Goal: Create project structure**
```bash
mkdir <folder-name>        # Create folder
cd <folder-name>           # Enter folder

touch <file-name>       # Create file

mkdir <folder-name>         # Create another folder
cp <file-name> <folder-name>   # Copy file

mv <old-file-name> <new-file-name>  # Rename file

rm <file-name>           # Delete file
```
# Task 3: Shortcuts & Productivity

```bash
# Create Multiple Files
touch <file1> <file2> <file3> <file4>

# Create Nested Directories
mkdir -p project1/src/components

# Copy Entire Folder
cp -r <folder-name> <new-folder>

# Move Multiple Files
mv <file1> <file2> <file3> <folder>/
```

# Task 4: Loops (Automation)
**Goal: Create 10 files**

```bash
# Loop Method
for i in {1..10}; do
  touch file$i.txt
done

# Shortcut Method
touch file{1..10}.txt
```
