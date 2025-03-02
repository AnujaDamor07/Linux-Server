<h1 align="center">Basic Linux Commands</h1>

## **File and Directory Management**  

- **Show the current working directory:**  
  ```bash
  pwd
  ```
  
- **List all files and directories in the current directory:**  
  ```bash
  ls
  ```

- **List files with detailed information (permissions, owner, size, date modified):**  
  ```bash
  ls -l
  ```

- **List all files, including hidden ones (files starting with `.`):**  
  ```bash
  ls -a
  ```

- **List files with human-readable sizes (KB, MB, GB):**  
  ```bash
  ls -lh
  ```

- **List all files and directories recursively, including subdirectories:**  
  ```bash
  ls -R
  ```

- **Change to a specified directory:**  
  ```bash
  cd directory_name
  ```

- **Move up one directory level:**  
  ```bash
  cd ..
  ```

- **Move to the root directory:**  
  ```bash
  cd /
  ```

- **Create a new directory:**  
  ```bash
  mkdir new_folder
  ```

- **Create multiple nested directories in one command:**  
  ```bash
  mkdir -p parent/child/grandchild
  ```

- **Delete an empty directory:**  
  ```bash
  rmdir foldername
  ```

- **Delete a specific file:**  
  ```bash
  rm file.txt
  ```

- **Delete a directory and all its contents forcefully:**  
  ```bash
  rm -rf foldername
  ```

## **File Operations**  

- **Create an empty file:**  
  ```bash
  touch filename.txt
  ```

- **Display the contents of a file:**  
  ```bash
  cat filename.txt
  ```

- **Create and edit a file (press `Ctrl + D` to save):**  
  ```bash
  cat > filename.txt
  ```

- **Copy a file to a specified location:**  
  ```bash
  cp file.txt /path/to/destination/
  ```

- **Copy an entire directory and its contents:**  
  ```bash
  cp -r source_folder destination_folder
  ```

- **Move or rename a file or directory:**  
  ```bash
  mv oldname.txt newname.txt
  ```

- **Create a symbolic (soft) link to a file or directory:**  
  ```bash
  ln -s /path/to/target linkname
  ```

- **Create a hard link to a file:**  
  ```bash
  ln /path/to/file hardlinkname
  ```

## **System Information**  

- **Show the current system date and time:**  
  ```bash
  date
  ```

- **Display how long the system has been running:**  
  ```bash
  uptime
  ```

- **Show Linux kernel details:**  
  ```bash
  uname -a
  ```

- **Display CPU information:**  
  ```bash
  lscpu
  ```

- **List all connected USB devices:**  
  ```bash
  lsusb
  ```

- **Display PCI hardware information:**  
  ```bash
  lspci
  ```

- **List all storage devices and partitions:**  
  ```bash
  lsblk
  ```

## **User and Session Information**  

- **Show the currently logged-in user:**  
  ```bash
  whoami
  ```

- **List all users currently logged into the system:**  
  ```bash
  who
  ```

- **Show detailed user login information:**  
  ```bash
  who -a
  ```

- **Display active users and their running processes:**  
  ```bash
  w
  ```

- **Show user ID and group memberships:**  
  ```bash
  id
  ```

## **Network and Host Information**  

- **Show the system hostname:**  
  ```bash
  hostname
  ```

- **Display the system’s IP address:**  
  ```bash
  hostname -I
  ```

- **Show network configuration details (IP, MAC address, etc.):**  
  ```bash
  ifconfig
  ```

- **Display the system’s DNS configuration:**  
  ```bash
  cat /etc/resolv.conf
  ```

- **Show the network routing table:**  
  ```bash
  route -n
  ```

## **Process and Memory Information**  

- **List currently running processes:**  
  ```bash
  ps aux
  ```

- **Display real-time system statistics and resource usage:**  
  ```bash
  top
  ```

- **Show memory and swap usage in a human-readable format:**  
  ```bash
  free -h
  ```

## **Terminal Utilities**  

- **Clear the terminal screen:**  
  ```bash
  clear
  ```

- **Show the name of the terminal device:**  
  ```bash
  tty
  ```

- **Display command history:**  
  ```bash
  history
  ```

- **Show the calendar for the current month:**  
  ```bash
  cal
  ```

- **Show the calendar for a specific year:**  
  ```bash
  cal 2025
  ```

## **System Shutdown and Reboot**  

- **Shut Down the System**  
  ```bash
  shutdown -P now
  ```

- **Restart the System**  
  ```bash
  shutdown -r now
  ```

- **Cancel a Scheduled Shutdown**  
  ```bash
  shutdown -c
  ```

- **Alternative Shutdown Commands**  
  - `poweroff` - Turns off the system.  
  - `init 0` - Shuts down the system.  
  - `init 6` - Restarts the system.  
