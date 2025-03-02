RPM Package Management to install, upgrade, and remove software on Linux systems like **Red Hat**, **CentOS**, **Fedora**, **AlmaLinux**, and **RockyLinux** using the `rpm` command.

---

### **1. Download an RPM Package**

You can manually download RPM packages either using **`wget`** (direct URL) or **`dnf download`** (from a repository).

#### **Using `wget` (from a direct URL):**
1. Open a terminal.
2. Use `wget` to download an RPM package.

   Example:
   ```bash
   wget https://example.com/path/to/firefox.rpm
   ```

#### **Using `dnf` (from a repository):**
1. Open a terminal.
2. Download an RPM package without installing it using `dnf`.

   Example:
   ```bash
   sudo dnf download firefox
   sudo dnf download vlc
   ```

---

### **2. Install an RPM Package**

To install an RPM package, use the **`rpm -i`** command.

#### **Step-by-Step Installation:**

1. **Navigate** to the directory where the RPM file is located.
   
2. **Use the `rpm -i` command** to install the RPM package.

   Example:
   ```bash
   sudo rpm -i firefox-*.rpm
   sudo rpm -i vlc-*.rpm
   ```

   - If you want **verbose output** and a **progress bar**, use `-ivh`:

     ```bash
     sudo rpm -ivh firefox-*.rpm
     sudo rpm -ivh vlc-*.rpm
     ```

3. **To install ignoring dependency warnings**, use the `--nodeps` flag:
   
   ```bash
   sudo rpm -ivh --nodeps firefox-*.rpm
   ```

---

### **3. Upgrade an RPM Package**

Use **`rpm -U`** to upgrade a package. If the package isn't installed, it will be installed.

#### **Step-by-Step Upgrade:**

1. **Use the `rpm -U` command** to upgrade a package:

   Example:
   ```bash
   sudo rpm -U firefox-*.rpm
   sudo rpm -U vlc-*.rpm
   ```

2. **To force an upgrade and ignore warnings**, use the `--force` flag:

   ```bash
   sudo rpm -Uvh --force package.rpm
   ```

---

### **4. Remove (Uninstall) an RPM Package**

To **uninstall** a package, use **`rpm -e`**.

#### **Step-by-Step Uninstall:**

1. **Use the `rpm -e` command** to remove a package:

   Example:
   ```bash
   sudo rpm -e firefox
   sudo rpm -e vlc
   ```

2. **To uninstall ignoring dependencies**, use the `--nodeps` flag:

   ```bash
   sudo rpm -e --nodeps package-name
   ```

---

### **5. Check if a Package is Installed**

Use **`rpm -q`** to query if a package is installed.

#### **Step-by-Step Query:**

1. **Use `rpm -q` to check if a specific package is installed**:

   Example:
   ```bash
   rpm -q firefox
   rpm -q vlc
   ```

2. **To list all installed packages**:
   ```bash
   rpm -qa
   ```

3. **To search for installed packages using `grep`**:

   Example:
   ```bash
   rpm -qa | grep firefox
   rpm -qa | grep vlc
   ```

4. **To count the total number of installed packages**:
   ```bash
   rpm -qa | wc -l
   ```

---

### **6. View Package Information**

You can use **`rpm -qi`** to get detailed information about a package.

#### **Step-by-Step Information:**

1. **Use the `rpm -qi` command** to view detailed information about an installed package:

   Example:
   ```bash
   rpm -qi firefox
   rpm -qi vlc
   ```

   Example Output:
   ```
   Name        : firefox
   Version     : 102.6.0
   Release     : 1.el8
   Architecture: x86_64
   Size        : 460780
   License     : BSD
   Summary     : Mozilla Firefox Web browser
   ```

2. **To list all files installed by a package**, use `rpm -ql`:

   ```bash
   rpm -ql firefox
   ```

3. **To list configuration files**, use `rpm -qc`:

   ```bash
   rpm -qc firefox
   ```

4. **To list only documentation files**, use `rpm -qd`:

   ```bash
   rpm -qd firefox
   ```

5. **To list dependencies of a package**, use `rpm -qR`:

   ```bash
   rpm -qR firefox
   ```

---

### **7. Verify an Installed Package**

Use **`rpm -V`** to verify the integrity of an installed package.

#### **Step-by-Step Verification:**

1. **Use the `rpm -V` command** to check for file modifications:

   Example:
   ```bash
   rpm -V firefox
   ```

2. **Interpret the output** to understand which files have changed:
   ```
   S.5....T.  c /etc/firefox/firefox.conf
   ```

   - **`S`** → File size changed
   - **`5`** → MD5 checksum mismatch
   - **`T`** → File timestamp modified
   - **`c`** → Configuration file

---

### **8. Extract Files from an RPM Without Installing**

If you have an RPM file and don’t want to install it, you can extract its contents.

#### **Step-by-Step Extraction:**

1. **To list all files inside an RPM**, use `rpm -qpl`:

   ```bash
   rpm -qpl package.rpm
   ```

2. **To extract the files**, use `rpm2cpio` and **`cpio`**:

   ```bash
   rpm2cpio package.rpm | cpio -idmv
   ```

---

### **Summary of RPM Commands**

| Command | Description |
|---------|-------------|
| `rpm -qa` | List all installed packages |
| `rpm -qa | grep firefox` | Find installed packages containing "firefox" |
| `rpm -qi firefox` | Show detailed info of Firefox |
| `rpm -ql firefox` | List all installed files from Firefox |
| `rpm -qc firefox` | Show only configuration files of Firefox |
| `rpm -qd firefox` | Show only documentation files of Firefox |
| `rpm -qR firefox` | Show dependencies of Firefox |
| `rpm -V firefox` | Verify Firefox package integrity |
| `rpm -ivh package.rpm` | Install an RPM package |
| `rpm -Uvh package.rpm` | Upgrade an RPM package |
| `rpm -e firefox` | Remove Firefox package |

---

