`cp` and `mv` commands 

---

### **Additional `cp` Tips and Use Cases** 🌟

1. **Copying and Overwriting (without Prompt) 🛑**  
   If you want to copy a file and **forcefully overwrite** an existing file at the destination, use the `-f` option (force). The `-i` option would instead prompt you.

   **Example:**  
   ```bash
   $ cp -f file.txt /home/user/Documents/
   ```

2. **Preserving File Attributes (`-p`) 🗂️**  
   When copying files, the `-p` flag ensures that timestamps, modes, and ownerships are preserved.

   **Example:**  
   ```bash
   $ cp -p myfile.txt /home/user/backup/
   ```

3. **Copying with Symbolic Links (`-L` and `-P`) 🔗**  
   - **`-L`**: Follows symbolic links and copies the file or directory it points to.
   - **`-P`**: Copies symbolic links as they are (without following them).

   **Example:**  
   ```bash
   $ cp -L link.txt /home/user/backup/
   ```

---

### **Additional `mv` Tips and Use Cases** 🔥

1. **Move and Rename Multiple Files 🗂️**  
   If you want to move multiple files and rename them in the process, you can specify a **destination directory** where the files will be moved. They will maintain their names.

   **Example:**  
   ```bash
   $ mv *.txt /home/user/Documents/
   ```

2. **Move Multiple Files with Pattern Matching 🔍**  
   Wildcards (e.g., `*`) can be used in the `mv` command to move multiple files at once that match a specific pattern.

   **Example:**  
   ```bash
   $ mv *.log /home/user/logs/
   ```

3. **Prevent Overwriting with `-n`**  
   The `-n` (no-clobber) option prevents overwriting any existing files in the destination directory. If a file with the same name already exists, it won’t be replaced.

   **Example:**  
   ```bash
   $ mv -n file.txt /home/user/Documents/
   ```

4. **Move a Directory (`-r` flag for directories)**  
   Just like copying directories recursively, `mv` can also move a directory and all of its contents recursively, with the `-r` flag. (This is generally the default for `mv` if you're moving directories.)

   **Example:**  
   ```bash
   $ mv -r /home/user/old_folder /home/user/new_folder/
   ```

---
