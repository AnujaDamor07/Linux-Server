This list of **YUM commands** provides a detailed overview of the most common and advanced operations that can be performed using YUM in **RHEL/CentOS** and other **RPM-based** Linux distributions.
---

### **1. Check for Available Updates**  
Check for updates for installed packages:
```bash
yum check-update
```
**Output:**
```bash
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
bash.x86_64                          4.2.46-34.el7                       updates
kernel.x86_64                        3.10.0-1160.80.1.el7                updates
vim-enhanced.x86_64                  2:7.4.629-8.el7                     base
```
*(Lists available updates for installed packages.)*

---

### **2. Update All Packages**  
Update all installed packages to the latest versions:
```bash
yum update -y
```
**Output:**
```bash
Loaded plugins: fastestmirror
Resolving Dependencies
--> Running transaction check
---> Package bash.x86_64 0:4.2.46-33.el7 will be updated
---> Package bash.x86_64 0:4.2.46-34.el7 will be an update
...
Complete!
```
*(Updates all packages on the system.)*

---

### **3. Install a Package**  
Install a specific package:
```bash
yum install httpd -y
```
**Output:**
```bash
Loaded plugins: fastestmirror
Resolving Dependencies
--> Running transaction check
---> Package httpd.x86_64 0:2.4.6-97.el7.centos.5 will be installed
...
Complete!
```
*(Installs Apache HTTP server.)*

---

### **4. Remove a Package**  
Remove a package:
```bash
yum remove httpd -y
```
**Output:**
```bash
Loaded plugins: fastestmirror
Resolving Dependencies
--> Running transaction check
---> Package httpd.x86_64 0:2.4.6-97.el7.centos.5 will be erased
...
Complete!
```
*(Removes Apache HTTP server and related dependencies.)*

---

### **5. Search for a Package**  
Search for a package:
```bash
yum search nginx
```
**Output:**
```bash
Loaded plugins: fastestmirror
============================== Matched: nginx ==============================
nginx.x86_64 : A high performance web server and reverse proxy server
nginx-mod-http-image-filter.x86_64 : Image filter module for nginx
...
```
*(Searches for available packages related to nginx.)*

---

### **6. Show Package Information**  
Display information about a specific package:
```bash
yum info nginx
```
**Output:**
```bash
Loaded plugins: fastestmirror
Available Packages
Name        : nginx
Arch        : x86_64
Version     : 1.20.1
Release     : 1.el7
Size        : 2.0 M
Repo        : epel
Summary     : A high performance web server and reverse proxy server
URL         : http://nginx.org/
```
*(Displays details about the nginx package.)*

---

### **7. List All Installed Packages**  
List all installed packages:
```bash
yum list installed
```
**Output:**
```bash
Loaded plugins: fastestmirror
Installed Packages
bash.x86_64                     4.2.46-34.el7                @base
httpd.x86_64                    2.4.6-97.el7.centos.5        @updates
...
```
*(Lists all installed packages.)*

---

### **8. List All Available Packages**  
Show all packages available for installation:
```bash
yum list available
```
**Output:**
```bash
Loaded plugins: fastestmirror
Available Packages
nano.x86_64                2.9.8-1.el7          base
wget.x86_64                1.14-18.el7          base
htop.x86_64                2.2.0-3.el7          epel
```
*(Shows all packages available for installation.)*

---

### **9. List Installed Repositories**  
List active repositories:
```bash
yum repolist
```
**Output:**
```bash
Loaded plugins: fastestmirror
repo id                      repo name                                    status
base                         CentOS-7 - Base                              10,072
epel                         Extra Packages for Enterprise Linux 7        13,294
updates                      CentOS-7 - Updates                           1,342
```
*(Lists active repositories configured in the system.)*

---

### **10. Clean YUM Cache**  
Remove cached package metadata and downloaded files:
```bash
yum clean all
```
**Output:**
```bash
Loaded plugins: fastestmirror
Cleaning repos: base epel updates
Cleaning up everything
```
*(Removes cached package metadata and downloaded files to free space.)*

