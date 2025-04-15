
# 💻 FTP Client Usage 

---

## 📦 **Types of FTP Clients**

| Type               | Description |
|--------------------|-------------|
| **Command-Line Clients** | Built into most Linux/Unix systems (e.g., `ftp`, `lftp`) |
| **GUI Clients**           | User-friendly apps like **FileZilla**, **WinSCP**, **Cyberduck** |

---

## 📌 **When to Use an FTP Client**

- Upload or download files from remote servers
- Backup configuration or logs
- Share large/public files without complex sharing tools
- Access anonymous/public software repositories

---

## 🔗 **Connecting to an FTP Server**

### 🔸 Basic Command:
```bash
ftp <server-ip>
```
> Example:
```bash
ftp 192.168.145.123
```

### 🔸 Login with:
| Username Options | Description |
|------------------|-------------|
| `ftp`            | Standard anonymous login |
| `anonymous`      | Standard anonymous login |
| `anon`           | Sometimes accepted |

**Use any email-style string as a password:**
```text
Username: ftp
Password: md@server.com
```

---

## 🧪 **FTP Login Examples**

### ✅ FTP with username `ftp`:
```
ftp 192.168.145.123
Name: ftp
Password: md@server.com
230 Login successful.
ftp> exit
```

### ✅ FTP with username `anonymous`:
```
ftp 192.168.145.123
Name: anonymous
Password: guest@example.com
230 Login successful.
ftp> ls
```

---

## ⚙️ **Common FTP Commands**

### 🔍 Help / List all commands
```ftp
? 
```

### 📁 Directory Operations
| Command | Description |
|---------|-------------|
| `pwd`   | Show current remote directory |
| `ls` or `ls -lh` | List files/directories |

---

## 📥 **Download Files**

| Task                  | Command |
|-----------------------|---------|
| Download one file     | `get tuned.log` |
| Download many files   | `mget *.conf` or `mget file1 file2` |

---

## 📤 **Upload Files**

### 🔸 Switch to binary mode (recommended for non-text files)
```ftp
binary
```

| Task                  | Command |
|-----------------------|---------|
| Upload one file       | `put file.txt` |
| Upload many files     | `mput *.log` or `mput file1 file2` |

---

## 🔄 **Switching Transfer Modes**

| Mode     | Use for...        | Command |
|----------|-------------------|---------|
| ASCII    | Plain text files  | `ascii` |
| Binary   | Binaries, images  | `binary` |

---

## ❌ **Delete Files (Remote)**

| Task                  | Command |
|-----------------------|---------|
| Delete one file       | `delete nc64.exe` |
| Delete many files     | `mdelete *.exe` or `mdelete file1 file2` |

---

## 🛠️ **Extra Tips**

- Always use **binary mode** for `.exe`, `.jpg`, `.zip`, etc.
- Use **wildcards** with `mget`, `mput`, or `mdelete` for batch ops
- Ensure your FTP server has proper **write permissions** on upload directories
- Close session cleanly using `bye`, `exit`, or `quit`

---

## 🚪 **Ending the FTP Session**

```ftp
bye
exit
quit
```

---

### ✅ Example Session Recap:

```bash
ftp 192.168.145.123
Name: ftp
Password: md@server.com
ftp> binary
ftp> mput *.log
ftp> ls
ftp> quit
```

---

