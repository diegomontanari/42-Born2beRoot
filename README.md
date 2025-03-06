# Born2BeRoot Project Guide 🚀

This README is not a complete guide for completing the Born2BeRoot project. 

In this guide, we will go over everything you need to know to complete the project and provide a step-by-step list of tasks to help you finish it.

For a full guide, I recommend checking out the repository by fcorvaro (I'll leave the link at the bottom in the sources).

Let's get started!

![virtualize-virtualize-everything](https://github.com/user-attachments/assets/cf8d02c8-68eb-4327-b734-7531975a4f10)


# Introduction

Welcome to *Born to be Root* – a beginner-friendly guide to mastering Linux system administration. Whether you're just starting out or looking to sharpen your skills, this repository will help you navigate the Linux environment with confidence.  

![memeaboutvirtualmachines_1_77](https://github.com/user-attachments/assets/8da0153e-c367-4ed8-96ba-a06e9edd8533)
*Image from iq.opengenus.org/virtualization/*

## Why Start This Project?  
If you're new to Linux, this guide will help you build a strong foundation and develop real-world skills. Learning system administration can seem overwhelming at first, but by following structured tutorials and hands-on exercises, you'll gain the confidence to manage your own Linux environment.  

By working through this project, you'll:  
✅ Understand how Linux works under the hood  
✅ Learn best practices for managing a system  
✅ Gain experience in troubleshooting and optimization  
✅ Build a skill set that is valuable for IT, cybersecurity, and DevOps  

No prior experience? No problem! *Born to be Root* is designed to be beginner-friendly, guiding you step by step as you explore the power of Linux. 

## Key Points We Will Cover In This Guide 🖥️

1) Understanding Virtual Machines
2) Debian vs CentOS and Rocky Linux
   - Why choose Debian for your VM setup?
   - How to install Debian on a Virtual Machine
3) Using VirtualBox
4) Configuring Your Virtual Machine (VM)
5) Understanding Partitions
   - What are partitions?
   - Different types of partitions (Primary, Extended, Logical)
   - How partitions are useful in VM setup
   - Mount Points Explained
6) Starting the Virtual Machine
   - Installing Vim and Sudo
   - Managing users and user groups
7) Writing a System Info Script
8) Understanding and Using Crontab
9) Commands you need to learn!

# Let's start! 🚀

![3e494f8437e6b23acafecb608036edd7](https://github.com/user-attachments/assets/d7fb338f-248d-4a26-8e2b-424cf46c1434)

## 1) Understanding Virtual Machines
A virtual machine (VM) is a **simulated computer that runs within a physical computer**. It functions as an isolated system, complete with its own operating system, memory, storage, and processing resources, all managed independently from the host system. In simpler terms, it's an emulation of a computer system that enables an operating system ('guest') to run as an application within another operating system ('host').

### How a Virtual Machine Works 🖥️
A virtual machine operates through software called a **Hypervisor - Virtual Machine Monitor (VMM)**, which manages and coordinates the following key components:

- **CPU (Central Processing Unit)** → The "brain" of the computer. It processes calculations and program instructions, coordinating the operation of all other parts, such as memory, storage, and peripherals.
- **RAM (Random Access Memory)** → Temporary memory that serves critical functions:
  - Acts as a workspace where the computer runs programs and processes active data.
  - Provides fast access to temporary data, which is erased when the computer is turned off.
  - Unlike the hard drive (which is slower but permanent), RAM allows quick retrieval of necessary information for active tasks.
- **Hard Drive (Storage Disk)** → The computer's permanent "storage unit," where data is preserved, including:
  - Files (documents, photos, videos, etc.)
  - Installed programs
  - The operating system (Windows, macOS, Linux)
  - Two common types of storage: HDD (Hard Disk Drive) – mechanical, cheaper but slower; SSD (Solid State Drive) – electronic, faster but more expensive.
- **Network Card** → Allows the computer to connect to the Internet or a local network via Ethernet cable or wireless.
- **Input/Output Devices** → Keyboards, mice, monitors, printers, etc.

### Role of the Hypervisor ⭐
The hypervisor abstracts and **distributes hardware resources among different virtual machines** (VMs), enabling them to function independently. There are two main types:

- **Bare-Metal Hypervisors** → Run directly on hardware without a host OS, making them *more efficient and secure since they access physical resources directly*. Examples: Microsoft Hyper-V, KVM.
- **Hosted Hypervisors** → Installed as software on an existing OS, *easier to configure but slightly less efficient due to additional abstraction*. Examples: VMware Workstation, Oracle VirtualBox.

A hypervisor is responsible for:
- Allocating physical resources across multiple virtual machines
- Scheduling CPU instruction execution
- Managing shared memory
- Controlling access to peripherals

### Purpose of Virtual Machines
Virtual machines allow multiple operating systems to run on a single physical machine while keeping each environment completely separate and secure. This technology is essential for optimizing hardware usage, testing software in a secure environment, and managing system backups efficiently. Virtualization also enables seamless migration of virtual environments across different physical computers, ensuring **flexibility and operational continuity**.

A **virtual machine (VM)** is an emulation of a computer system that allows an operating system ("guest") to run as an application inside another operating system ("host").

## Key Components

- **Hypervisor**: A software that creates and manages VMs, allocating resources like CPU, RAM, and storage space.
- **Isolation**: VMs are isolated from each other and from the host system, improving security and stability.
- **Portability**: VMs can be easily moved between different host systems, as long as they are compatible with the hypervisor.


## 2) Debian vs CentOS and Rocky Linux

We need to choose between **Rocky Linux** and **Debian** for our virtual machine.

## Rocky Linux
- Designed for stability and security, making it a great choice for production environments, especially in enterprise settings.
- Focuses on long-term support, offering a predictable platform for businesses.

## Debian
- Known for its flexibility and ease of use, making it an excellent option for beginners.
- Has a large community with extensive documentation, making it easier to find help and resources.
- Offers a broad range of packages and is renowned for its stability.

## Comparison

| Feature           | Rocky Linux                      | Debian                      |
|-------------------|-----------------------------------|-----------------------------|
| **Stability**     | Enterprise-grade stability        | Strong stability and flexibility |
| **Ease of Use**   | Best for advanced users and enterprises | More suitable for beginners  |
| **Package Manager**| `yum`/`dnf`                       | `apt`                        |

In summary, **Rocky Linux** is ideal for enterprise-level applications, while **Debian** is a better choice for beginners and general-purpose use, offering a more flexible and user-friendly experience.

## 3-4) Using VirtualBox + Configuring Your Virtual Machine (VM)

VirtualBox is open-source software that allows you to create and manage virtual machines on your computer. It supports a wide range of operating systems and is a popular choice for personal and professional use.
- Download and Install VirtualBox
- Creating a New Virtual Machine
- Configuring the Virtual Hard Disk
- Setting Up the VM

*For more detailed instructions on this part, refer to the guide by fcorvaro.*



## 5) Understanding Partitions

A partition is a logical subdivision of a physical disk. Imagine your hard drive as one big room: if you want to organize it better, you can divide it with walls into multiple rooms (partitions). Each partition can be used for different purposes (operating system, data, swap, etc.).

When you install an operating system, you can choose to:

- Use the entire disk without partitions (not recommended).
- Split the disk into multiple partitions to separate the operating system, data, and other things.

### Types of Partitions: Primary, Extended, Logical

Disks can be divided into 3 types of partitions:

### Primary (Primary Partition)

- This is the main partition where the operating system is installed.
- A disk can have up to 4 primary partitions.
- If you want more than 4 partitions, you need to use an extended partition.

### Extended (Extended Partition)

- Acts as a "container" for other partitions.
- It can contain multiple logical partitions.
- A disk can have only one extended partition.

### Logical (Logical Partition)

- These are created inside an extended partition.
- Linux can manage up to 15 logical partitions on a disk.
- You can use them to separate the operating system from data.

### Practical Example

Let's say you have a 100GB disk. You can divide it as follows:

- **Primary Partition (30GB)** → Contains Linux (/boot, /root, etc.)
- **Extended Partition (70GB)** → Contains multiple logical partitions:
  - **Logical 1 (20GB)** → /home (documents, user files)
  - **Logical 2 (10GB)** → /swap (virtual memory)
  - **Logical 3 (40GB)** → /var (logs, cache, etc.)

💡 **Why are partitions used in Born2BeRoot?**

- Separate `/boot` (500MB) to protect the system in case of issues.
- Create an encrypted logical partition for added security.





## 9) Commands you need to learn!

Let’s complete this guide with a list of essential commands that you will need to successfully complete the project.

## Basic commands

### Check that the UFW service is started
```bash
sudo systemctl status ufw
```
### Check that the SSH service is started

To check if SSH is enabled and running:
```bash
sudo systemctl status ssh
```

### Check what OS is used
```bash
cat /etc/os-release
```

### View information about users

```bash
cat /etc/passwd
```
Note: The `cat /etc/passwd` command displays the contents of the `/etc/passwd` file in Linux and Unix-like systems. This file contains information about system users, such as the username, password (in encrypted form), user ID (UID), group ID (GID), the user's full name, home directory, and default shell.``

### Verify user group membership
```bash
groups <username>
```

### View all groups in the system
```bash
cat /etc/group
```

### View partitions
```bash
lsblk
```

Note: The command is named `lsblk` because it lists all block devices (such as hard drives and partitions).

### Create a new user
```bash
sudo useradd <username>
```
### Create a new group
```bash
sudo groupadd <groupname>
```
### Assign a user to a group
```bash
sudo usermod -aG <groupname> <username>
```
Note: The usermod command is used to modify a user's properties. The -aG option appends the user to a group without removing them from other groups (a = append, G = Group).

## Hostname Management Commands
A hostname is a label or identifier assigned to a device (such as a computer, server, or virtual machine) on a network. It is used to distinguish that device from others within the same network or over the internet. The hostname is a part of the fully qualified domain name (FQDN) and helps in locating the device by humans and other systems.

For example, a device with the hostname myserver can be identified as part of a network, and its hostname can be used in place of an IP address to connect to it.

In addition to identifying the device on a network, the hostname also helps in configuring network services, such as SSH, HTTP, or file sharing.

### Change the hostname
```bash
sudo vim /etc/hostname
```
Note: After running this command, the new hostname will take effect immediately, but you may need to restart the system or restart the systemd service to fully apply the change.

### View hostname
```bash
hostnamectl
```
Note: The command is named `hostnamectl` because it is used to control the system's hostname and related settings.

## Sudo Management Commands
Sudo (short for "super user do") is a program for Unix and Unix-like systems that allows users to execute commands with the privileges of other users, typically the root user, while maintaining their own credentials. Originally, it was designed to allow commands to be run only as the superuser, but later versions enabled running commands as other users as well.

The configuration of sudo is managed in the /etc/sudoers file, which defines who can execute commands, which users they can act as, and what commands they can run. Some systems like macOS and Ubuntu install sudo by default, while others may require installation.

Sudo is primarily used to allow non-privileged users to run administrative commands securely without exposing the root password, improving security management. For example, in Ubuntu, users in the admin group can execute commands as root using their own credentials.

### ### Check the version of sudo
```bash
sudo --version
```
Note: In general, in Unix and Linux commands, long options are represented with two hyphens (--), while short options (a single hyphen followed by a letter or number) use one hyphen (-)

### Find the Path to the sudo Binary (if it's installed)
```bash
which sudo
```
Note: A binary is a compiled program file. It’s the machine code that the CPU understands and executes, but it's in a format that is not human-readable.

### Add a user to the sudo group
```bash
sudo usermod -aG sudo <username>
```
### Explain and show the usage of sudo with examples
```bash
sudo ls /root # Access a directory restricted to administrators
sudo apt update # Update packages os Debian/Ubuntu
sudo reboot # Restart the system
```
### Check if the /var/log/sudo/ folder exists
```bash
ls -l /var/log/sudo/
```
### Check if the file contains the history of commands used with sudo
```bash
cat /var/log/sudo/sudo.log # cat stands for "concatenate" and it's used to display the contents of a file
```
Note: the .log extension is only a naming convention to indicate that the file cotains log data. Why? Because Linux doesn't rely on file extensions like Windows does. You could name the file anything (sudo_log , sudo.txt , sudo-data) and it would still function the same way as long as the system is configured to write logs to it.

### Run a command with sudo and verify that the log is updated
```bash
sudo ls /root
catg /var/log/sudo/sudo.log
```
## 























## Sources:
https://github.com/f-corvaro/42.common_core/tree/main/01-born2beroot
https://github.com/vhacman/Born2beroot
https://iq.opengenus.org/virtualization/
https://it.wikipedia.org/wiki/Sudo
































