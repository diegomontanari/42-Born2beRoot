# Born2BeRoot Project Guide 🚀

This README is not a complete guide for completing the Born2BeRoot project. 

In this guide, we will go over everything you need to know to complete the project and provide a step-by-step list of tasks to help you finish it.

For a full guide, I recommend checking out the repository by fcorvaro (I'll leave the link at the bottom in the sources).

Let's get started!

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
1. [Understanding Virtual Machines](#1-understanding-virtual-machines)
2. [Debian vs CentOS and Rocky Linux](#2-debian-vs-centos-and-rocky-linux)
3. [Using VirtualBox and Configuring Your Virtual Machine (VM)](https://github.com/diegomontanari/42-Born2beRoot/blob/main/README.md#3-using-virtualbox--configuring-your-virtual-machine-vm)
4. [Understanding Partitions](https://github.com/diegomontanari/42-Born2beRoot/blob/main/README.md#4-understanding-partitions)
5. [Commands You Need to Learn](https://github.com/diegomontanari/42-Born2beRoot/blob/main/README.md#5-commands-you-need-to-learn)
   - [Basic commands](https://github.com/diegomontanari/42-Born2beRoot/blob/main/README.md#basic-commands)
   - [Hostname Management Commands](https://github.com/diegomontanari/42-Born2beRoot/blob/main/README.md#hostname-management-commands)
   - [Sudo Management Commands](https://github.com/diegomontanari/42-Born2beRoot/blob/main/README.md#sudo-management-commands)
   - [UFW Management Commands](https://github.com/diegomontanari/42-Born2beRoot/blob/main/README.md#ufw-management-commands)
   - [SSH Management Commands](https://github.com/diegomontanari/42-Born2beRoot/blob/main/README.md#ssh-management-commands)
6. [Differences Between apt and aptitude](https://github.com/diegomontanari/42-Born2beRoot/blob/main/README.md#6-differences-between-apt-and-aptitude)
7. [What is AppArmor?](https://github.com/diegomontanari/42-Born2beRoot/blob/main/README.md#7-what-is-apparmor)
8. [What is LVM?](https://github.com/diegomontanari/42-Born2beRoot/blob/main/README.md#8-what-is-lvm)
9. [Understanding cron and crontab](#9-understanding-cron-and-crontab)
10. [Sources](https://github.com/diegomontanari/42-Born2beRoot/blob/main/README.md#10-sources)

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

## 3) Using VirtualBox + Configuring Your Virtual Machine (VM)

VirtualBox is open-source software that allows you to create and manage virtual machines on your computer. It supports a wide range of operating systems and is a popular choice for personal and professional use.
- Download and Install VirtualBox
- Creating a New Virtual Machine
- Configuring the Virtual Hard Disk
- Setting Up the VM

*For more detailed instructions on this part, refer to the guide by fcorvaro.*

![virtualize-virtualize-everything](https://github.com/user-attachments/assets/cf8d02c8-68eb-4327-b734-7531975a4f10)

## 4) Understanding Partitions

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





## 5) Commands you need to learn!

Let’s complete this guide with a list of essential commands that you will need to successfully complete the project.

## Basic commands

### Check that the UFW service is started
```bash
sudo ufw status
```
### Check that the SSH service is started

To check if SSH is enabled and running:
```bash
sudo systemctl status ssh
```
Note: **ssh** is a service managed by **systemd**, while **ufw** is **independent**. 
This means that:
- **If a service is managed by systemd**: sudo systemctl  status <service>
- **If a service is independent**: sudo <service> status
Basically, **if the service is independent, its name comes before** the word "status"; **if it is managed by systemd, the name comes after** "systemctl status".


### Check what OS is used
```bash
cat /etc/os-release
```
Note:
cat: It stands for "concatenate" and is used to display the contents of a file.
/etc: This is a directory (folder) that holds system configuration files in Linux-based systems.
os-release: This file contains information about the operating system, such as its name, version, and other details about the distribution.

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
 
Note: The command is named `lsblk` (stands "list block") and it is used to list all block devices in the system, such as hard drives, SSDs, and their partitions.

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

### Check the version of sudo
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
Note: 
The usermod command is used to modify a user’s properties on a Linux system. Specifically:
The -a option stands for "append" and ensures that the user is added to the specified group without being removed from any existing groups.
The -G option is used to specify the groups that the user should be part of.
So, the command sudo usermod -aG <groupname> <username> adds the specified user to the <groupname> group, keeping the user's membership in other groups intact.

### Group Verification and Info
To verify if the group exists, you can use the command:

```bash
getent group Users42
```
If the group exists, this command will return information about it.


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
Note: 
/var is a directory in the Linux filesystem that stands for "variable". It is used to store files that are expected to change in size or content over time.
/var/log is a directory that stores system log files. These log files contain information about system events, user activities, and error messages. The log files help administrators troubleshoot and monitor the system's performance.

### Check if the file contains the history of commands used with sudo
```bash
cat /var/log/sudo/sudo.log # cat stands for "concatenate" and it's used to display the contents of a file
```
Note: the .log extension is only a naming convention to indicate that the file cotains log data. Why? Because Linux doesn't rely on file extensions like Windows does. You could name the file anything (sudo_log , sudo.txt , sudo-data) and it would still function the same way as long as the system is configured to write logs to it.

## Enable Logging for Sudo (if /var/log/sudo/sudo.log does not exist)

To enable logging for sudo commands, you need to configure the sudoers file and specify the location where the logs should be stored.

### Creating the Logging Directory

Create a dedicated directory in `/var/log/` to log each sudo command's input and output:

```bash
sudo mkdir /var/log/sudo
```

### Edit the sudoers file

Use the `visudo` command to safely edit the sudoers file. This command prevents syntax errors.

```bash
sudo visudo
```

#### Add the logging configuration

Locate the Defaults section in the sudoers file and add the following lines to enable logging:

```bash
Defaults    log_output
Defaults    logfile="/var/log/sudo/sudo.log"
```

- `log_output`: Enables logging of all commands executed with sudo, capturing both input and output.
- `logfile`: Specifies the file where sudo command logs will be stored.

Save the changes and exit the editor. If using `visudo`, press `ESC`, type `:wq`, and press `Enter`.

### Verify the logging configuration

To ensure that logging is enabled, run a sudo command and check the log file:

```bash
sudo ls /root
cat /var/log/sudo/sudo.log
```

You should see the executed command logged in the specified file.

**Note:** Ensure that the `/var/log/sudo/` directory exists and has the appropriate permissions for logging.

### Difference Between System Logs (Audit) and Sudo Logs

When we talk about system logs, there are two main methods for viewing information related to commands executed with `sudo`:

1. **System Logs (Audit) via `journalctl`:**
   - **`journalctl`:** Logs system-wide events, including `sudo` sessions, errors, and other related activities.
   - To view the logs related to `sudo`, you can use:
     ```bash
     sudo journalctl | grep sudo
     ```
   - This command will show the system logs containing the word "sudo," including details about the user who executed the command, the time, and the type of command.

2. **Sudo Logs (Specific Log File) via `/var/log/sudo/sudo.log`:**
   - **`/var/log/sudo/sudo.log`:** Logs only the specific `sudo` commands executed and their output, based on the configuration in the `sudoers` file.
   - To view the log, you can use:
     ```bash
     sudo cat /var/log/sudo/sudo.log
     ```
   - This command will show a linear log of the commands executed via `sudo` (if correctly configured), and will include details like the command run and the user who initiated the session.

### Run a command with sudo and verify that the log is updated
```bash
sudo ls /root
cat /var/log/sudo/sudo.log
```

## UFW Management Commands

UFW (Uncomplicated Firewall) is a user-friendly front-end for managing iptables, designed to simplify firewall configuration in Linux systems. It allows users to manage network traffic rules easily by enabling or disabling ports and protocols.

UFW is typically installed by default on Ubuntu and other Debian-based systems, but if it's not installed, it can be manually installed.

### Check if UFW is Installed
```bash
sudo ufw status
```
If UFW is not installed, install it with:
```bash
sudo apt update && sudo apt install ufw -y
```
*Note: The `-y` flag automatically answers 'yes' to any prompts during the installation process, allowing the command to proceed without user intervention.*

### Check if UFW is Enabled
```bash
sudo ufw status
```
If it is inactive, enable it with:
```bash
sudo ufw enable
```

### List Active UFW Rules
```bash
sudo ufw status numbered
```
This command displays all active firewall rules in a numbered format.

### Add a Rule to Allow Port 8080
```bash
sudo ufw allow 8080
```

### Verify the Rule for Port 8080
```bash
sudo ufw status numbered
```
This command ensures the rule was added correctly.

### Delete the Rule for Port 8080
First, find the rule number:
```bash
sudo ufw status numbered
```
Then delete the rule using its number:
```bash
sudo ufw delete <rule_number>
```
Replace `<rule_number>` with the correct number from the listed rules.

---

## SSH Management Commands

SSH (Secure Shell) is a protocol that allows secure remote access to systems over an encrypted connection. It is commonly used for remote administration and file transfers between systems.

### Check if SSH is Installed
```bash
dpkg -l | grep openssh-server
```
*Note: `dpkg` is the package management system for Debian-based distributions, and `grep` is a command-line tool used to search for specific text within files or outputs. Here, `dpkg -l` lists installed packages, and `grep openssh-server` filters the list to check if the OpenSSH server is installed.*

If SSH is not installed, install it with:
```bash
sudo apt update && sudo apt install openssh-server -y
```

### Check if SSH is Running
```bash
sudo systemctl status ssh
```
If SSH is not active, start the service with:
```bash
sudo systemctl start ssh
```

### Verify SSH Port Configuration
```bash
sudo cat /etc/ssh/sshd_config | grep Port
```
Note: we need to modify 2 files: 1) /etc/ssh/sshd_config , which is the server-side configuration file for SSH (here we need to change both the port and set PermitRootLogin no) and /etc/ssh/ssh_config , the client-side configuration file for SSH (here we just need to change the port)



By default, SSH runs on port 22. To change it to port 4242, edit the configuration file:
```bash
sudo vim /etc/ssh/sshd_config
```
Find the line:
```
Port 22
```
Change it to:
```
Port 4242
```
Save and exit (`ESC`, `:wq`, `Enter`). Restart SSH to apply changes:
```bash
sudo systemctl restart ssh
```

### Create a New User for SSH Access
```bash
sudo adduser new_user
```

### Log in via SSH with the New User
```bash
ssh new_user@localhost -p 4242
```

### Set Up SSH Key Authentication
Generate an SSH key pair:
```bash
ssh-keygen -t rsa -b 4096
```
Copy the key to the server:
```bash
ssh-copy-id -p 4242 new_user@localhost
```

### Ensure Root Login is Disabled
Check the configuration:
```bash
sudo cat /etc/ssh/sshd_config | grep PermitRootLogin
```
If necessary, edit the file:
```bash
sudo vim /etc/ssh/sshd_config
```
Ensure the line is set to:
```
PermitRootLogin no
```
Note: the line PermitRootLogin no in the SSH configuration file (/etc/ssh/sshd_config) is used to disable direct root login over SSH. This is a security measure to prevent unauthorized access to the root account on a server. If someone were to compromise a regular user account and gain SSH access, they would not be able to directly escalate to root privileges unless they can successfully execute sudo or similar commands.

Save and restart SSH:
```bash
sudo systemctl restart ssh
```

### Initiate an SSH connection to localhost on a custom port
```bash
ssh dmontana@localhost -p 4241  # ssh (Secure Shell) is used to securely log into a remote machine
```
Note: The localhost address (127.0.0.1) means the connection is being made to the same machine. The -p flag specifies a non-default SSH port (4241 instead of the default 22). This is useful when an SSH server is configured to listen on a different port for security reasons.

## Difference between the ssh_config and sshd_config files in SSH configuration:

- ssh_config: This file is the **client-side configuration file for SSH**. It is used to configure settings for outgoing SSH connections from a client to a server. The settings here affect how the SSH client behaves when it tries to connect to a remote server (e.g., which SSH protocol version to use, whether to enable compression, default user, etc.). It is usually found in /etc/ssh/ssh_config or ~/.ssh/config.

- sshd_config: This file is the **server-side configuration file for SSH**. It is used to configure settings on the SSH server that listens for incoming SSH connections. The settings here affect how the server handles client connections (e.g., which authentication methods are allowed, which port to listen on, access control, etc.). It is usually located in /etc/ssh/sshd_config.

To summarize:

ssh_config: Configures client-side behavior.
sshd_config: Configures server-side behavior.

Simpler explanation:

- ssh_config: This is the configuration file for the SSH client. It controls **how your computer connects to other remote computers via SSH** (like which settings to use when you connect).

- sshd_config: This is the configuration file for the SSH server. It controls **how the remote computer allows incoming SSH connections** (like which methods it accepts for login).

In short:

- ssh_config: for setting up how your computer connects to others.
- sshd_config: for setting up how others connect to your computer.

# Linux Security Configuration Guide

## Sudo Configuration

### Creating the Sudo Configuration File

Create a file in the `/etc/sudoers.d/` directory to store the sudo policy:

```bash
sudo touch /etc/sudoers.d/sudo_config
```

This file will contain all the custom sudo policies we want to implement for enhanced security.

### Editing the Sudo Configuration File

Open the file created in the first step:

```bash
sudo vim /etc/sudoers.d/sudo_config
```

### Adding Sudo Policies

Write the following lines into the file:

```
Defaults passwd_tries=3
Defaults badpass_message="Custom error message"
Defaults logfile="/var/log/sudo/sudo_config"
Defaults log_input, log_output
Defaults iolog_dir="/var/log/sudo"
Defaults requiretty
Defaults secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/snap/bin"
```

Each of these settings serves a specific security purpose:

- `passwd_tries=3`: Limits the total attempts allowed for entering the sudo password
- `badpass_message="Custom error message"`: Displays a custom message when an incorrect password is entered
- `logfile="/var/log/sudo/sudo_config"`: Specifies the path where sudo logs will be stored
- `log_input, log_output`: Enables logging of both command input and output
- `iolog_dir="/var/log/sudo"`: Defines where input/output logs will be stored
- `requiretty`: Enhances security by requiring a TTY for sudo execution
- `secure_path`: Lists directories included in the secure path for sudo operations

## Password Policy Configuration

### Editing the login.defs File

Open the login.defs file for editing:

```bash
sudo vim /etc/login.defs
```

### Setting the Password Parameters

Update the following parameters in the file:

```
# Change from
PASS_MAX_DAYS 99999
# To
PASS_MAX_DAYS 30

# Change from
PASS_MIN_DAYS 0
# To
PASS_MIN_DAYS 2
```

These parameters control password aging:

- `PASS_MAX_DAYS`: Maximum number of days until password expiration
- `PASS_MIN_DAYS`: Minimum number of days before a password can be changed
- `PASS_WARN_AGE`: Number of days before password expiration when warnings begin

### Installing the libpam-pwquality Package

Install the package that will enforce password quality:

```bash
sudo apt install libpam-pwquality
```

Confirm the installation when prompted.

### Editing the common-password File

Open the common-password file for editing:

```bash
sudo vim /etc/pam.d/common-password
```

### Updating Password Quality Settings

Find the line containing `retry=3` and add the following parameters immediately after it on the same line:

```
minlen=10 ucredit=-1 dcredit=-1 lcredit=-1 maxrepeat=3 reject_username difok=7 enforce_for_root
```

Each parameter enhances password security:

- `minlen=10`: Requires passwords to contain at least 10 characters
- `ucredit=-1`: Requires at least one uppercase letter
- `dcredit=-1`: Requires at least one digit
- `lcredit=-1`: Requires at least one lowercase letter
- `maxrepeat=3`: Prevents the same character from repeating more than three times consecutively
- `reject_username`: Prohibits passwords containing the username
- `difok=7`: Requires at least seven different characters from the previous password
- `enforce_for_root`: Applies this password policy to the root user as well

## 6) Differences Between `apt` and `aptitude`

`aptitude` provides both a command-line and a text-based interface for package management, whereas `apt` is strictly command-line. `aptitude` is not installed by default and must be added using `apt`.

### Key Differences:
- `aptitude` includes a visual interface, while `apt` is purely command-line.
- When encountering package conflicts, `aptitude` suggests resolutions, while `apt` does not.
- `aptitude` can fetch and display Debian changelogs.
- `apt` requires more Linux package management knowledge, while `aptitude` is more user-friendly due to its interface.

## 7) What is AppArmor?
AppArmor (Application Armor) is a Linux security module that restricts program capabilities using per-program profiles.

Restricting program capabilities is essential for security, as it minimizes the potential damage malicious or compromised applications can cause.

For example, a web browser should only have access to the internet and user-downloadable files, but not system-critical files or processes. Without restrictions, a compromised browser could modify system configurations or access sensitive data.

Doesn't this happen automatically?

Not always. Some operating systems implement default restrictions, but many applications have broader permissions than necessary. AppArmor allows you to define specific rules to limit a program's actions. For example, on a Linux distribution without AppArmor active, a browser could access sensitive files if an exploit compromises it. With AppArmor, however, you can prevent the browser from accessing system folders or executing dangerous commands in advance.

## 8) What is LVM?
LVM (Logical Volume Manager) allows flexible management of logical volumes, enabling dynamic resizing and efficient storage allocation.

## 9) Understanding cron and crontab

**Cron** and **Crontab** are tools that allow you to schedule tasks to run automatically on a Linux or Unix-based operating system.

1. **Cron** is a program that runs in the background and handles executing tasks at specified intervals, like running a script every day at 7 AM.

2. **Crontab** is the file or command you use to tell Cron what tasks to run and when to run them. It's like a to-do list where you specify:
   * **What** should be done (e.g., running a command or script).
   * **When** it should be done (e.g., every day, every hour, every Monday, etc.).

The tricky part is writing the correct syntax, which consists of 5 fields indicating:
* **Minutes** (0-59)
* **Hours** (0-23)
* **Day of the month** (1-31)
* **Month** (1-12)
* **Day of the week** (0-6, where 0 is Sunday)

Example:
Let's say you want to run a script every day at 7 AM. The line in your **crontab** would look like this:

```
0 7 * * * /path/to/your/script.sh
```

This means:
* `0` minutes
* `7` hours
* `*` every day of the month
* `*` every month
* `*` every day of the week

Basically, every day at 7:00 AM, Cron will execute the script you specified.

To use **crontab**, you need to:
* **Open the crontab file** with the command `crontab -e`.
* **Add your line** with the schedule you want.
* Save and exit.

Cron will take care of the rest!

## Scheduling Tasks for Multiple Days Per Week

Let's say you need to run a database backup script every Monday, Wednesday, and Friday at 9:30 PM. Here's how you would set up the crontab entry:

```
30 21 * * 1,3,5 /path/to/database-backup.sh
```

This command breaks down as follows:
* `30` minutes (30 minutes past the hour)
* `21` hours (9 PM in 24-hour format)
* `*` every day of the month
* `*` every month
* `1,3,5` only on Monday (1), Wednesday (3), and Friday (5)

When you use commas in any field, it creates a list of values for which the command should run. You could similarly schedule tasks for specific months (e.g., `1,6,12` for January, June, and December) or specific days of the month.

Remember that whenever your schedule needs to accommodate multiple specific times or dates, using commas to separate the values is the way to go. This makes cron incredibly flexible for creating complex scheduling patterns for your automated tasks.




## 10) Sources:
https://github.com/f-corvaro/42.common_core/tree/main/01-born2beroot  
https://github.com/vhacman/Born2beroot  
https://iq.opengenus.org/virtualization/  
https://it.wikipedia.org/wiki/Sudo  

