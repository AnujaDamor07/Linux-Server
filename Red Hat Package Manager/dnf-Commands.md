The **`dnf`** (Dandified YUM) command is the next-generation package manager for Fedora, RHEL, CentOS, and other related distributions. It provides improved performance, better dependency resolution, and enhanced features compared to the older **`yum`** command.

### **1. Install a Package**
To install a specific package, use the following command:
```bash
dnf install <package_name>
```
**Example:**
```bash
dnf install vim
```
This will install the **vim** package.

---

### **2. Remove a Package**
To remove an installed package, use:
```bash
dnf remove <package_name>
```
**Example:**
```bash
dnf remove vim
```
This will uninstall **vim** from your system.

---

### **3. Update a Package**
To update a specific package to its latest version:
```bash
dnf update <package_name>
```
**Example:**
```bash
dnf update vim
```
This will update **vim** to the latest available version.

---

### **4. Update All Packages**
To update all installed packages to their latest available versions:
```bash
dnf update
```

---

### **5. Search for a Package**
To search for a package by name or keyword:
```bash
dnf search <package_name>
```
**Example:**
```bash
dnf search vim
```
This will search for packages that match the name **vim**.

---

### **6. List Installed Packages**
To see a list of all installed packages on your system:
```bash
dnf list installed
```

---

### **7. List Available Packages**
To view a list of available packages in the repositories:
```bash
dnf list available
```

---

### **8. Display Information About a Package**
To see detailed information about a specific package:
```bash
dnf info <package_name>
```
**Example:**
```bash
dnf info vim
```
This will display detailed information about the **vim** package.

---

### **9. Check for Package Updates**
To check for available updates for all installed packages:
```bash
dnf check-update
```

---

### **10. Install a Group of Packages**
To install a group of related packages (e.g., a development or web server group):
```bash
dnf groupinstall "Group Name"
```
**Example:**
```bash
dnf groupinstall "Development Tools"
```
This installs the **Development Tools** group of packages.

---

### **11. Remove a Group of Packages**
To remove an entire group of packages:
```bash
dnf groupremove "Group Name"
```
**Example:**
```bash
dnf groupremove "Development Tools"
```
This will uninstall the entire **Development Tools** group.

---

### **12. Display Available Groups**
To see a list of available groups of packages:
```bash
dnf group list
```

---

### **13. Display Information About a Group**
To get detailed information about a specific package group:
```bash
dnf group info "Group Name"
```
**Example:**
```bash
dnf group info "Development Tools"
```
This will show detailed information about the **Development Tools** package group.

---

### **14. Clean the Package Cache**
To clear the package metadata and cached packages, freeing up space:
```bash
dnf clean all
```
This clears the cache for downloaded packages, metadata, and temporary data.

---

### **15. Enable a Repository**
To enable a specific repository:
```bash
dnf config-manager --set-enabled <repo_name>
```
**Example:**
```bash
dnf config-manager --set-enabled epel
```
This will enable the **EPEL** repository.

---

### **16. Disable a Repository**
To disable a repository:
```bash
dnf config-manager --set-disabled <repo_name>
```
**Example:**
```bash
dnf config-manager --set-disabled epel
```
This will disable the **EPEL** repository.

---

### **Summary of Key Commands**

- **Install a package:**
  ```bash
  dnf install <package_name>
  ```

- **Remove a package:**
  ```bash
  dnf remove <package_name>
  ```

- **Update a package:**
  ```bash
  dnf update <package_name>
  ```

- **Update all packages:**
  ```bash
  dnf update
  ```

- **Search for a package:**
  ```bash
  dnf search <package_name>
  ```

- **List installed packages:**
  ```bash
  dnf list installed
  ```

- **List available packages:**
  ```bash
  dnf list available
  ```

- **Display information about a package:**
  ```bash
  dnf info <package_name>
  ```

- **Check for package updates:**
  ```bash
  dnf check-update
  ```

- **Install a group of packages:**
  ```bash
  dnf groupinstall "Group Name"
  ```

- **Remove a group of packages:**
  ```bash
  dnf groupremove "Group Name"
  ```

- **Display available groups:**
  ```bash
  dnf group list
  ```

- **Display information about a group:**
  ```bash
  dnf group info "Group Name"
  ```

- **Clean the package cache:**
  ```bash
  dnf clean all
  ```

- **Enable a repository:**
  ```bash
  dnf config-manager --set-enabled <repo_name>
  ```

- **Disable a repository:**
  ```bash
  dnf config-manager --set-disabled <repo_name>
  ```

---

