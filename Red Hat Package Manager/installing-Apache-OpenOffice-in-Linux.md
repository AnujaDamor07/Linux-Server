
# **📌 How to Install Apache OpenOffice on Linux**

Apache **OpenOffice** is a free and open-source office suite that includes a word processor, spreadsheet, presentation software, and more. You can install it on **RHEL, CentOS, AlmaLinux, Rocky Linux, Fedora**, and **Ubuntu/Debian** distributions.

---

## **🔹 Step 1: Remove Existing LibreOffice (Optional)**

Most Linux distributions come with **LibreOffice** pre-installed. Since OpenOffice and LibreOffice serve similar functions, you may want to remove LibreOffice first.

### **Remove LibreOffice (Optional)**
For **Debian/Ubuntu**:
```bash
sudo apt remove --purge libreoffice* -y
```

For **RHEL/CentOS/Fedora**:
```bash
sudo dnf remove libreoffice* -y      # For newer Fedora versions
sudo yum remove libreoffice* -y      # For older Fedora/CentOS versions
```

---

## **🔹 Step 2: Download Apache OpenOffice**

Apache OpenOffice is not available in most package managers, so you need to **download it manually** from the official website.

### **Go to the Official Download Page:**
🔗 **[Apache OpenOffice Download Page](https://www.openoffice.org/download/)**

- Select **Linux 64-bit (rpm)** for RHEL-based distros (CentOS, Fedora, AlmaLinux, Rocky)
- Select **Linux 64-bit (deb)** for Debian-based distros (Ubuntu, Debian)

### **Download Using `wget`**

#### For **RHEL-based systems** (CentOS, Fedora, AlmaLinux, Rocky):
```bash
wget https://sourceforge.net/projects/openofficeorg.mirror/files/4.1.14/binaries/en-US/Apache_OpenOffice_4.1.14_Linux_x86-64_install-rpm_en-US.tar.gz
```

#### For **Debian-based systems** (Ubuntu, Debian):
```bash
wget https://sourceforge.net/projects/openofficeorg.mirror/files/4.1.14/binaries/en-US/Apache_OpenOffice_4.1.14_Linux_x86-64_install-deb_en-US.tar.gz
```

*Note*: Replace `4.1.14` with the latest version available.

---

## **🔹 Step 3: Extract the Downloaded File**

Once the file is downloaded, extract it using `tar`:

```bash
tar -xvzf Apache_OpenOffice_4.1.14_Linux_x86-64_install-*.tar.gz
```

---

## **🔹 Step 4: Install Apache OpenOffice**

### For **RHEL-based systems** (CentOS, Fedora, AlmaLinux, Rocky):
1. Navigate to the **RPMS** directory:
    ```bash
    cd en-US/RPMS
    ```

2. Install the RPM packages:
    ```bash
    sudo rpm -Uvh *.rpm
    ```

3. Install the desktop integration package:
    ```bash
    cd desktop-integration
    sudo rpm -Uvh openoffice4.1.14-redhat-menus-*.rpm
    ```

---

### For **Debian-based systems** (Ubuntu, Debian):
1. Navigate to the **DEBS** directory:
    ```bash
    cd en-US/DEBS
    ```

2. Install the `.deb` packages:
    ```bash
    sudo dpkg -i *.deb
    ```

3. Install the desktop integration package:
    ```bash
    cd desktop-integration
    sudo dpkg -i openoffice4.1.14-debian-menus-*.deb
    ```

---

## **🔹 Step 5: Verify Installation**

Once installed, you can verify OpenOffice is working:

### Start OpenOffice from the Terminal:
```bash
openoffice4
```

Alternatively, you can launch OpenOffice from the **Application Menu** on your system.

---

## **🔹 Step 6: Set OpenOffice as Default (Optional)**

If you want **OpenOffice** to be the default office suite for your system, you can set it as the default application for office documents:

```bash
sudo update-alternatives --set soffice /opt/openoffice4/program/soffice
```

---

## **🔹 Step 7: Uninstall Apache OpenOffice (If Needed)**

If you ever need to remove OpenOffice from your system, use the following commands:

### For **RHEL-based systems** (CentOS, Fedora, AlmaLinux, Rocky):
```bash
sudo rpm -e openoffice4
```

### For **Debian-based systems** (Ubuntu, Debian):
```bash
sudo dpkg -r openoffice4
```

---

## **📌 Summary of Commands**

| **Step**                                  | **Command** |
|-------------------------------------------|-------------|
| Remove LibreOffice (Optional)             | `sudo apt remove --purge libreoffice* -y` (Ubuntu/Debian) |
|                                           | `sudo dnf remove libreoffice* -y` (RHEL/CentOS/Fedora) |
| Download OpenOffice                       | `wget <OpenOffice URL>` |
| Extract Files                             | `tar -xvzf Apache_OpenOffice_*.tar.gz` |
| Install OpenOffice (RHEL)                 | `cd en-US/RPMS && sudo rpm -Uvh *.rpm` |
| Install OpenOffice (Debian)               | `cd en-US/DEBS && sudo dpkg -i *.deb` |
| Launch OpenOffice                         | `openoffice4` |
| Uninstall OpenOffice (RHEL)               | `sudo rpm -e openoffice4` |
| Uninstall OpenOffice (Debian)             | `sudo dpkg -r openoffice4` |

---

