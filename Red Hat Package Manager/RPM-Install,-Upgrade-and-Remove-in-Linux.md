
1. **Downloading RPM Packages**: 
   - You can use `wget` to download a package from a direct URL or `dnf download` to get it from a repository.

2. **Installing RPM Packages**:
   - The `rpm -i` command installs an RPM package. You can also use options like `-h` (progress bar) and `-v` (verbose mode) for more detailed output during installation.

3. **Upgrading Packages**:
   - The `rpm -U` command upgrades an existing package or installs it if it isn't already installed.

4. **Removing Packages**:
   - Use `rpm -e` to remove a package. You can add `--nodeps` to bypass dependency checks when uninstalling.

5. **Checking Installed Packages**:
   - You can check if a package is installed with `rpm -q`, and you can list all installed packages or use `grep` to search for specific ones.

6. **Viewing Package Information**:
   - `rpm -qi` shows detailed information about an installed package. You can also list all files installed by the package and check for dependencies.

7. **Verifying Package Integrity**:
   - `rpm -V` verifies whether the files of an installed package have been altered, indicating any file integrity issues.

8. **Extracting RPM Files**:
   - If you want to see the contents of an RPM file without installing it, you can use `rpm -qpl` to list the files or `rpm2cpio` to extract the files.

### **Quick Reference Table**:
This table provides a summary of the most common `rpm` commands for easy reference:

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

