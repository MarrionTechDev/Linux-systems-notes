# Debian Installation Process Before, During, and After with Images

This is the machine I had lying around and decided to use as a Linux machine.

The folder contains images of the Dell D630 before, during, and after installing Debian 12.0.0 Linux Distro.

---

## Issues
- Had to reset the BIOS (System) password on boot. (used https://bios-pw.org/ ) [View Image](Images/20260212-135240.jpg)
- Reset the System Password in BIOS and set it to blank. (used the same password) [View Image](Images/20260212-141546.jpg)
  Made sure:
  - System Password = Disabled 
  - Set up Password = Disabled 
   
- The laptop had a Windows XP login password. (Ignored it since I would wipe it with Linux) [View Image](Images/20260212-143325.jpg)
- Battery wasn't charging. "The system cannot communicate with this battery." (Ignored it since I would use it as a server later with a charger.) [View Image](Images/20260212-145541.jpg)
- Upgraded both the HDD to an SSD. Original screws were too short (Ignored it since it still registered in BIOS and clicked in place after pushing it further)
  [View Image](Images/20260221-173022.jpg) [View Image](Images/20260221-182832.jpg) [View Image](Images/20260221-173901.jpg)
- Upgraded both RAM sticks from 2GB to 4GB. Memory stick didn't sit properly (Had to push until it clicked in place)
  [View Image](Images/20260221-173015.jpg) [View Image](Images/20260221-182805.jpg) [View Image](Debian Installation/Images/20260212_141411.jpg)
- Debian installation got stuck at "Load installer components from Installation media" (Was using a large flash drive as bootable USB. Using an 8GB flash drive worked later) [View Image](Images/20260216-174200.jpg)
- Remapped the "s" button to Left shift for typing using the terminal.

---

## Debian 12.0.0 Installation 
- Choose Language
- Configure the network. "Choose the one to use as the primary network interface during the installation" (Went with enp9s0 (Broadcom NetXtreme) with ethernet connection)
 - Enter the hostname for the system. (The name your machine uses on a network)
 - Removed the syn-2602-8000-xxxx-xxxx-xxxx-xxxx number router/ ISP before setting hostname (Hostname will show up as user@hostname:~$ later)
- Left Domain Name blank (This is just a standalone lab machine for myself)
- Set up users and passwords. Set a password for 'root', the system administrative account. (Left blank and continue to disable direct root login and get sudo privileges) [View Image](Images/20260221-192809.jpg)
  - Set up user accounts and passwords. Your Name, Username (no caps, no space, and simple: username@hostname:~$), and Password (Your sudo password. Make it strong and memorable)
- Configure the clock with the time zone
- Partition Disks 
  - Selected Guided – use entire disk [View Image](Images/20260221-195113.jpg)
  - Select the SSD (256.1 GB)
  - Partitioning scheme: All files in one partition
    [View Image](Images/20260221-200216.jpg) [View Image](Images/20260221-200345.jpg)
- Leave to install base system
  - The core Linux kernel is being copied
  - Essential packages are being installed
  - File system structure is being built
- Configure package manager
  - Country of mirror: United States
  - Mirror: deb.debian.org
  - Proxy: leave blank
- Configure popularity contest. Helps Debian developers see which packages are popular. (Optional. I choose no.

  ### Software selection
  - Desktop Environments(KDEs): GNOME, KDE Plasma, MATE, XFCE, LXDE, LXQt, GNOME Flashback
    - Heavy: GNOME, KDE
    - Lightweight: XFCE, LXDE, LXQt, MATE
    We can always install XFCE later manually.
  - Servers / Utilities
    - Web server → Apache/Nginx
    - SSH server → Very important for remote access
    - Standard system utilities → Always select
    - Print server → Skip
  - Was going to go for minimal CLI with standard system utilities and SSH server for focus on Linux machine learning
  - Accidentally selected Debian desktop and Gnome without checking ssh server (Uninstalled Gnome and installed XFCE and ssh server later)
    
- Configure grub pc. Install the GRUB boot loader on the primary drive
 - Lets your computer start Debian
 - Can handle multiple OSes (dual boot) if needed
 - Lets you choose kernel versions if multiple are installed
- Installation finished!!

---

## Updating the Package List, Remove GNOME and install XFCE (lightweight DE), and Installing SSH server

### Updating Package List
- Open up the termial (ctrl + Alt + T) or tty (Ctrl + Alt + F3)
- Type: sudo apt update
- Type your user password when prompted (This refreshes the package list)

### Install OpenSSH - server 
- Next, type: sudo apt install openssh-server
- “Do you want to continue? [Y/n]” → type Y and press Enter
  - SSH = Secure Shell
  - Lets you remotely connect to your D630 from another computer over the network
  - You can run commands, edit files, and manage your “server” without sitting in front of it
- Type: sudo systemctl enable ssh
- This enables SSH to start automatically with every boot of the computer
- Type: sudo systemctl start ssh
- This starts SSH right then.
  - Optional Quick Check
  - Type: sudo systemctl status ssh
  - Confirms SSH is running
  - Should show, Active: active (running)

### Removing GNOEM and Installing Lightweight XFCE
- Still in terminal
- Type: sudo apt remove --purge gnome-shell gdm3 gnome-session
- Do you want to continue? [Y/n] → type Y and press Enter
 - After, Type: sudo apt autoremove
 - This removes the leftover dependencies GNOME needed
 - Frees even more space
- If you have a black blank screen with a beeping cursor at the Left top after this, press Ctrl + Alt + F3 to log back in (if you were using tty)
- Type: sudo apt install xfce4 lightdm
- If asked, "Multiple display managers installed. Use the arrow keys to select lightdm
- Press Enter
 - Optional to ensure XFCE will show the login screen after boot.
 - Type: sudo systemctl enable lightdm
 - Then: sudo systemctl start lightdm
- Once installation is complete: Type: sudo reboot
- This reboots the system
- You should see the XFCE desktop load. [View Image](Images/01-IMG.jpeg)
    
