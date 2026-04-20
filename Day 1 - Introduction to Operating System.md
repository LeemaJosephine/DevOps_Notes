# Day 1 - Introduction to Operating System

# What is an OS?
  Operating System is a middle layer between user and application Hardware.
  E.g: Windows, Linux, MacOS, Android etc.,
  
Operating Systems are classified based on where we are using it.
- **Desktop/ Laptop** - Windows, MacOS, Linux
- **Mobile** - Android. iOS, Harmony
- **Server/Enterprise level**- Red Hat
- There are many more specialized OS types beyond these.

# What does an OS do?
- Running the program
- Memory Management
- File Management
- Resource Management
  
Example: When a user clicks a browser, the OS coordinates CPU, memory, and other resources to open it.
    
# Main Components of OS

Each component of does some work, the components are: 
-  Kernel (Core of OS) -> Controls CPU, Memory, Devices.
-  System Calls - Interface between Apps and OS
-  File System - Organizing data (files/folder)
-  Device Drivers - Communicate with hardware
-  User Interface - CLI (Terminal) or GUI (Graphical User Interface)

# Tasks of an OS
  ##  Major Responsibilities
  1. Process Management - Runs multiple program (Multi-Tasking)
  2. Memory Management - Allocate RAM efficiently
  3. File Management - Stores and retrieves files
  4. Device Management - Controls Keyboard, mouse, printers.
  5. Security - User authentication and permissions.

# Types of Operating System

## Linux
  - Open Source powerhouse = Free access to code and Freedom to Change
  - Note: Red Hat is an Open source company, designed for commercial use.
  - What is distribution:
  - Linux Kernel + Software + tools + Package Manager + Interface (CLI)
  - Linux is a Unix-like OS Kernel combined with tools ->

Key Features:
  - Open Source
  - Strong community support
  - Extremely lightweight and powerful
  - Excellent for servers and development

Popular Distros:
- Ubuntu
- Kali Linux
- Debian
- Fedora

Where it is used
- Cloud
- DevOps
- Web services (90% of internet runs on Linux)

## Windows
  - User-friendly
  - Strong software compatibility
  - Popular for personal and enterprise desktop use
    
## MacOS
  - Developed by Apple Inc.
  - Based on Unix
  - Known for stability and design
    
## Unix

  - One of the oldest operating system
  - Developed at Bell Labs
  - Designed for multiuser and multitasking

Features:

  - Strong security and permission models
  - Highly stable and reliable
  - Written mostly in C language
  - Designed for servers and enterprise systems

Examples:

  - IBM AIX
  - HP-UX
  - Solaris
    
Usecases:

  - Banking systems
  - Telecom Infrastructure
  - Large Enterprise Services

 
### Unix is the parent of Linux (Unix-like)

# Linux Vs Windows

## When to use Windows?
- When you want ease of use
- Regular office work or gaming
- Need specific software (MS Office, Adobe)
- Windows = Ease + Compatibility + Desktop
  
## When to use Linux?
- Choose Linux if you want performance + Control
- You like customization
- You are into programming/DevOps/Cloud
- Linux = Power + Control + Servers
- Why Linux is Lightweight? 
      Minimal background process, runs only essential services, no unnecessary apps by default as result uses less RAM, CPU and storage.
  
## How an organization decides (Linux or Windows): 
1. Start with the Use Case
- Choose Linux when
    - Running Web Servers, APIs, Microservices.
    - Using cloud platform
    - Need high performance + automation
- Choose Windows when:
    - Use microsoft ecosystem
    - Need tools like
        - Active directory
        - .NET applications
        - Microsoft office
2. Cost Consideration
3. Security Requirements - Surface of the attack is less in Linux than Windows. Windows need anti-virus
4. Application Compatibility
5. Team Skills - Linus needs command line knowledge, Windows needs lesser training compared to Linux
6. Cloud and DevOps Strategy - Windows for Cloud and Linus for Containers. 
7. Enterprise Ecosystem - Windows provide strong integration with Active directory (MS Team, Sharepoint), best for IT environment. Linux is strong in Open source ecosystems. 
  
## Can an organization run both Linux + Windows 
Yes, based on their requirement.

## Can we run Linux inside Windows (Linux on Windows)
Yes,
1. WSL - Windows Subsystem for Linux
     WSL is present in windows by default using that we can run Linux inside Windows.
2. Virtual Machine (Computer within a Computer)
   Tools:
     - VirtualBox
     - VMWare
       How it works? Linux runs as separate operating system inside windows
3. Dual Boot
     - Install both OS on same system
     - Choose OS at startup
## Can we run Windows inside Linux (Windows on Linux)

1. Virtual Machine (Computer within a Computer) - Windows runs inside Linux on VM
2. Wine (Compatibility Layer)
     - Not a full OS
     - Runs windows apps on Linux
3. Dual Boot
   - Install both OS on same system
   - Choose OS at startup

# System States

## 1. Boot (System booting)
Starting the computer from OFF state
Technically:
- Power ON
- BIOS/UEFI starts
- Hardware checks (POST)
- Bootloader loads OS
- Kernel loads into RAM
- OS starts services - login screen appears.

Analogy:
Starting a car from completely OFF state
  -  Engine starts
  -  System initializes
  -  Ready to drive

## 2. Restart (Reboot)
Turning off and on automatically
Technically:
- OS will close all processes
- Clears RAM
- Reloads kernel
- Start Fresh

Analogy:
  Restarting your phone to fix temporary issues

## 3. Start (Power ON)
Processing power button to turn system ON
It triggers boot process
Technically:
- It sends signal to motherboard
- Boot sequences will begin

Analogy:
  Switching on electricity in house

## 4. Hibernet
Saves the current state and turn OFF completely
Technically:
- RAM data -> saved to hard disk
- Power = 0
- On resume -> state restored

Analogy:
  Like bookmarking a page in book

## 5. Shut down
Completetly turning off system
Technically:
- All process stopped
- RAM cleared
- OS safely exits
- Power OFF

Analogy: Closing shop for a day

## 6. Sleep
Pausing system but keeping RAM active

Technical:
- RAM powered
- CPU mostly off
- Quick resume

### Sleep Vs Hibernet

| Feature | Sleep | Hibernet |
| --------|-------|----------|
| Power use| Low  | Zero |
| Resume Speed | Fast | Slow |
| Data Storage | RAM | Disk |

## 7. Log off
Exit current user session

Technically:
- Closes user processes
- Keeps system ON

## 8. Lock
Locks screen without closing apps

Technically:
- Sessions remains active
- Requires password to access

## 9. Force Shutdown
Holding power button -> immediate shutdown

Risk:
- Data loss
- File corruption as there is no proper OS

### In DevOps, 2 operations are important 1. Reload/Restart 2. System Boot/Reboot

# What is Virtualization?
Virtualization is creating a virtual version of physical resource.

How it works
  - Managed by a Hypervisor
  - It divides
      - CPU
      - RAM
      - Storage
    - Creates multiple virtual systems

# What is Virtual Machine?
Virtual machine: software based computer.
  
It has
- OS
- CPU (Virtual CPU)
- RAM (Virtual)
- Disk (Virtual
    
    


