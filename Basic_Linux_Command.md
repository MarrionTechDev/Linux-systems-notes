# 🐧 Linux Shell Command Cheat Sheet

A categorized list of essential Linux commands for beginners and server users.

---

## Navigation

```bash
pwd        # Show current directory (where you are)
ls         # List files
ls -l      # Detailed list
ls -a      # Show hidden files
cd folder  # Change directory
cd ..      # Go up one level
cd ~       # Go to home directory
```
---

## File & Directory Management

```bash
mkdir name        # Create directory
rmdir name        # Remove empty directory
touch file        # Create empty file (dot extension to specify file type)
rm file           # Delete file
rm -r folder      # Delete folder recursively (deletes everything inside)
cp src dest       # Copy file/folder
mv src dest       # Move or rename
```

---

## Viewing Files

```bash
cat file          # Show full file
less file         # Scroll through file
head file         # First 10 lines
tail file         # Last 10 lines
tail -f file      # Live updates (logs)

```

---
## Searching

```bash
find . -name "file.txt"     # Find files
grep "text" file.txt        # Search inside file (by text)
grep -r "text" .            # Search recursively (by text)
history                     # List all commands typed
ctrl + r search    # Search through history for command
```

---
## User, Permissions & Ownership

```bash
whoami                   # show current user
id                       # shows the user ID, groups, and other details about the user.
sudo adduser username    # create a new user
su - username            switch users
chmod +x file            # Make executable for a file
chmod 755 file           # Set permissions for a file
chown user:group file    # Change owner of a file

```

---

## Processes

```bash
top           # Real-time processes running
q             # quit out of top view
ps aux        # List processes
kill PID      # Kill process using ID
htop          # Better process viewer (if installed)

```

---

## Package Management (Debian/Ubuntu)

```bash
sudo apt update          # Update package list
sudo apt upgrade         # Upgrade system
sudo apt install package # Install package

```

## Networking

```bash
ip a                # Show IP address
ping google.com     # Test connection
ssh user@ip         # Connect via SSH
curl url            # Fetch web data
```
---

## System Commands

```bash
sudo            # Run as admin
reboot          # Restart system
shutdown now    # Power off system
```
---

## Things to know

```bash
ctrl + l                # clear terminal (just push up)
command --help          # get more info on command
history                 # list all commands typed in the terminal
ctrl + r word/command   # search history for word/ command
clear                   # clear screen (delete previous line of code)
TAB                     # Auto-complete commands/files
↑                       # Command history
man command             # Manual/help page