---

### **11. View YUM Transaction History**  
Display past YUM transactions:
```bash
yum history
```
**Output:**
```bash
ID     | Command         | Date and Time     | Action | Packages
------------------------------------------------------------
  10   | install nginx   | 2024-02-12 10:05  | Install | 1
   9   | update         | 2024-02-11 20:15  | Update  | 5
...
```
*(Displays past YUM transactions.)*

---

### **12. Downgrade a Package**  
Downgrade a package to an earlier version:
```bash
yum downgrade package-name
```
**Output:**
```bash
Resolving Dependencies
--> Running transaction check
---> Package package-name.x86_64 1.2.3-1.el7 will be downgraded
---> Package package-name.x86_64 1.2.2-1.el7 will be installed
...
Complete!
```
*(Downgrades a package to a previous version.)*

---

### **13. Install a Package Group**  
Install a group of related packages (e.g., Development Tools):
```bash
yum groupinstall "Development Tools"
```
**Output:**
```bash
Transaction Summary
Install  10 Packages
Upgrade   2 Packages
Complete!
```
*(Installs a group of related packages.)*

---

### **14. Remove a Package Group**  
Remove a package group:
```bash
yum groupremove "Development Tools"
```
**Output:**
```bash
Transaction Summary
Erase  10 Packages
Complete!
```
*(Removes a group of packages.)*

---

### **15. Enable a Repository Temporarily**  
Enable a repository temporarily:
```bash
yum --enablerepo=epel install htop
```
*(Installs `htop` from the `epel` repository without permanently enabling it.)*

---

### **16. Disable a Repository Temporarily**  
Disable a repository temporarily:
```bash
yum --disablerepo=epel update
```
*(Updates packages without using the `epel` repository.)*

---

### **17. List Disabled Repositories**  
List repositories that are disabled:
```bash
yum repolist disabled
```
*(Lists repositories that are disabled by default.)*

---

### **18. List All Available Package Groups**  
Show all available package groups:
```bash
yum group list
```
*(Shows all available package groups for installation.)*

---

### **19. Find the Download URL of a Package**  
Get the direct download URL for a package:
```bash
yumdownloader --url package-name
```
*(Displays the direct download URL for the package.)*

---

### **20. Download a Package Without Installing**  
Download a package without installing it:
```bash
yumdownloader package-name
```
*(Downloads the package to `/var/cache/yum/`.)*

---

### **21. Download a Package with Source Code**  
Download the source code for a package:
```bash
yumdownloader --source package-name
```
*(Downloads the `.src.rpm` file for the package.)*

---

### **22. View Installed Packages via YUM History**  
View installed packages using YUM history:
```bash
yum history list
```
*(Displays past YUM transactions.)*

---

### **23. Get Details of a Specific YUM Transaction**  
View detailed information about a specific transaction:
```bash
yum history info <ID>
```
*(Shows detailed information about transaction ID.)*

---

### **24. Rollback a YUM Transaction**  
Undo a transaction and revert changes:
```bash
yum history undo <ID>
```
*(Reverts transaction ID, uninstalling or removing the installed package.)*

---

### **25. List Dependencies of a Package**  
Display the dependencies required by a package:
```bash
yum deplist package-name
```
*(Shows a list of required dependencies for the package.)*

---

### **26. Check YUM Logs**  
View the YUM logs:
```bash
cat /var/log/yum.log
```
*(Displays all installation and update logs from YUM.)*

---

### **27. Install a Package and Lock Its Version**  
Install and prevent the package from being updated:
```bash
yum install package-name --setopt=protected_packages=1
```
*(Prevents the package from being removed or updated.)*

---

### **28. Prevent a Package from Being Updated**  
Lock the version of a package:
```bash
yum versionlock package-name
```
*(Locks the package to its current version, preventing future updates.)*

---

### **29. Show Older Versions of a Package**  
Show available older versions of a package:
```bash
yum list --showduplicates package-name
```
*(Displays all available versions of the package.)*

---

### **30. Install
