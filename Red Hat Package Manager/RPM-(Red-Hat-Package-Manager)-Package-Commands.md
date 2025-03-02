RPM (Red Hat Package Manager) is a popular package management system used in Red Hat-based distributions like CentOS, Fedora, and RHEL. 

### 1. **Install an RPM Package**
To install an RPM package, use the `rpm` command with the `-i` (install) option:

```bash
sudo rpm -i package-name.rpm
```

- `-i` stands for **install**.
- Replace `package-name.rpm` with the name of the RPM file you want to install.

### 2. **Upgrade an RPM Package**
To upgrade an installed package to a newer version, use the `-U` (upgrade) option:

```bash
sudo rpm -U package-name.rpm
```

- `-U` stands for **upgrade**.
- If the package is already installed, it will be upgraded to the new version. If it's not installed, it will be installed.

### 3. **Uninstall (Remove) an RPM Package**
To uninstall or remove an RPM package, use the `-e` (erase) option:

```bash
sudo rpm -e package-name
```

- `-e` stands for **erase**.
- Replace `package-name` with the name of the package you want to uninstall (without the `.rpm` extension).

### 4. **Query a Package**
To query information about a package, use the `-q` (query) option. There are several variants:

- **Query a specific package:**
  ```bash
  rpm -q package-name
  ```
  This will display the version of the installed package.

- **Query all installed packages:**
  ```bash
  rpm -qa
  ```
  This will list all installed packages.

- **Query a specific package's detailed information:**
  ```bash
  rpm -qi package-name
  ```
  This shows detailed information about the package, including the version, vendor, description, and more.

- **Query files installed by a package:**
  ```bash
  rpm -ql package-name
  ```
  This will list all files installed by the package.

### 5. **Verify an Installed Package**
To verify the integrity of an installed package and check whether its files are correctly installed, use the `-V` (verify) option:

```bash
rpm -V package-name
```

This checks if the package's files are present and have the correct permissions.

### 6. **Check if a Package is Installed**
To check if a specific RPM package is installed:

```bash
rpm -q package-name
```

If the package is not installed, it will return a message like `package package-name is not installed`.

### 7. **List All RPM Packages in the System**
To list all installed packages on your system, use:

```bash
rpm -qa
```

This will display a list of all the installed RPM packages along with their versions.

### 8. **List Files Installed by a Package**
To see what files a particular RPM package installed:

```bash
rpm -ql package-name
```

This will list the files included with the package.

### 9. **Check Dependencies of an RPM Package**
To see the dependencies of a package, use the `-R` (requires) option:

```bash
rpm -qR package-name
```

This will list all the dependencies required by the package.

### 10. **Check What Package Provides a Specific File**
If you want to know which package provides a specific file, use the `-f` (file) option:

```bash
rpm -qf /path/to/file
```

This will return the name of the package that provides the file.

### 11. **Install RPM Package with Dependencies (Using `yum` or `dnf`)**
Although `rpm` is useful, it's often better to use `yum` or `dnf` to handle dependencies automatically. To install an RPM package using `yum` or `dnf`, you can use:

- **With `yum` (RHEL 7/CentOS 7):**
  ```bash
  sudo yum install package-name.rpm
  ```

- **With `dnf` (Fedora, RHEL 8/CentOS 8 and later):**
  ```bash
  sudo dnf install package-name.rpm
  ```

This will automatically resolve dependencies for the package.

### 12. **Create an RPM Package**
To create an RPM package from source files, you will need to prepare a **SPEC file**. Here is the basic command for building an RPM package:

```bash
rpmbuild -ba /path/to/specfile.spec
```


