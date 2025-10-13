My Journey Through TryHackMe's Cybersecurity 101 Path:

A write-up covering my progress and key learnings from the initial modules, up to Linux Fundamentals 2.
Introduction
Welcome to my write-up! I'm documenting my journey through the TryHackMe Cybersecurity 101 pathway to solidify my knowledge and share what I've learned. This document covers my hands-on experience with foundational cybersecurity concepts and my first steps into the powerful world of the Linux command line.

Module 1: Introduction to Cybersecurity
This room provided a high-level overview of the cybersecurity landscape. It introduced the core concepts of why cybersecurity is important and the different roles within the industry.

Core Concepts
Offensive Security (Red Team): This involves ethically hacking systems to find and report vulnerabilities before malicious actors can exploit them.

Defensive Security (Blue Team): This focuses on protecting an organization's systems from threats by monitoring, detecting, and responding to attacks.

Module 2: Linux Fundamentals Part 1
This was my first hands-on experience with the Linux terminal. The module focused on basic navigation and file interaction, which are essential skills for any cybersecurity professional.

Core Concepts & Key Commands
Interacting with a Linux system is done through the Command-Line Interface (CLI). I learned some of the most fundamental commands:

ls: Lists the contents of the current directory.

cd: Changes the current directory.

cat: Displays the entire content of a file directly in the terminal.

pwd: Prints the current working directory, which is incredibly helpful for staying oriented in the filesystem.

Module 3: Linux Fundamentals Part 2
This module built directly on the first one, introducing more advanced and powerful concepts for interacting with the system both remotely and locally.

Connecting Remotely with SSH
SSH (Secure Shell) is the primary way to connect to a Linux machine remotely over a network. It provides a secure, encrypted command-line session.

The command syntax is ssh username@<machine_ip>. For example, to log in to a machine at 10.10.10.2 as the user tryhackme, I would run:

ssh tryhackme@10.10.10.2

After providing the correct password, I have full terminal access to the remote machine.

Advancing Command Usage: Flags and man Pages
Commands can be modified with flags (or switches) to change their behavior. For example, with ls:

ls -l: Provides a "long listing" format with details like permissions, owner, and size.

ls -a: Shows all files, including hidden files that start with a dot (.).

These can be combined: ls -la.

To learn about all the available flags for a command, I used the built-in manual pages with the man command. For example, man ls opens a detailed document explaining every option for the ls command.

More Essential Filesystem Commands
I learned several new commands for creating and managing files and directories:

touch <filename>: Creates a new, empty file.

mkdir <directoryname>: Creates a new directory.

cp <source> <destination>: Copies a file or directory.

mv <source> <destination>: Moves a file or directory. This is also used to rename files (e.g., mv old.txt new.txt).

rm <filename>: Permanently deletes a file. To delete an empty directory, rmdir is used, but rm -r will recursively delete a directory and all its contents.

file <filename>: Determines the type of a given file.

A Quick Look at File Permissions & Switching Users
A core concept in Linux is file permissions. Every file has permissions for three types of users: the Owner, the Group, and Other (everyone else). The permissions are:

Read (r): The ability to view the contents of a file.

Write (w): The ability to change the contents of a file.

Execute (x): The ability to run the file (if it's a script or program).

To switch users, I used the su (substitute user) command. Running su <username> and entering that user's password logs you in as them in the current terminal session. This is especially important when needing to perform actions as the administrative root user.

Understanding the Linux Filesystem Layout
The Linux filesystem is a hierarchy starting from the root directory (/). Certain directories have specific purposes and are critical for the system's operation.

/root: The personal home directory for the administrative superuser, root.

/home: Contains the personal directories for all regular users.

/etc: Holds all system-wide configuration files for the OS and installed applications.

/var: Stores "variable" data that changes often, most importantly logs in /var/log.

/tmp: A world-writable directory for temporary files. Data here is often deleted on reboot.

Summary of Key Learnings
The fundamental difference between Red Teaming and Blue Teaming.

Basic Linux CLI navigation (ls, cd, pwd) and file interaction (cat).

Connecting to a remote machine securely using SSH.

Modifying command behavior with flags and using man pages to learn about them.

File and directory manipulation with touch, mkdir, cp, mv, and rm.

A foundational understanding of Linux file permissions (read, write, execute) and how to switch users with su.

The purpose of key directories in the Linux filesystem like /etc, /var, and /home.

Conclusion & Next Steps
These first few modules have been a fantastic introduction. Getting comfortable with the Linux command line was challenging at first, but it's clear how powerful it is. I'm excited to move on to the next modules and dive deeper into networking and web application security.