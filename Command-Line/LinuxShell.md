# TryHackMe – Linux Shell Notes

These notes cover the **Linux Shell fundamentals** from TryHackMe.  
They focus on navigation, file handling, searching, permissions, and basic shell concepts.

---

## Linux Shell Basics

### Shell Overview
A shell is an interface that allows users to interact with the operating system by executing commands.

### Available Shells
- `cat /etc/shells` → Lists all available shells on the system

---

## Navigation Commands

### Directory Navigation
- `pwd` → Displays the current working directory
- `cd <directory>` → Changes to the specified directory
- `cd ..` → Moves up one directory level
- `cd ~` → Moves to the home directory

### Listing Files
- `ls` → Lists files and directories
- `ls -a` → Shows hidden files
- `ls -l` → Long listing format
- `ls -la` → Long listing including hidden files

---

## File and Directory Management

### Creating Files and Directories
- `touch <filename>` → Creates an empty file
- `mkdir <directory>` → Creates a new directory

### Removing Files and Directories
- `rm <filename>` → Deletes a file
- `rm -r <directory>` → Deletes a directory recursively

### Copying and Moving
- `cp <source> <destination>` → Copies files
- `mv <source> <destination>` → Moves or renames files

---

## Viewing File Contents

### Displaying Files
- `cat <filename>` → Displays file content
- `less <filename>` → View file content page by page
- `head <filename>` → Displays first 10 lines
- `tail <filename>` → Displays last 10 lines

---

## Searching and Filtering

### Searching Text
- `grep <word> <file>` → Searches for a word in a file
- `grep -i <word> <file>` → Case-insensitive search
- `grep -r <word> <directory>` → Recursive search

---

## Permissions and Ownership

### File Permissions
- `ls -l` → View file permissions
- `chmod +x <file>` → Makes a file executable
- `chmod 755 <file>` → Sets read/write/execute permissions

### Ownership
- `chown user:group <file>` → Changes file ownership

---

## Piping and Redirection

### Piping
- Piping (`|`) sends output of one command as input to another.

## Shebang
- Every script should start with a shebang.
- A shebang is a combination of characters added at the beginning of a script to specify the shell interpreter.

## Script Concepts
- Variables → Used to store values inside a script
- Loops → Used to repeat actions more than one time
- Conditional Statements → Executes code only if a condition is met
- Comments → Help in understanding the code

## Script Permissions
- 'chmod +x <script-name>' → Gives executable permission to a script
