###**What is Linux?**
- Linux is an open-source operating system modelled on UNIX. It’s the foundation of many cloud infrastructures and has a significant presence in the server world, among other places.

:--- File System Hierarchical structure where all the data is organized.

The root directory **( / )** is essential for the structure of the entire Linux filesystem. It's where the system's core components and all other directories branch out from, and it serves as the base directory.
Under the root directory, various subdirectories are found, each serving a specific purpose. Here’s an overview of some common subdirectories in Linux, based on the Filesystem Hierarchy Standard (FHS):

1.	**/bin**   –  Contains essential binary files **(programs)** needed for system booting and repair. This directory includes basic command-line utilities like ls, cp, mv, cat, etc.
2.	
3.	**/boot**  –  Contains files necessary for the boot process, such as the Linux kernel and initial RAM disk images. Files here are critical for the system to start up properly.
4.	
5.	**/dev**   –  Contains device files that represent hardware devices on the system, like hard drives, terminals, and other devices. These files are used for interacting with hardware components.
6.	
7.	**/etc**   –  Stores configuration files for the system and installed applications. Files here control system-wide settings (like network configurations, user settings, etc.). Examples include /etc/passwd and /etc/network/interfaces.
8.
9.	**/home**  –  Holds the personal directories for each user on the system. Each user has their own directory within **/home,** like **/home/john** for user **"john".**
10.	
11.	**/lib**   –  Contains shared libraries essential for running binaries in **/bin** and **/sbin.** It houses common code libraries needed by various system programs.
12.	
13.	**/media** –  A mount point for removable media like USB drives, CD/DVDs, etc. This is where external storage devices are mounted when inserted into the system.
14.	
15.	**/mnt**   –  Traditionally used as a temporary mount point for filesystems during maintenance or system administration tasks, though /media is now commonly used for external devices.
16.	
17.	**/opt**   –  Used for optional application software packages, typically third-party software that is not part of the default distribution.
18.	
19.	**/proc**  –  A virtual filesystem that provides system and process information in real-time. Files in **/proc** are not actual files on disk but reflect the current state of the system, such as /proc/cpuinfo for CPU information or /proc/meminfo for memory details.
20.
21.	**/root**  –  The home directory for the root user (administrator). This is distinct from **/home** and is where the system administrator's files are stored.
22.	
23.	**/run**   –  A temporary filesystem that contains runtime data, such as process IDs (PIDs) or system information, that the system needs during its runtime.
24.	
25.	**/sbin**  –  Contains system binary files, similar to **/bin,** but these are used for administrative tasks like system maintenance. For example, commands like ifconfig and reboot.
26.	
27.	**/srv**   –  Stores data for services provided by the system, such as websites or FTP servers. This directory may include directories for web servers **(/srv/www),** FTP servers, or databases.
28.	
29.	**/sys**   –  Another virtual filesystem, like /proc, that provides information and allows interaction with the system's kernel. It’s commonly used to gather data about devices or settings related to the kernel.
30.	
31.	**/tmp**   –  A directory for temporary files. Files in **/tmp** are typically deleted when the system reboots. Programs use this directory to store temporary files that are needed for a short duration.
32.	
33.	**/usr**   –  Contains the majority of user-related programs and data. It's one of the largest directories and is where user applications, libraries, and documentation reside. The **/usr/bin** directory holds most user command binaries, while **/usr/lib** holds libraries.
34.
35.	**/var**   –  Stores variable data such as logs, mail, and spool files. Files in this directory change frequently during the normal operation of the system. **/var/log** is a typical location for system logs.
Permissions and Ownership

In Linux, file and directory ownership are very important for security. The root directory **( / )** and its subdirectories are usually owned by the root user, and permissions are set to ensure only the administrator has the ability to modify these files. Regular users are granted access to their own home directories in /home and can only modify files they own, not system directories.



###**SUB-DIRECTORY IN A SHORT**


**/bin**       :-    **common binary executables used by all users**


**/boot**      :-    **files associated with boot loader**


**/dev**       :-    **attached devices (usb, cdrom, mouse, keyboard)**


**/etc**       :-    **configuration files**


**/home**      :-    **personal directories for each user account**


**/lib**       :-    **shared system libraries**


**/media**     :-    **directory for mounting removable devices (floppy drive, cdrom)**


**/mnt**       :-    **directory for mounting filesystems (nfs, smb)**


**/opt**       :-    **optional vendor add-on software**


**/proc**      :-    **virtual filesystem for system processes/resources information**


**/root**      :-    **home directory for administrator account**


**/run**       :-    **storage for runtime information**


**/sbin**      :-    **binary executables used by administrator**


**/srv**       :-    **data for server services**


**/sys**       :-    **virtual filesystem for hardware/driver information**


**/tmp**       :-    **temporary files purged on reboot**


**/usr**       :-    **utilities and read-only user data/programs**


**/var**       :-    **variable and log files**
