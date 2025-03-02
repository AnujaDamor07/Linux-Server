Linux filesystem and its various directories.

### **Root Directory Overview**
The root directory **( / )** is the topmost directory in Linux and serves as the base of the entire file system. All other directories branch off from here.

### **Common Subdirectories:**

1. **/bin** - Essential binary files and commands used by all users (e.g., `ls`, `cp`, `mv`).
2. **/boot** - Files needed for booting the system (e.g., kernel and RAM disk images).
3. **/dev** - Device files representing hardware (e.g., hard drives, USB devices).
4. **/etc** - System configuration files (e.g., `passwd`, `network` settings).
5. **/home** - Personal directories for users (e.g., `/home/john`).
6. **/lib** - Shared libraries used by binaries in `/bin` and `/sbin`.
7. **/media** - Mount points for removable media (e.g., USB drives, CD/DVDs).
8. **/mnt** - Temporary mount points for filesystems (e.g., NFS or SMB shares).
9. **/opt** - Optional software packages, typically third-party applications.
10. **/proc** - Virtual filesystem providing process and system info (e.g., `/proc/cpuinfo`).
11. **/root** - Home directory for the root (administrator) user.
12. **/run** - Storage for runtime system data (e.g., process IDs and system info).
13. **/sbin** - Binary files used for administrative tasks (e.g., `reboot`, `ifconfig`).
14. **/srv** - Data for services provided by the system (e.g., web server data).
15. **/sys** - Virtual filesystem for kernel and device info.
16. **/tmp** - Directory for temporary files, which are deleted upon reboot.
17. **/usr** - User-related programs and data (e.g., applications and libraries).
18. **/var** - Variable data like logs, mail, and spool files (e.g., `/var/log`).

### **Permissions and Ownership:**
- Root user typically owns the root directory and its subdirectories.
- Regular users are restricted to modifying their own files within their home directories in `/home`.
- Proper ownership and permissions ensure security in the system, as administrative tasks are restricted to the root user.

