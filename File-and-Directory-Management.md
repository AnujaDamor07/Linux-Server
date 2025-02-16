##**File and Directory Management**

•	**Pwd**    :- **Displays your current working directory and shows the full path of the directory.**


•	**ls -l**  :- **Lists files and directories in a detailed (long) format, showing permissions, ownership, size, and modification date.**


•	**ls -a**  :- **Lists all files, including hidden ones (those starting with a dot .).**


•	**ls -h**  :- **Shows file sizes in human-readable format (e.g., KB, MB).**


•	**ls -R**  :- **Lists files and directories recursively.**  


•	           :- **. refers to the current directory.**


•	           :- **.. refers to the parent directory.**


•	           :- **.hidden file is an example of a hidden file**


•	**cd**     :- **Changes your current directory.**


•	**cd ..**  :- **Moves you up one directory level.**


•	**mkdir**  :- **Creates a new directory.**


•	**rkdir**  :- **Removes an empty directory.**


•	**rm**     :- **Removes files or directories.**


•	**rm -rf** :- **Forcefully removes directories and their contents.**



##**File Operations**


•	**touch**       :- **Creates an empty file or updates the timestamp of an existing file.**


•	**cat**         :- **Displays the contents of a file.**


•	**cp**          :- **Copies files or directories.**


•	**mv**          :- **Moves or renames files or directories.**


•	**ls -s**       :- **Creates a symbolic link (or soft link), which is a reference to the original file.**


•	**ln**          :- **Creates a hard link to a file.**



##**System Information**  


•	**date**          :- **shows the current system date and time.**


•	**uptime**        :- **displays how long the system has been running.**


•	**vuname -a**       :- **shows detailed linux kernel information.**


•	**lscpu**         :- **displays cpu architecture and details.**


•	**lsusb**         :-  **lists connected usb devices.**


•	**lspci**         :- **lists pci hardware (e.g., network card, graphics card).**


•	**lsblk**         :- **Lists block devices and partitions.**



**User and Session Information** 


•	**whoami**      :- **Shows the currently logged-in user.**


•	**Who**         :- **Lists users currently logged into the system.**


•	**Id**          :- **Displays user and group ID along with group memberships.**


•	**W**           :- **Shows who is logged in and their active processes.**



##**Network and Host Information**


•	**hostname**             :- **displays or sets the system’s hostname.**


•	**hostname -i**          :- **shows the system’s ip address.**


•	**ifconfig**             :- **displays network interface configuration (deprecated in favor of ip command).**


•	**cat /etc/resolv.conf** :- **displays dns configuration.**


•	**route -n**             :- **Shows the routing table.**



##**Process and Memory Information**


•	**ps aux**      :- **Displays detailed information about all running processes.**


•	**Top**         :- **Shows real-time system processes and resource usage.**


•	**free -h**     :- **Displays memory and swap usage in human-readable format.**



##**Terminal Utilities**


•	**clear**   :- **clears the terminal screen.**


•	**tty**     :- **shows the terminal device you're using.**


•	**history** :- **displays the history of commands used.**


•	**cal**     :- **displays the calendar for the current month (or a specific year).**



##**System Shutdown and Reboot**


•	**shutdown -P now** :- **This command shuts down the system immediately and powers it off. The -P flag is for powering off the system.**


•	**shutdown -r now** :- **This command immediately reboots the system. The -r flag stands for "reboot."**


•	**shutdown -c**     :- **This command cancels any scheduled shutdowns. If there was a shutdown scheduled, this will stop it from happening.**

