 **YUM** (Yellowdog Updater, Modified) is accurate and provides a good overview of its core functionality.
---

## **📌 YUM (Yellowdog Updater, Modified)**

**YUM** is a powerful package manager used primarily in **RPM-based Linux distributions** such as **CentOS**, **RHEL (Red Hat Enterprise Linux)**, and **Fedora**. It simplifies software installation, updating, and removal by managing dependencies automatically. YUM uses repositories to fetch and install software packages, making it easier to maintain your system.

---

### **Key Features of YUM:**

1. **Dependency Resolution:**  
   YUM automatically resolves and installs any dependencies required by the packages you want to install. This ensures that all necessary libraries and tools are available for the software to function properly.

2. **Repository Management:**  
   YUM works with online or local repositories, which store software packages. By using repositories, YUM can easily download and install the latest package versions.

3. **Group Installations:**  
   YUM allows you to install a group of related packages in one go (e.g., a "development tools" group), saving time and ensuring consistency.

4. **Rollback Capability:**  
   YUM can revert to a previous package version if an update causes issues. This feature helps maintain system stability and ensures you can quickly recover from potential problems.

---

### **Basic YUM Commands:**

1. **Update All Packages**  
   Updates all installed packages to the latest available versions:
   ```bash
   sudo yum update -y
   ```

2. **Install a Package**  
   Installs a specific package:
   ```bash
   sudo yum install package-name -y
   ```

3. **Remove a Package**  
   Removes a specified package from the system:
   ```bash
   sudo yum remove package-name -y
   ```

4. **List Available Updates**  
   Lists all the packages that have updates available:
   ```bash
   sudo yum check-update
   ```

5. **Search for a Package**  
   Searches for a package in the enabled repositories:
   ```bash
   sudo yum search package-name
   ```

6. **Display Package Info**  
   Displays detailed information about a package:
   ```bash
   sudo yum info package-name
   ```

7. **Install a Package Group**  
   Install a group of related packages (e.g., Development Tools):
   ```bash
   sudo yum groupinstall "Development Tools" -y
   ```

8. **Remove a Package Group**  
   Remove a group of packages:
   ```bash
   sudo yum groupremove "Development Tools" -y
   ```

---

### **Advanced Features:**

1. **Listing Installed Packages:**
   To list all installed packages on your system, use:
   ```bash
   sudo yum list installed
   ```

2. **Cleaning the YUM Cache:**
   Over time, the YUM cache may take up a significant amount of space. To clean up the cache, use:
   ```bash
   sudo yum clean all
   ```

3. **Enable/Disable Repositories:**
   You can enable or disable specific repositories temporarily:
   ```bash
   sudo yum --disablerepo=repo-name install package-name
   sudo yum --enablerepo=repo-name install package-name
   ```

4. **Rollback a Package Update:**
   YUM allows you to roll back a package to a previous version. If an update caused problems, you can revert to the previous version with:
   ```bash
   sudo yum history undo <transaction-id>
   ```

   To view the transaction history:
   ```bash
   sudo yum history
   ```

---
