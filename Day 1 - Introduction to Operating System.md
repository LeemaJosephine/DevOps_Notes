# Day 1 - Introduction to Operating System

# What is an OS?
  Operating System is a middle layer between user and application Hardware.
  E.g: Windows, Linux, MacOS, Android etc.,
  
Operating Systems are classified based on where we are using it.
- Desktop/ Laptop - Windows, MacOS, Linux
- Mobile - Android. iOS, Harmony
- Server/Enterprise level - Red Hat
- We have a lot of OS beyond the above listed.

# What does an OS do?
- Running the program
- Memory Management
- File Management
- Resource Management
  
E.g: User clicks the bowser to open, CPU will perform the action and all this is done by OS.
    
# Main Components of OS

Each component of does some work, the components are: 
-  Kernel (Core of OS) -> Controls CPU, Memory, Devices.
-  System Calls - Interface between Apps and OS
-  File System - Organising data (files/folder)
-  Device Drivers - Communicate with hardware
-  User Interface - CLI (Terminal) or GUI (Graphical User Interface)

# Tasks of an OS
  ##  Major Responsibilities
  1. Process Management - Runs multiple program (Multi-Tasking)
  2. Memory Management - Allocate RAM efficiently
  3. File Management - Stores and retrives files
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

Popular Distors:
- Ubuntu
- Kali Linux
- Debian
- Fedora

Where is is used
- Cloud
- DevOps
- Web services (90% of internet runs on Linux)

## Windows
  - 
## MacOS
  - 
## Unix

  - One of the oldest operating system
  - Dveloped at Bell Labs
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

 
### Unix is Parent of Linux and Windows

# Linux Vs Windows

### When to use Windows?
- When you want ease of use
- Regular office work or gaming
- Need specific software (MS Office, Adobe)
- Windows = Ease + Compatibility + Desktop
  
### When to use Linux?
- Choose Linux if you want performance + Control
- You like customization
- You are into programming/DevOps/Cloud
- Linux = Power + Control + Servers
- Why Linux is Lightweight? 
      Minimal beackground process, runs only essential services, no unnecessary apps by default as result uses less RAM, CPU and storage.
  
### How an organization decides (Linus or Windows): 
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
3. Security Requiremenrs - Surface of the attack is less in Linux than Windows. Windows need anti-virus
4. Application Compatibility
5. Team Skills - Linus needs commanf line knowledge, Windows needs lesser traing compared to Linux
6. Cloud and DevOps Stratergy - Windows for Cloud and Linus for Containers. 
7. Enterprise Ecosystem - Windows provide strong integration with Active directory (MS Team, Sharepoint), best for IT environment. Linux is strong in Open source ecosystems. 
  
### Can an organization run both Linux + Windows 
Yes, based on their requirement.

### Can we run Linux inside Windows (Linux on Windows)
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
### Can we run Windows inside Linux (Windows on Linux)

1. Virtual Machine (Computer within a Computer) - Windows runs inside Linux on VM
2. Wine (Compatibility Layer)
     - Not a full OS
     - Runs windows apps on Linux
3. Dual Boot
   - Install both OS on same system
   - Choose OS at startup
          

