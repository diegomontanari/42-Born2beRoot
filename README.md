# Born to be Root 🚀  

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
3-4) Using VirtualBox + Configuring Your Virtual Machine (VM)
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

# Let's start! 🚀

![3e494f8437e6b23acafecb608036edd7](https://github.com/user-attachments/assets/d7fb338f-248d-4a26-8e2b-424cf46c1434)

## 1) Understanding Virtual Machines
A virtual machine (VM) is a simulated computer that runs within a physical computer. It functions as an isolated system, complete with its own operating system, memory, storage, and processing resources, all managed independently from the host system. In simpler terms, it's an emulation of a computer system that enables an operating system ('guest') to run as an application within another operating system ('host').

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

## 3. Types of Partitions: Primary, Extended, Logical

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





































![virtualize-virtualize-everything](https://github.com/user-attachments/assets/cf8d02c8-68eb-4327-b734-7531975a4f10)



