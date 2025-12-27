# Command Line Fundamentals

# TryHackMe – Command Line Notes

These are my personal notes from the **TryHackMe Command Line** rooms.  
They cover essential **Windows CMD, PowerShell, and Linux Shell** commands along with basic scripting concepts.

---

## Windows Command Line (CMD)

### System Information
- `ver` → Displays Windows version
- `systeminfo` → Shows detailed system information (OS, processor, memory)

### Help & Screen Control
- `help` → Displays help for commands
- `cls` → Clears the command prompt screen

### Network Commands
- `ipconfig` → Displays IP address, subnet mask, and default gateway
- `ipconfig /all` → Displays DNS servers and DHCP status
- `ping <target>` → Checks connectivity to a server
- `tracert <target>` → Displays the route taken by packets
- `nslookup` → Looks up a domain or host

### Network Statistics
- `netstat` → Displays current network connections
- `netstat -a` → Displays all active connections
- `netstat -b` → Shows programs using network ports
- `netstat -o` → Displays process IDs (PID)
- `netstat -n` → Shows numerical IP addresses and ports

### File and Directory Management
- `cd` → Shows current directory
- `dir` → Lists files in the directory
- `dir /a` → Displays hidden and system files
- `cd <directory>` → Changes directory
- `cd ..` → Moves up one directory level
- `mkdir <name>` → Creates a new directory
- `rmdir <name>` → Removes a directory
- `copy` → Copies files
- `move` → Moves files
- `del` → Deletes files

### Process and System Control
- `tasklist` → Lists running processes
- `taskkill /PID <pid>` → Terminates a process
- `shutdown /s` → Shuts down the system
- `shutdown /r` → Restarts the system

---

## Windows PowerShell

PowerShell is a powerful Windows tool used for **task automation and configuration management**.

### File and Directory Commands
- `Get-Content` → Displays file contents
- `Set-Location` → Changes the working directory
- `Get-ChildItem` → Lists files and directories
- `New-Item` → Creates files or directories
- `Remove-Item` → Deletes files or directories
- `Copy-Item` → Copies files

### System and Network Commands
- `Get-ComputerInfo` → Displays detailed system information
- `Get-LocalUser` → Lists local users
- `Get-NetIPConfiguration` → Network interface configuration
- `Get-NetIPAddress` → IP address details
- `Get-Process` → Displays running processes
- `Get-Service` → Displays service status
- `Get-NetTCPConnection` → Shows active TCP connections
- `Get-FileHash` → Generates a file hash

### Piping
Piping (`|`) sends the output of one command as input to another.

Example:
```powershell
'Get-Process | Sort-Object CPU'
